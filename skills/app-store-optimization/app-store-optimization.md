# App Store Optimization (ASO) Skill

| Field | Value |
|---|---|
| **Skill Name** | app-store-optimization |
| **Source** | Antigravity |
| **BenOS Fit** | 4/5 |
| **Ventures** | SIPP |
| **API Status** | Green |
| **Voice Injection** | Light |
| **Group** | MARKETING |
| **Version** | 1.0 |
| **Last Updated** | 2026-05-12 |

---

## Purpose

Complete App Store Optimization (ASO) toolkit for researching, optimizing, and tracking mobile app performance on Apple App Store and Google Play Store. Covers keyword research, metadata optimization, visual asset strategy, review management, A/B testing, and launch readiness — with SIPP-specific guidance baked in.

---

## Triggers

Use this skill when you hear or type:
- "ASO"
- "app store"
- "app listing"
- "Play Store"
- "app keywords"
- "mobile app launch"

---

## Inputs

### Keyword Research
```json
{
  "app_name": "SIPP: Home Water Quality Monitor",
  "category": "Utilities",
  "target_keywords": ["smart home water quality", "water quality test", "lead detection home"],
  "competitors": ["Hach Water Quality", "YSI EXO", "Tap Score"],
  "language": "en-US"
}
```

### Metadata Optimization
```json
{
  "platform": "apple",
  "app_info": {
    "name": "SIPP: Home Water Quality Monitor",
    "category": "Utilities",
    "target_audience": "Homeowners, parents, renters aged 28-55",
    "key_features": ["Real-time water quality readings", "IoT sensor integration", "Historical data tracking", "Instant alerts"],
    "unique_value": "See exactly what's in your tap water — in seconds"
  },
  "current_metadata": {
    "title": "Current Title",
    "subtitle": "Current Subtitle",
    "description": "Current description..."
  },
  "target_keywords": ["water quality", "home water monitor", "lead detection home"]
}
```

### Review Analysis
```json
{
  "app_id": "com.sipp.waterquality",
  "platform": "apple",
  "date_range": "last_30_days",
  "rating_filter": [1, 2, 3, 4, 5],
  "language": "en"
}
```

### ASO Score Calculation
```json
{
  "metadata": {
    "title_quality": 0.8,
    "description_quality": 0.7,
    "keyword_density": 0.6
  },
  "ratings": {
    "average_rating": 4.5,
    "total_ratings": 15000
  },
  "conversion": {
    "impression_to_install": 0.05
  },
  "keyword_rankings": {
    "top_10": 5,
    "top_50": 12,
    "top_100": 18
  }
}
```

---

## Outputs

- **Keyword Research Report** — recommended keywords with volume estimates, competition level, relevance scores, long-tail opportunities
- **Optimized Metadata Package** — platform-specific title/subtitle/description with character count validation, keyword density analysis, before/after comparison
- **Competitor Analysis Report** — top competitors, keyword overlap, visual asset assessment, identified gaps
- **ASO Health Score** — overall 0–100 score across Metadata Quality, Ratings & Reviews, Keyword Performance, Conversion Metrics
- **A/B Test Plan** — hypothesis, test duration, success metrics, sample size, significance thresholds
- **Launch Checklist** — pre-submission validation, store compliance, testing matrix, post-launch monitoring plan

---

## BenOS Integrations

- **GitHub MCP** — pull Flutter app repo metadata (app name, bundle ID, version) directly into ASO workflow; sync "What's New" copy with release notes
- **Pairs with `product-manager-toolkit`** — use for defining target audience, feature prioritization, and positioning before writing metadata
- **Pairs with `landing-page-generator`** — coordinate app store keyword clusters with web landing page SEO terms for cross-channel discovery consistency; ideal for pre-launch stack before hardware ships

---

## Customization Notes

- SIPP keyword clusters and submission checklist are pre-loaded below
- Flutter (iOS + Android) dual-platform guidance baked in
- Screenshot strategy prioritizes water quality dashboard as hero frame
- Generic tool/script references in the source skill map to BenOS stack (GitHub MCP for repo data, Claude for copy generation, Analytics for conversion tracking)

