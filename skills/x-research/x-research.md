# x-research

| Field | Value |
|---|---|
| Skill ID | x-research |
| Group | MARKETING |
| Source | HoC Suite |
| BenOS Fit | 4/5 |
| Ventures | WIC, Bennovative, SIPP |
| API Status | Green |
| Voice Injection | Light |
| Version | 1.0 |
| Last Updated | 2026-05-12 |

## Purpose

Research high-performing X/Twitter content from tracked accounts using Apify's Tweet Scraper V2. Identifies outlier tweets, trending topics, and content patterns to inform venture-specific content strategy.

## Triggers

- "X research"
- "Twitter research"
- "content research"
- "what performs on X"
- "analyze X content"
- "find trending tweets"
- "what's working on twitter"
- "analyze X accounts"
- "tweet analysis"

## Inputs

- Venture name (WIC, Bennovative, or SIPP) — determines which account set and query themes to use
- Optional: `--days` (lookback window, default 30)
- Optional: `--max-items` (tweets per account, default 100)
- Optional: `--handles` (override configured accounts with specific handles)
- Optional: `--threshold` (outlier detection multiplier, default 2.0)

## Outputs

- `x-research/{YYYY-MM-DD_HHMMSS}/raw.json` — raw tweet data from Apify
- `x-research/{YYYY-MM-DD_HHMMSS}/outliers.json` — scored outliers with topics and content patterns
- `x-research/{YYYY-MM-DD_HHMMSS}/video-analysis.json` — AI video hook analysis (optional)
- `x-research/{YYYY-MM-DD_HHMMSS}/report.md` — final research report with actionable takeaways

## BenOS Integrations

- **Primary data source:** Apify MCP (paid and connected — Tweet Scraper V2)
- **Pairs with:** social-content, content-repurposing
- **Feeds into:** content-creator for brand voice analysis using outlier patterns
- **Run before:** social-content or content-repurposing when you need real data, not assumptions

## Customization Notes

- MEDIUM CUSTOMIZE applied: all tool references mapped to BenOS stack (Apify as primary, already paid/connected)
- Venture-specific search queries and tracked accounts defined per venture below
- Engagement scoring preserved from source (bookmarks 4×, replies 3×)
- `.claude/context/x-accounts.md` is the accounts config file — see Configure Accounts section in Full Instructions

---

# Full Instructions

## BenOS Workflow

**Where this skill sits:** Upstream of social-content and content-repurposing. Run this first when you need real data about what performs in a venture's niche before writing content.

**Before running:** Execute `product-marketing-context` to confirm which venture you are researching and what the current content goals are.

**After running:** Feed the outlier analysis directly into the `social-content` skill for post drafting, or into `content-repurposing` to adapt top-performing formats for other channels.

---

## Venture-Specific Research Configuration

> **For WIC:** Search queries: "specialty coffee", "single origin coffee", "coffee ritual", "DTC coffee", "coffee subscription". Accounts to track: top DTC coffee brands, specialty coffee roasters, barista educators. Goal: identify sensory/story angles that drive engagement.

> **For Bennovative:** Search queries: "stoicism", "building in public", "founders", "doing hard things", "entrepreneurship", "discipline". Accounts to track: Ryan Holiday, Jocko Willink, Alex Hormozi, David Goggins adjacent. Goal: identify format patterns (threads vs single tweets) and hook structures.

> **For SIPP:** Search queries: "water quality", "smart home", "home water filter", "PFAS water", "lead in water", "IoT home". Accounts to track: water quality advocates, smart home reviewers, home improvement creators. Goal: surface fear/concern language for ad copy and content hooks.

---

## Prerequisites

- `APIFY_TOKEN` in `.env` or environment (Apify is paid and connected in BenOS)
- `GEMINI_API_KEY` in `.env` (only needed for optional video analysis step)
- `apify-client` and `google-genai` Python packages
- Accounts configured in `.claude/context/x-accounts.md` per venture