---

## Instructions

### Overview

This skill provides complete ASO capabilities for launching and optimizing mobile applications on the Apple App Store and Google Play Store. It covers research, metadata writing, visual asset strategy, ratings management, A/B testing, launch readiness, and ongoing optimization.

---

### Keyword Research

**Process:**
1. Start with the app's core value proposition — what problem does it solve in 3–5 words?
2. Expand into keyword clusters: branded terms, category terms, problem terms, solution terms
3. Score each keyword on volume, competition, and relevance
4. Prioritize: high relevance + low competition > high volume alone
5. Validate against what top competitors rank for, then find gaps

**Best Practices:**
- Balance high-volume keywords with achievable rankings
- Only target keywords genuinely relevant to your app
- Include 3–4 word long-tail phrases with lower competition
- Research quarterly — keyword trends shift
- Don't copy competitors blindly; ensure relevance to your features

**Example:**
> *App: Home water quality monitor. Core value: "know what's in your tap water."*
> *Keyword clusters: Problem ("tap water safety", "is my water safe"), Solution ("water quality test", "water quality meter"), Device ("IoT water sensor", "smart home water monitor"), Outcome ("lead detection home", "water quality alert").*
> *Apple keyword field (100 chars, no spaces): `waterquality,tapwater,leadsafety,homemonitor,watertest,IoTsensor,drinkingwater,wateralert`*

> **For SIPP App Submission:**
> Primary keyword clusters: "smart home water quality", "home water monitor", "water quality test", "lead detection home", "water safety app", "IoT water sensor", "water quality meter", "tap water safety". App store category: Utilities or Health & Fitness. App is Flutter (iOS + Android). Pre-launch: optimize for discovery before hardware ships. Screenshot strategy: show the water quality dashboard first, then the installation flow.

**SIPP App Submission Checklist:**
- [ ] App title includes primary keyword (e.g., "SIPP: Home Water Quality Monitor")
- [ ] Subtitle (iOS) / Short Description (Android) contains secondary keywords
- [ ] First 3 lines of description visible without "more" tap — lead with the problem/solution
- [ ] Screenshots show: (1) dashboard reading, (2) setup flow, (3) historical data, (4) alerts
- [ ] Preview video: 15–30 seconds showing first reading moment (the aha moment)
- [ ] Keywords field (iOS): no spaces, no repeated words from title
- [ ] Rating prompt configured for post-first-reading trigger

---

### Metadata Optimization

**Platform-Specific Character Limits:**

| Field | Apple App Store | Google Play Store |
|---|---|---|
| Title | 30 chars | 50 chars |
| Subtitle / Short Description | 30 chars | 80 chars |
| Promotional Text | 170 chars (editable without update) | — |
| Full Description | 4,000 chars | 4,000 chars |
| Keyword Field | 100 chars (comma-separated, no spaces) | No separate field |
| What's New | 4,000 chars | — |

**Process:**
1. Write title: primary keyword + brand name or differentiator, within character limit
2. Write subtitle (iOS): secondary keyword cluster, benefit-oriented
3. Write short description (Android): hook sentence with top 2 keywords
4. Write full description: lead with problem/solution in first 3 visible lines, then features, then social proof
5. Fill Apple keyword field: no plurals, no spaces, no duplicates from title
6. Validate all character counts before submitting

**Best Practices:**
- Front-load the most important keyword in the title
- Write for humans first, SEO second
- Focus on user benefits, not just features
- Use every character — don't waste valuable space
- Update metadata at every major release
- Apple Promotional Text can change without app resubmission — use it for seasonal campaigns

**Example:**
> *Title (Apple, 30 chars): `SIPP: Home Water Monitor` (24 chars)*
> *Subtitle (Apple, 30 chars): `Test lead, pH & contaminants` (28 chars)*
> *Short Description (Android, 80 chars): `Know what's in your tap water. Real-time readings from your SIPP sensor.` (72 chars)*
> *First visible lines of description: "Your tap water could contain lead, chlorine, or other contaminants you can't see or taste. SIPP gives you a real-time reading in seconds — right from your phone."*