Verify Apify connection:
```bash
python3 -c "
import os
try:
    from dotenv import load_dotenv
    load_dotenv()
except ImportError:
    pass
from apify_client import ApifyClient
assert os.environ.get('APIFY_TOKEN'), 'APIFY_TOKEN not set'
" && echo "Apify OK"
```

---

## Configure Accounts

Create or update `.claude/context/x-accounts.md` with the following structure. Populate handle lists based on the venture being researched.

```markdown
# X Tracked Accounts

## WIC
handles:
  - @bluebottlecoffee
  - @stumptown
  - @onyx_coffee
  - @[other specialty DTC coffee roasters and barista educators]

search_queries:
  - "specialty coffee"
  - "single origin coffee"
  - "coffee ritual"
  - "DTC coffee"
  - "coffee subscription"

## Bennovative
handles:
  - @RyanHoliday
  - @jockowillink
  - @AlexHormozi
  - @davidgoggins
  - @[other stoic/founder/discipline-adjacent accounts]

search_queries:
  - "stoicism"
  - "building in public"
  - "founders"
  - "doing hard things"
  - "entrepreneurship"
  - "discipline"

## SIPP
handles:
  - @[water quality advocates]
  - @[smart home reviewers]
  - @[home improvement creators]
  - @[PFAS/lead water safety voices]

search_queries:
  - "water quality"
  - "smart home"
  - "home water filter"
  - "PFAS water"
  - "lead in water"
  - "IoT home"
```

---

## Workflow

### 1. Create Run Folder

```bash
RUN_FOLDER="x-research/$(date +%Y-%m-%d_%H%M%S)" && mkdir -p "$RUN_FOLDER" && echo "$RUN_FOLDER"
```

### 2. Fetch Tweets via Apify

Apify is the primary data source in BenOS — it is paid and connected. Use Tweet Scraper V2 via the Apify MCP or the Python client.

```bash
python3 .claude/skills/x-research/scripts/fetch_tweets.py \
  --days 30 \
  --max-items 100 \
  --output {RUN_FOLDER}/raw.json
```

Parameters:
- `--days`: Days back to search (default: 30)
- `--max-items`: Max tweets per account (default: 100)
- `--handles`: Override accounts file with specific handles

**API Limits:** Minimum 50 tweets per query required. Wait a couple minutes between runs.

**Venture examples:**
- WIC run: `--handles bluebottlecoffee stumptown onyx_coffee` or pull from `x-accounts.md` WIC section
- Bennovative run: `--handles RyanHoliday jockowillink AlexHormozi` or pull from `x-accounts.md` Bennovative section
- SIPP run: use handles from `x-accounts.md` SIPP section focused on water quality and smart home creators

### 3. Identify Outliers

```bash
python3 .claude/skills/x-research/scripts/analyze_posts.py \
  --input {RUN_FOLDER}/raw.json \
  --output {RUN_FOLDER}/outliers.json \
  --threshold 2.0
```

Output JSON contains:
- `total_posts`: Number of tweets analyzed
- `outlier_count`: Number of outliers found
- `topics`: Top hashtags, mentions, and keywords
- `content_patterns`: Analysis of what formats perform well
- `accounts`: List of accounts analyzed
- `outliers`: Array of outlier tweets with engagement metrics

### 4. Analyze Videos with AI (Optional)

If outliers contain video content (more common in SIPP smart home and WIC barista content):

```bash
python3 .claude/skills/video-content-analyzer/scripts/analyze_videos.py \
  --input {RUN_FOLDER}/outliers.json \
  --output {RUN_FOLDER}/video-analysis.json \
  --platform x \
  --max-videos 5
```

Note: X/Twitter is primarily text-based. For Bennovative research (stoicism/founders niche), video analysis is rarely needed — focus on thread structure and hook patterns instead. For WIC and SIPP, video analysis can surface sensory hooks and fear-trigger language respectively.

### 5. Generate Report

Read `{RUN_FOLDER}/outliers.json` (and optionally `{RUN_FOLDER}/video-analysis.json`), then generate `{RUN_FOLDER}/report.md`.