---

### Visual Assets

**Screenshot Strategy:**
1. First 2–3 screenshots are critical — most users never scroll past them
2. Use captions to tell the value story frame by frame
3. Show the "aha moment" as early as possible
4. Match the visual style to the in-app design

**Icon Best Practices:**
- Must be recognizable at 60×60px (small size on device)
- A/B test the icon — it is the single highest-impact visual element
- Avoid text in the icon; rely on shape and color

**Preview Video:**
- 15–30 seconds maximum
- Open with the core value moment, not a loading screen
- Captions for sound-off viewing
- End with a clear benefit statement

**Example (SIPP):**
> *Screenshot 1: Dashboard showing a live water quality reading with a green "Safe" indicator — headline caption: "Know your water in seconds."*
> *Screenshot 2: Sensor setup flow (3 steps) — caption: "Installs in under 5 minutes."*
> *Screenshot 3: 30-day historical trend chart — caption: "Track quality over time."*
> *Screenshot 4: Alert notification on lock screen — caption: "Get notified if anything changes."*
> *Preview video: Opens on the moment the first reading appears on screen. No intro screen. Caption: "This is your water."*

---

### Conversion Optimization

**A/B Testing Framework:**
1. Define one variable per test (icon, first screenshot, title)
2. Run tests for minimum 2 weeks or until statistical significance (95% confidence)
3. Calculate required sample size before starting
4. Track impression-to-install conversion rate as the primary metric
5. Document all test results for future reference

**Store Listing Optimization:**
- Use Apple's Product Page Optimization (up to 3 treatments simultaneously)
- Use Google Play's Store Listing Experiments for A/B tests
- Test during stable periods — avoid running tests during major holidays or events

**Example:**
> *Hypothesis: Showing the dashboard screenshot first (vs. the installation flow first) will increase conversion rate.*
> *Test duration: 3 weeks. Primary metric: impression-to-install rate. Secondary: page view duration.*
> *Success threshold: 95% statistical significance, minimum 5% relative lift.*

---

### Rating & Review Management

**Review Monitoring:**
- Track reviews daily for first 2 weeks post-launch
- Filter by 1-star and 2-star reviews weekly — these contain the most actionable signal
- Extract common complaint themes and route to the engineering backlog

**Response Strategy:**
- Reply to reviews within 24–48 hours
- Always professional, never defensive
- For negative reviews: acknowledge, apologize if warranted, describe fix timeline
- For positive reviews: thank the user, reinforce a key benefit, invite further feedback

**Rating Improvement:**
- Trigger the in-app rating prompt after a positive experience (first successful reading, not on launch)
- Never ask immediately after an error or frustrating flow
- Use SKStoreReviewAPI (iOS) or In-App Review API (Android) — do not redirect to the store manually

**Example (SIPP):**
> *Rating prompt trigger: After the user receives their first water quality reading and sees a "Safe" or "Review recommended" result.*
> *Prompt timing: 5 seconds after the result screen loads, if the session is > 60 seconds.*
> *Response template for 1-star "sensor won't connect": "We're sorry you hit this — Bluetooth pairing issues are our top priority fix. Please email support@sipp.com with your device model and we'll get you set up. Update v1.2 (releasing this week) addresses this directly."*

---

### Launch & Update Strategy

**Pre-Launch Checklist:**
- All required screenshots at correct resolutions (Apple: 6.9", 6.5", 12.9" iPad; Google: phone + 7" tablet)
- App icon at all required sizes and formats
- Privacy policy URL live and accessible
- App description finalized and character-validated
- Age rating questionnaire completed accurately
- In-app purchase items created and approved (if applicable)
- TestFlight / internal test track validated on target devices
- Crash-free rate > 99% before submission

**Launch Timing:**
- Avoid major holidays for initial launch (algorithm resets are harder to read)
- Tuesday–Thursday releases tend to get earlier editorial review
- Coordinate press coverage to land same day as store availability

**Update Cadence:**
- First 30 days: ship fixes quickly; active development signals quality to the algorithm
- "What's New" text: lead with the most user-visible change; don't pad with internal notes
- Major feature releases: treat like a mini-launch (update screenshots, metadata, PR outreach)

**Example:**
> *SIPP v1.0 launch plan: Submit to Apple and Google on Monday for Tuesday review. Press embargo lifts Thursday. "What's New": "First release — connect your SIPP sensor and see your water quality in real time." Post-launch: monitor crash rate and reviews hourly for 48 hours. Ship v1.0.1 patch by day 7 if critical issues surface.*

---

### Analytics & Tracking

**Key Metrics:**
- **Impression-to-product-page rate** — are search results driving clicks?
- **Product-page-to-install rate** — is the listing converting?
- **Keyword ranking positions** — track weekly for top 20 target keywords
- **Download velocity** — total installs per day/week/month
- **Ratings trend** — average rating over rolling 30 days
- **Uninstall rate** — available in Google Play; proxy for onboarding quality

**ASO Health Score (0–100):**
- Metadata Quality (0–25): title keyword inclusion, description front-load, character utilization
- Ratings & Reviews (0–25): average rating, total rating volume, response rate
- Keyword Performance (0–25): # of target keywords ranking top 10, top 50, top 100
- Conversion Metrics (0–25): impression-to-install rate vs. category benchmark

**Example:**
> *SIPP ASO score at launch: Metadata 18/25 (title strong, description needs benefit front-load), Ratings 0/25 (no ratings yet), Keywords 8/25 (3 keywords in top 50), Conversion 12/25 (2.1% conversion vs. 3.5% Utilities benchmark). Priority action: improve description opening paragraph and run first A/B test on hero screenshot.*

---

### Localization

**Priority Markets:**
1. English (US) — launch market
2. Spanish (US/Mexico) — second-largest US household market
3. English (UK/AU/CA) — fast follow for English-speaking markets
4. French (CA) — regulatory requirement if targeting Canada

**Process:**
1. Identify highest-opportunity markets by category download volume
2. Use professional translators (not machine translation) for title and subtitle
3. Research locale-specific keywords — direct translation rarely captures local search behavior
4. Validate with native speakers before publishing
5. Track downloads by locale to measure localization ROI

**Example:**
> *Spanish (US) keyword research for SIPP: "calidad del agua en casa", "monitor de agua inteligente", "detector de plomo agua" — these outperform direct translations of English keywords by 2–3x in US Hispanic App Store searches.*

---

### Limitations

- Keyword search volume estimates are approximate — Apple and Google do not publish official data
- Apple App Store keyword changes require a full app submission (except Promotional Text)
- Google Play metadata changes take 1–2 hours to index
- A/B testing requires significant traffic volume for statistical significance — plan minimum 2-week windows
- Store ranking algorithms are proprietary and change without notice
- This skill covers organic ASO only — it does not include Apple Search Ads or Google UAC paid strategies
- Does not cover app submission technical issues (provisioning profiles, certificates, signing)
- Benchmarks vary significantly by category — Utilities benchmarks differ from Games

---

### When NOT to Use This Skill

- For web apps or PWAs (use SEO skills instead)
- For enterprise apps not distributed through public stores
- For apps in beta/TestFlight or internal test tracks only
- When you need paid user acquisition strategy (use a marketing/paid-growth skill)

---

### Integration with Other BenOS Skills

- **`product-manager-toolkit`** — define positioning, audience, and feature hierarchy before writing metadata
- **`landing-page-generator`** — sync keyword clusters between app store and web for cross-channel discovery
- **`content-strategy`** — create app descriptions and "What's New" copy
- **GitHub MCP** — pull Flutter repo data (version, bundle ID, release notes) into ASO workflow

---

*Source: Antigravity. Requirements based on Apple App Store and Google Play Store guidelines as of November 2025. Verify current requirements before major launches.*