**Report Structure:**

```markdown
# X/Twitter Research Report — {Venture}

Generated: {date}

## Summary

- **Venture**: {WIC | Bennovative | SIPP}
- **Total tweets analyzed**: {total_posts}
- **Outlier tweets identified**: {outlier_count}
- **Outlier rate**: {percentage}%

## Top Performing Tweets (Outliers)

### 1. @{username} ({name})

> {tweet_text}

- **URL**: {url}
- **Date**: {created_at}
- **Engagement**: {likes} likes | {retweets} RTs | {replies} replies | {bookmarks} bookmarks
- **Engagement Score**: {score}
- **Engagement Rate**: {rate}%
- **Followers**: {followers}

[Repeat for top 15 outliers]

## Top Performing Hooks (if video analysis available)

### Hook 1: {technique} - @{username}
- **Opening**: "{opening_line}"
- **Why it works**: {attention_grab}
- **Replicable Formula**: {replicable_formula}
- [Watch Video]({url})

## Trending Topics

### Top Hashtags
[From outliers.json topics.hashtags]

### Top Keywords
[From outliers.json topics.keywords]
<!-- For WIC: look for sensory/ritual language -->
<!-- For Bennovative: look for identity/challenge framing -->
<!-- For SIPP: look for fear/urgency language around water safety -->

### Top Mentions
[From outliers.json topics.mentions]

## Content Patterns in Outliers

| Pattern | Count | Percentage |
|---------|-------|------------|
| Contains media | {count} | {pct}% |
| Contains external link | {count} | {pct}% |
| Thread format | {count} | {pct}% |
| Quote tweet | {count} | {pct}% |
| Asks a question | {count} | {pct}% |
| List/numbered format | {count} | {pct}% |
| Short (<100 chars) | {count} | {pct}% |
| Medium (100-200 chars) | {count} | {pct}% |
| Long (>200 chars) | {count} | {pct}% |

## Actionable Takeaways

[Synthesize patterns into 4-6 specific recommendations tailored to the venture's content goals]

<!-- WIC: focus on sensory angles and story-driven formats -->
<!-- Bennovative: focus on thread vs single tweet breakdown, hook structure patterns -->
<!-- SIPP: focus on fear/concern language and question hooks for ad copy -->

## Accounts Analyzed

[List accounts]
```

---

## Quick Reference

Full pipeline:
```bash
RUN_FOLDER="x-research/$(date +%Y-%m-%d_%H%M%S)" && mkdir -p "$RUN_FOLDER" && \
python3 .claude/skills/x-research/scripts/fetch_tweets.py -o "$RUN_FOLDER/raw.json" && \
python3 .claude/skills/x-research/scripts/analyze_posts.py -i "$RUN_FOLDER/raw.json" -o "$RUN_FOLDER/outliers.json"
```

With video analysis (optional, useful for WIC/SIPP):
```bash
python3 .claude/skills/video-content-analyzer/scripts/analyze_videos.py -i "$RUN_FOLDER/outliers.json" -o "$RUN_FOLDER/video-analysis.json" -p x
```

Then read JSON files and generate the report.

---

## Engagement Metrics

**Engagement Score (weighted):**
- Bookmarks: 4x (highest signal — saved for reference, strong intent)
- Replies: 3x (active conversation, community pull)
- Retweets: 2x (amplification)
- Quotes: 2x (engagement with commentary)
- Likes: 1x (passive approval)

**Outlier Detection:** Tweets with engagement rate > mean + (threshold × std_dev)

**Engagement Rate:** (score / followers) × 100

---

## Output Location

All output goes to timestamped run folders:
```
x-research/
└── {YYYY-MM-DD_HHMMSS}/
    ├── raw.json            # Raw tweet data from Apify
    ├── outliers.json       # Outliers with metadata and topics
    ├── video-analysis.json # AI video analysis (optional)
    └── report.md           # Final report
```
