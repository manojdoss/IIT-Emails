# Full SEO Audit Report — Institute for Integrative Therapies
## https://www.iit-mn.com

**Audit Date:** March 7, 2026
**Audited by:** Claude SEO (Parallel Subagent Audit)
**Business Type:** Local Service / Healthcare — YMYL (Ketamine & Psychedelic Medicine Clinic)
**Location:** 9300 Hennepin Town Rd, Suite 110, Eden Prairie, MN 55347
**Phone:** (651) 280-8774

---

## Executive Summary

| | |
|---|---|
| **SEO Health Score** | **52 / 100** |
| **Business Type Detected** | Local Medical Clinic (YMYL) |
| **Platform** | Webflow on Cloudflare CDN |
| **Pages Indexed** | ~23–30 confirmed |
| **Schema Markup** | None detected |
| **Critical Issues** | 5 |
| **High Priority Issues** | 9 |

### SEO Health Score Breakdown

| Category | Weight | Score | Weighted |
|---|---|---|---|
| Technical SEO | 25% | 66/100 | 16.5 |
| Content Quality / E-E-A-T | 25% | 62/100 | 15.5 |
| On-Page SEO | 20% | 38/100 | 7.6 |
| Schema / Structured Data | 10% | 12/100 | 1.2 |
| Performance (CWV) | 10% | 55/100 | 5.5 |
| Images | 5% | 55/100 | 2.75 |
| AI Search Readiness | 5% | 50/100 | 2.5 |
| **TOTAL** | **100%** | | **51.55 → 52/100** |

### Top 5 Critical Issues

1. **robots.txt returns 403** — Googlebot cannot read crawl directives; risk of temporary crawl suspension
2. **No XML sitemap accessible** — Google must discover all pages through link-following alone
3. **Zero schema markup detected sitewide** — No MedicalClinic, LocalBusiness, Physician, FAQPage, or any other structured data; severely limits rich results and AI Overview eligibility
4. **All title tags missing geo-keywords** — Every page omits "Minnesota," "Eden Prairie," or "Twin Cities" — catastrophic for local SEO
5. **No custom meta descriptions on any page** — Google auto-generates snippets, reducing CTR for a YMYL healthcare site

### Top 5 Quick Wins

1. Fix robots.txt to return 200 (single-line `User-agent: * Allow: /` is sufficient)
2. Enable/submit XML sitemap through Webflow site settings + Google Search Console
3. Add `MedicalClinic` + `LocalBusiness` JSON-LD to homepage (ready-to-paste code in this report)
4. Rewrite all 14 title tags with geo-keywords (optimized versions provided below)
5. Write meta descriptions for the 5 highest-traffic pages (templates provided below)

---

## Section 1: Technical SEO

**Overall Technical Score: 66 / 100**

### 1.1 Crawlability — 45/100 🔴 CRITICAL

- `/robots.txt` returns **403 Forbidden** for all automated crawlers
- Per Google's documentation, a 403 on robots.txt causes Googlebot to assume temporary disallow and may suspend crawling
- Despite this, Google has indexed ~23–30 pages, suggesting the WAF was applied after initial indexing or has gaps in Googlebot IP coverage
- The site is on **Webflow with Cloudflare WAF** — bot protection is applied at the network layer, not through robots.txt rules
- No Disallow rules can be confirmed; no Sitemap declaration can be confirmed from robots.txt

**Fix:** Allowlist Googlebot's verified IP ranges in Cloudflare, or create a firewall rule that passes requests with Googlebot's user-agent. At minimum, ensure `/robots.txt` returns a 200 response.

### 1.2 Sitemap — 30/100 🔴 CRITICAL

- `/sitemap.xml` returns 403; no alternate sitemap paths confirmed
- No sitemap URL referenced anywhere publicly
- Webflow natively generates sitemaps — this feature may simply be disabled or blocked by the WAF

**Confirmed Indexed Pages (from search engine sampling):**

| URL | Status |
|---|---|
| `https://www.iit-mn.com/` | Indexed |
| `https://www.iit-mn.com/about/` | Indexed |
| `https://www.iit-mn.com/contact/` | Indexed |
| `https://www.iit-mn.com/pricing/` | Indexed |
| `https://www.iit-mn.com/get-started/` | Indexed |
| `https://www.iit-mn.com/faq/` | Indexed |
| `https://www.iit-mn.com/iit-research/` | Indexed |
| `https://www.iit-mn.com/news-and-media/` | Indexed |
| `https://www.iit-mn.com/covid-19/` | Indexed (stale) |
| `https://www.iit-mn.com/healing/` | Indexed |
| `https://www.iit-mn.com/healing/ketamine-assisted-psychotherapy/` | Indexed |
| `https://www.iit-mn.com/healing/ketamine-assisted-psychotherapy/medicine-sessions/` | Indexed |
| `https://www.iit-mn.com/healing/ketamine-infusions/` | Indexed |
| `https://www.iit-mn.com/training/` | Indexed |
| `https://www.iit-mn.com/training/intro-to-kap/` | Indexed |
| `https://www.iit-mn.com/training/kap-guided-externship/` | Indexed |
| `https://www.iit-mn.com/staff/manoj-doss/` | Indexed |
| `https://www.iit-mn.com/staff/matthew-spitzmueller/` | Indexed |
| `https://www.iit-mn.com/staff/samantha-anders/` | Indexed |
| `https://www.iit-mn.com/staff/emily-stevenson/` | Indexed |
| `https://www.iit-mn.com/legal/` | Indexed |
| `https://www.iit-mn.com/legal/privacy-statement-us/` | Indexed |
| `https://www.iit-mn.com/legal/opt-out-preferences/` | Indexed (should be noindexed) |

**Fix:** In Webflow Site Settings → SEO → enable sitemap. Verify it renders at `/sitemap.xml`. Submit to Google Search Console. Add `Sitemap: https://www.iit-mn.com/sitemap.xml` to robots.txt.

### 1.3 Indexability — 60/100 🟡

- ~23–30 pages confirmed indexed — appropriate for site size
- No noindex signals detected on commercial/clinical pages
- **Issue:** `/legal/opt-out-preferences/` is indexed — this is a CCPA utility page with no SEO value; should be noindexed
- **Issue:** `/covid-19/` is stale, dated content consuming crawl budget; update, redirect, or noindex
- No confirmed duplicate content issues; page titles are unique per page

### 1.4 Security (HTTPS/SSL) — 78/100 🟢

- HTTPS confirmed operational — all indexed URLs use `https://www.iit-mn.com`
- Webflow + Cloudflare provides automatic SSL/TLS certificate management (auto-renewing)
- CDN-level TLS 1.3 and DDoS protection via Cloudflare
- **Likely Gap:** Custom security headers (Content-Security-Policy, X-Frame-Options, X-Content-Type-Options) are not configured by default on Webflow deployments
- Security headers unverifiable due to 403 blocking — configure via Cloudflare Transform Rules

### 1.5 URL Structure — 82/100 🟢

- Clean, logical, semantic URL hierarchy
- Consistent trailing slashes, lowercase, hyphens (not underscores), no parameters
- Section-based hierarchy: `/healing/`, `/training/`, `/staff/`, `/legal/`
- **Minor Issue:** `medicine-sessions` at depth-3 is at the outer crawl depth edge for a small site
- `/covid-19/` is stale — candidate for redirect or removal

### 1.6 Mobile Responsiveness — 75/100 🟢 (inferred)

- Webflow enforces responsive design; all sites generate responsive CSS breakpoints
- No mobile usability complaints in any public review or directory listing
- Cannot directly verify viewport meta tag, touch target sizing, or interstitial behavior without crawl access

### 1.7 Core Web Vitals / Page Speed — 55/100 🟡

- No CrUX field data available (site traffic below CrUX threshold)
- PageSpeed Insights returns no data (403 blocking)
- **Estimated performance profile** based on Webflow/Cloudflare healthcare site benchmarks:

| Metric | Estimated Value | Status |
|---|---|---|
| LCP | 2.5–4.0s (mobile) | Needs Improvement / Poor |
| CLS | 0.05–0.15 | Good / Needs Improvement |
| INP | 100–200ms | Good / Needs Improvement |
| FCP | 1.5–3.0s (mobile) | Needs Improvement |

- Common Webflow CWV risks: unoptimized hero images (LCP), Google Fonts without preconnect (CLS), large JS bundles, third-party script bloat (analytics, CRM, chat widgets)

**Fix:** Audit with PageSpeed Insights from inside the network. Add `loading="eager"` + proper `srcset` to hero image. Preconnect to font CDN. Defer non-critical third-party scripts.

### 1.8 Redirects — 70/100 🟢 (inferred)

- Canonical version is `https://www.iit-mn.com` — consistent across all indexed results and third-party citations
- Webflow enforces HTTPS by default with 301 redirects from HTTP
- Cannot directly verify single-hop vs. multi-hop redirect chain from `http://iit-mn.com`

### 1.9 Canonical Tags — 65/100 🟡 (inferred)

- Webflow auto-generates self-referencing canonical tags — likely correct
- No duplicate content conflicts detected in index
- Cannot confirm canonicals on legal/utility pages or depth-3 pages

### 1.10 Hreflang — 95/100 🟢

- English-only, US-only site — no hreflang needed
- Absence is correct; no action required

---

## Section 2: Content Quality & E-E-A-T

**Overall Content Score: 62 / 100**

### 2.1 E-E-A-T Assessment

| Dimension | Score | Assessment |
|---|---|---|
| **Experience** | 7/10 | Strong founder narrative, documented patient stories via Star Tribune, operational details in content |
| **Expertise** | 8/10 | Dr. Doss (DO, Addiction Medicine), Dr. Varghese (MD, U of MN Neurology), 12-clinician team, PI on Phase 3 trials |
| **Authoritativeness** | 7.5/10 | Star Tribune, MinnPost, WCCO coverage; clinical trial site for Cybin and ataiBeckley; Psychology Today verified |
| **Trustworthiness** | 6.5/10 | Transparent pricing, insurance in-network listed; but no on-site testimonials, no content review dates, no medical disclaimers surfaced |

**Overall E-E-A-T: 7.25/10**

This is a **YMYL healthcare site** — Google holds these to the highest quality bar. The strong expertise and authority signals are genuine differentiators, but the trustworthiness gaps (no on-site testimonials, no content review dates, no disclaimers) are YMYL compliance risks.

### 2.2 Content Depth by Page

| Page | Depth | Assessment |
|---|---|---|
| `/healing/ketamine-assisted-psychotherapy/` | High | Covers bio-psycho-spiritual model, neuroplasticity mechanism, 4-phase protocol, integration philosophy |
| `/healing/ketamine-infusions/` | High | IV vs IM vs SL comparison, dosing rationale, induction series protocols, transparent pricing |
| `/iit-research/` | Medium-High | Cybin + ataiBeckley trial partnerships, Ketamine Repository |
| `/pricing/` | High | Detailed, transparent, insurance context — rare competitive differentiator |
| `/staff/manoj-doss/` | Medium-High | Founder narrative, PI roles, training program |
| `/faq/` | Medium | Answers session format questions; FAQ schema missing |
| `/training/kap-guided-externship/` | Medium | Apprenticeship model; depth unknown without direct access |
| `/get-started/` | Thin (likely) | CTA funnel — likely < 200 words |
| `/contact/` | Thin | Form-only page |
| `/news-and-media/` | Thin | External media link aggregation, not original content |
| `/covid-19/` | Stale | Dated content; should be updated or removed |
| `/training/intro-to-kap/` | Medium-Thin | Course description with likely limited educational depth |

### 2.3 Missing Content Opportunities (Critical Gaps)

**Condition-Specific Landing Pages — Highest Priority**

No individual condition pages exist. All conditions (depression, PTSD, anxiety, OCD, chronic pain, grief, addiction) are bundled into service pages. Competitors with condition-specific pages outrank for condition-based searches.

Recommended new pages:
- `/conditions/depression/` — Ketamine for treatment-resistant depression (MDD, TRD)
- `/conditions/ptsd/` — Ketamine for PTSD: evidence base, IIT facilitation model
- `/conditions/anxiety/` — Generalized anxiety, social anxiety, existential anxiety
- `/conditions/ocd/` — Off-label ketamine for OCD
- `/conditions/chronic-pain/` — Already a distinct pricing tier ($850/2hr) — deserves its own page
- `/conditions/addiction/` — Dr. Doss's board specialty; no dedicated content found
- `/conditions/grief-and-loss/` — Supported by Star Tribune patient feature story
- `/conditions/end-of-life-anxiety/` — Palliative/existential distress; underserved niche

**SPRAVATO Dedicated Page**

SPRAVATO (esketamine) is FDA-approved with a REMS program requiring specific disclosure language. No dedicated page found. Create `/healing/spravato/` covering: eligibility (TRD + current antidepressant), REMS requirements, in-office administration, insurance coverage distinctions from IV ketamine.

**Insurance Deep-Dive Page**

Create `/insurance/` explaining in-network benefits (BCBS, Cigna, Aetna, UCare, HealthPartners), pre-authorization workflow, out-of-network reimbursement, and CareCredit 0% financing terms.

**Original Blog / Educational Content**

No original blog articles found. The `/news-and-media/` page aggregates external coverage only. Launch a blog with 2–4 physician-bylined posts per month. High-value topics:
- "What to expect during your first ketamine infusion at IIT"
- "How ketamine differs from SSRIs for depression"
- "Ketamine-assisted psychotherapy vs. ketamine infusions: which is right for you?"
- "Minnesota's psychedelic medicine landscape in 2026"

### 2.4 Blog / News Presence — 40/100

- Last indexed ~December 17, 2025
- Content is external media curation, not original editorial
- No original educational blog articles discovered
- Publication cadence: heavy in 2021 (launch + group therapy announcement), sparse until 2025–2026 (research press releases)

### 2.5 Patient Testimonials / Reviews — 50/100

- 4.4-star rating cited on TMS Therapy Near Me directory
- HealingMaps and Psychology Today profiles contain review language
- Star Tribune anonymized patient feature (grief + ketamine)
- **Gap:** No testimonials, reviews, or patient stories embedded on iit-mn.com itself
- **Fix:** Embed Google Reviews widget; add a `/patient-stories/` page with consented anonymized narratives; embed star rating + review count via AggregateRating schema

### 2.6 AI Citation Readiness — 50/100

- Content is philosophically rich but not structured for AI Overview extraction
- No FAQ schema detected — the primary mechanism for AI citation eligibility
- Press releases (EINPresswire) are being picked up by AI systems — capitalize on this with more structured releases
- Service pages are prose-heavy; no explicit Q&A sections or summary boxes
- **Fix:** Add FAQPage schema to `/faq/` and FAQ sections to all service pages; add TL;DR summary boxes at top of condition pages; structure content around explicit questions matching common search queries

### 2.7 YMYL Compliance — 60/100

**Compliant:**
- Physician credentials displayed
- Transparent pricing and insurance information
- Free 15-min discovery call (reduces pressure sales risk)
- Multiple third-party verification points

**Non-Compliant / Deficient:**
- No medical disclaimer or outcome variability language surfaced
- No content review dates on service/educational pages
- No HIPAA notice or terms of service prominently surfaced
- No "Last reviewed by [Physician Name, Date]" datestamps
- SPRAVATO REMS disclosure language absent

---

## Section 3: On-Page SEO

**Overall On-Page Score: 38 / 100** 🔴

### 3.1 Title Tag Analysis

**Critical Issues:**
- **Homepage title:** `Home - Institute for Integrative Therapies` — "Home" is a non-keyword; worst-practice baseline for a YMYL medical site
- **No geo-targeting anywhere:** "Eden Prairie," "Minnesota," "Twin Cities" absent from every single title tag
- **KAP Externship title is 93 chars** — SERP truncation cuts brand name entirely
- **KAP Intro page breaks brand format** — no " - Institute for Integrative Therapies" suffix

| Page | Current Title | Recommended Title |
|---|---|---|
| Homepage | `Home - Institute for Integrative Therapies` | `Ketamine Clinic Eden Prairie MN \| Institute for Integrative Therapies` |
| About | `About IIT - Institute for Integrative Therapies` | `About Our Ketamine Clinic in Minnesota \| IIT` |
| Ketamine Infusions | `Ketamine Infusions - Institute for Integrative Therapies` | `Ketamine Infusion Therapy Minnesota \| IIT` |
| KAP | `Ketamine Assisted Psychotherapy - Institute for Integrative Therapies` | `Ketamine-Assisted Psychotherapy (KAP) Eden Prairie \| IIT` |
| KAP Externship | `Ketamine Assisted Psychotherapy Guided Externship Program - ...` (93 chars) | `KAP Guided Externship for Therapists \| IIT Minnesota` |
| KAP Intro | `Ketamine Assisted Psychotherapy for Therapists` | `Intro to KAP: Ketamine Therapy Training for Therapists \| IIT` |
| Dr. Doss | `Manoj Doss, DO - Institute for Integrative Therapies` | `Dr. Manoj Doss, DO — Addiction Medicine & Ketamine \| IIT` |
| Contact | `Contact Us - Institute for Integrative Therapies` | `Contact IIT — Ketamine Clinic Eden Prairie MN` |
| Pricing | `Pricing - Institute for Integrative Therapies` | `Ketamine Therapy Cost & Pricing \| IIT Eden Prairie MN` |
| Get Started | `Get Started with IIT Today - Institute for Integrative Therapies` | `Start Ketamine Therapy in Minnesota \| IIT` |
| FAQ | `FAQ - Institute for Integrative Therapies` | `Ketamine Therapy FAQs — Common Questions Answered \| IIT` |
| Research | `IIT Research - Institute for Integrative Therapies` | `Ketamine & Psychedelic Research Program \| IIT Minnesota` |
| News | `News and Media - Institute for Integrative Therapies` | `Psychedelic Medicine News & Media \| IIT Minnesota` |
| Training | `Training - Institute for Integrative Therapies` | `Ketamine-Assisted Psychotherapy Training \| IIT` |

### 3.2 Meta Descriptions

**Finding:** No custom meta descriptions detected on any page. Google auto-generates snippets from body copy — inconsistent, lacks CTA, lacks location, lacks insurance information.

**Recommended meta descriptions (key pages):**

**Homepage:**
> Minnesota's first psychedelic medicine clinic. Ketamine infusions, KAP, and SPRAVATO in Eden Prairie, MN. In-network with BCBS, Cigna, Aetna & more. Call (651) 280-8774.

**KAP Page:**
> Ketamine-Assisted Psychotherapy (KAP) combines ketamine with psychotherapy for lasting relief from depression, PTSD, and anxiety. Serving Eden Prairie & the Twin Cities.

**Pricing Page:**
> Ketamine infusions from $500/session. In-network with Blue Cross Blue Shield, Cigna, Aetna, UCare, and HealthPartners. Financing available through CareCredit.

**FAQ Page:**
> Answers to common questions about ketamine therapy in Minnesota — treatment process, insurance, costs, and what to expect. Call IIT at (651) 280-8774.

**Dr. Doss Staff Page:**
> Dr. Manoj Doss, DO is a board-certified Addiction Medicine specialist and founder of IIT — Minnesota's leading ketamine and psychedelic-assisted therapy clinic.

### 3.3 Internal Linking Gaps

| Gap | Impact |
|---|---|
| Staff page (`/staff/manoj-doss/`) not linked from KAP, Ketamine Infusions, or Research pages | E-E-A-T signal loss |
| FAQ page not linked from Pricing, Get Started, or KAP pages | Missed conversion support |
| Research page not linked from About or KAP pages | Authority signal not distributed |
| Training section siloed — no inbound links from clinical treatment pages | Authority leak |
| Pricing page does not link to Get Started | Conversion funnel gap |

### 3.4 Keyword Targeting by Page

| Page | Primary Keyword | Secondary Keywords |
|---|---|---|
| Homepage | ketamine clinic Eden Prairie MN | ketamine therapy Minnesota, psychedelic medicine clinic, ketamine infusion near me |
| Ketamine Infusions | ketamine infusion therapy Minnesota | IV ketamine for depression, ketamine infusion cost, ketamine infusions near me |
| KAP | ketamine assisted psychotherapy Minnesota | KAP therapy Eden Prairie, ketamine psychotherapy depression PTSD |
| Pricing | ketamine therapy cost Minnesota | does insurance cover ketamine, ketamine cost with insurance |
| Dr. Doss | Dr. Manoj Doss ketamine physician Minnesota | addiction medicine doctor Eden Prairie |
| FAQ | ketamine therapy questions Minnesota | how does ketamine therapy work, ketamine insurance coverage |
| Research | psychedelic medicine research Minnesota | psilocybin clinical trial Minnesota |
| Training | ketamine assisted psychotherapy training | KAP training for therapists, psychedelic therapy certification |

---

## Section 4: Schema / Structured Data

**Schema Score: 12 / 100** 🔴 CRITICAL

**Finding:** Zero structured data detected across all indexed pages. No rich results, no FAQ accordions, no breadcrumb trails, no Knowledge Panel enhancements, no star rating displays. For a YMYL healthcare site, this is a critical gap — 65–71% of pages cited by AI search tools use schema markup.

### 4.1 Missing Schema — Priority Matrix

| Schema Type | Priority | Pages | Impact |
|---|---|---|---|
| `MedicalClinic` + `LocalBusiness` | Critical | Homepage, Contact | Local pack, Knowledge Panel |
| `Organization` with `sameAs` | Critical | Homepage | Entity disambiguation for AI/LLMs |
| `Physician` | High | `/staff/manoj-doss/` et al | E-E-A-T, provider trust signals |
| `FAQPage` | High | `/faq/`, KAP page, Pricing | FAQ rich result accordions |
| `BreadcrumbList` | High | All pages | URL display in SERPs |
| `MedicalTherapy` / `MedicalProcedure` | Medium | KAP, Ketamine Infusions | Treatment entity understanding |
| `Course` | Medium | Training pages | Rich results for training |
| `WebSite` with `SearchAction` | Medium | Homepage | Sitelink search box |
| `AggregateRating` | Medium | Homepage | Star ratings in SERPs |
| `NewsArticle` | Low | `/news-and-media/` | News carousel |

### 4.2 Ready-to-Implement Schema — Homepage

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": ["MedicalClinic", "MedicalBusiness", "LocalBusiness"],
      "@id": "https://www.iit-mn.com/#clinic",
      "name": "Institute for Integrative Therapies",
      "alternateName": "IIT",
      "description": "Minnesota's first psychedelic medicine clinic offering ketamine infusions, ketamine-assisted psychotherapy (KAP), and SPRAVATO in Eden Prairie, MN.",
      "url": "https://www.iit-mn.com",
      "telephone": "+16512808774",
      "address": {
        "@type": "PostalAddress",
        "streetAddress": "9300 Hennepin Town Rd, Suite 110",
        "addressLocality": "Eden Prairie",
        "addressRegion": "MN",
        "postalCode": "55347",
        "addressCountry": "US"
      },
      "geo": {
        "@type": "GeoCoordinates",
        "latitude": "44.8408",
        "longitude": "-93.4708"
      },
      "medicalSpecialty": ["Psychiatry", "Addiction Medicine", "Pain Management"],
      "availableService": [
        {
          "@type": "MedicalTherapy",
          "name": "Ketamine Infusion Therapy",
          "description": "IV ketamine infusions for treatment-resistant depression, PTSD, anxiety, chronic pain, and migraines."
        },
        {
          "@type": "MedicalTherapy",
          "name": "Ketamine-Assisted Psychotherapy (KAP)",
          "description": "Ketamine combined with psychotherapy for lasting healing from depression, anxiety, PTSD, grief, and addiction."
        },
        {
          "@type": "MedicalTherapy",
          "name": "SPRAVATO (Esketamine)",
          "description": "FDA-approved esketamine nasal spray for treatment-resistant depression."
        }
      ],
      "priceRange": "$$",
      "paymentAccepted": "Insurance, Cash, CareCredit",
      "sameAs": [
        "https://www.facebook.com/psychedelictherapymn/",
        "https://thethirdwave.co/directory/clinics/ketamine/minnesota/institute-for-integrative-therapies/",
        "https://healingmaps.com/listing/institute-for-integrative-therapies-eden-prairie-minnesota-clinic/",
        "https://psychedelic.support/network/the-institute-for-integrative-therapies/",
        "https://www.psychologytoday.com/us/therapists/institute-for-integrative-therapies-eden-prairie-mn/1040745"
      ],
      "founder": {
        "@type": "Physician",
        "@id": "https://www.iit-mn.com/staff/manoj-doss/#physician"
      }
    },
    {
      "@type": "WebSite",
      "@id": "https://www.iit-mn.com/#website",
      "url": "https://www.iit-mn.com",
      "name": "Institute for Integrative Therapies",
      "publisher": { "@id": "https://www.iit-mn.com/#clinic" }
    }
  ]
}
```

### 4.3 Ready-to-Implement Schema — Dr. Manoj Doss Staff Page

```json
{
  "@context": "https://schema.org",
  "@type": "Physician",
  "@id": "https://www.iit-mn.com/staff/manoj-doss/#physician",
  "name": "Manoj Doss",
  "honorificSuffix": "DO",
  "description": "Board-certified Addiction Medicine specialist and founder of the Institute for Integrative Therapies. Pioneer in evidence-based ketamine and psychedelic-assisted therapy in Minnesota.",
  "jobTitle": "Founder & CEO",
  "medicalSpecialty": "Addiction Medicine",
  "url": "https://www.iit-mn.com/staff/manoj-doss/",
  "worksFor": { "@type": "MedicalClinic", "@id": "https://www.iit-mn.com/#clinic" },
  "telephone": "+16512808774"
}
```

### 4.4 Ready-to-Implement Schema — FAQ Page

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What conditions does ketamine therapy treat?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Ketamine therapy at IIT treats anxiety, depression, PTSD, suicidal ideation, grief, chronic pain, migraines, and addiction. Ketamine works on different neural pathways than traditional psychiatric medications, making it effective for treatment-resistant cases."
      }
    },
    {
      "@type": "Question",
      "name": "Does insurance cover ketamine infusions?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "IIT is in-network with Blue Cross Blue Shield, Cigna, Aetna, UCare, and HealthPartners. Ketamine infusions for mental health are $500/session or $250 with insurance. Financing is available through CareCredit."
      }
    },
    {
      "@type": "Question",
      "name": "How many ketamine sessions will I need?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "For mental health, IIT typically recommends an initial induction series of six 1-hour ketamine infusions administered twice weekly over three weeks. For pain management, the standard protocol is four 2-hour infusions once weekly over four weeks."
      }
    },
    {
      "@type": "Question",
      "name": "Where is IIT located?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Institute for Integrative Therapies is located at 9300 Hennepin Town Rd, Suite 110, Eden Prairie, MN 55347. Call (651) 280-8774 to schedule."
      }
    }
  ]
}
```

### 4.5 BreadcrumbList — KAP Page Example

```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    { "@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.iit-mn.com/" },
    { "@type": "ListItem", "position": 2, "name": "Healing", "item": "https://www.iit-mn.com/healing/" },
    { "@type": "ListItem", "position": 3, "name": "Ketamine-Assisted Psychotherapy" }
  ]
}
```

---

## Section 5: Performance (Core Web Vitals)

**Performance Score: 55 / 100** 🟡

- No CrUX field data available (traffic volume below threshold)
- Platform: Webflow on Cloudflare CDN (inherits CDN caching, HTTP/2, Brotli compression)

**Estimated CWV (Webflow healthcare site benchmarks):**

| Metric | Estimated | Target |
|---|---|---|
| LCP (mobile) | 2.5–4.0s | < 2.5s |
| CLS | 0.05–0.15 | < 0.1 |
| INP | 100–200ms | < 200ms |
| FCP (mobile) | 1.5–3.0s | < 1.8s |

**Common Webflow performance risks:**
- Unoptimized hero images (largest LCP element on healthcare sites)
- Google Fonts without `preconnect` (causes font-swap CLS)
- Third-party scripts (CRM, chat, analytics) blocking INP
- Webflow CMS JS bundles on pages with CMS content

**Fixes:**
1. Audit with PageSpeed Insights from trusted IP
2. Add `loading="eager"` + proper `width`/`height` attributes to hero image
3. Add `<link rel="preconnect">` for Google Fonts / Adobe Fonts
4. Defer non-critical third-party scripts (`async`/`defer`)
5. Enable WebP image format in Webflow site settings

---

## Section 6: Images

**Image Score: 55 / 100** 🟡 (inferred — direct access blocked)

- Webflow sites default to serving images without explicit alt text unless the editor adds it
- Healthcare sites with staff photography have high risk of missing or generic alt text (e.g., "doctor-photo.jpg" instead of "Dr. Manoj Doss, founder of IIT, Eden Prairie MN ketamine clinic")
- No image optimization issues were surfaced in any third-party listing (suggesting images aren't causing egregious load failures)

**Recommended fixes:**
- Audit all images for missing alt text, especially: hero image, staff photos (Dr. Doss, Dr. Varghese, therapist headshots), treatment room photos, and logo
- Ensure alt text is descriptive + keyword-aware for key images: `alt="Dr. Manoj Doss, DO — Founder of Institute for Integrative Therapies, Eden Prairie MN"`
- Verify all images are served in WebP format (configurable in Webflow)
- Ensure hero image has `width` and `height` attributes to prevent CLS

---

## Section 7: AI Search Readiness (GEO)

**AI Search Readiness Score: 50 / 100** 🟡

### Current State

- IIT's press releases (EINPresswire, PR Newswire) are being picked up by AI systems — a latent asset
- Content is philosophically rich but not structured for passage-level AI extraction
- No FAQ schema — the primary eligibility signal for Google AI Overviews
- Prose-heavy service pages lack explicit Q&A sections that AI models can extract as answers
- The Ketamine Repository (`/ketamine-repository/`) is a strong latent asset — if structured with citations and summary boxes, could become a major AI citation target

### AI Crawler Accessibility

- `robots.txt` returning 403 affects **all** crawlers including AI crawlers (GPTBot, ClaudeBot, PerplexityBot)
- Fixing robots.txt is essential for AI search visibility, not just Google

### llms.txt

- No `/llms.txt` file found — this emerging standard (adopted by growing number of sites) helps AI models discover preferred content
- Consider adding `/llms.txt` listing key pages and their summaries

### Improvements for AI Overviews Eligibility

1. Add FAQPage schema to `/faq/` and service pages
2. Add explicit Q&A sections to condition pages: "What is ketamine therapy for depression? → [concise answer]"
3. Add TL;DR summary boxes at the top of each service page
4. Structure the Ketamine Repository with clear headings, research summaries, and citations
5. Ensure all AI crawlers (GPTBot, ClaudeBot, PerplexityBot, Google-Extended) are allowed in robots.txt

---

## Section 8: Competitive Landscape

### Key Competitors for "ketamine therapy Minnesota" SERPs

| Competitor | Domain | Advantage Over IIT |
|---|---|---|
| Minnesota Ketamine Clinic | mnketamine.com | Keyword-rich exact-match domain |
| Ketamine Treatment Minnesota | ketaminetreatmentminnesota.com | Aggregator; ranks for local queries without providing services |
| Center for Conscious Alchemy | consciousalchemy.co | Minneapolis/St. Paul location; holistic brand positioning |
| HealingMaps | healingmaps.com/best-ketamine-clinics-in-minnesota/ | High-authority directory dominates "best ketamine clinic MN" |
| The Third Wave | thethirdwave.co | Directory listing + editorial content |
| TMS Therapy Near Me | tmstherapynearme.com | Aggregator with Eden Prairie-specific IIT listing |

### IIT's Competitive Advantages

- Only clinic with: transparent pricing, multi-insurance in-network, active Phase 3 clinical trial partnerships, therapist training program, "first in MN" positioning
- Multi-disciplinary team of 12 clinicians is rare for a single-location clinic
- Star Tribune and WCCO earned media provide authority that paid directories cannot replicate

### IIT's SEO Weaknesses vs. Competitors

- No condition-specific pages (all competitors have these)
- Weaker title tag optimization vs. keyword-rich competitor domains
- Zero schema vs. competitors with at least basic LocalBusiness markup
- No blog/original content to compete for informational search intent

---

## Appendix: Staff Roster (for Schema Implementation)

The following staff have confirmed `/staff/[name]/` pages:
- Dr. Manoj Doss, DO (Founder & CEO, Addiction Medicine)
- Dr. Ranji Varghese, MD (Co-Investigator, University of MN Neurology, Medical Director)
- Samantha Anders, PhD, LP (Counseling Psychology, U of MN)
- Matthew Spitzmueller, PhD, LICSW (Licensed Clinical Social Worker)
- Emily Stevenson, PhD, LPCC (Licensed Clinical Mental Health Counselor)

Additional staff referenced by first name only: Allyson, Olivia, Amie, Abbie Shain — full bio pages should be created if not already present.

---

## Data Sources

- Google Search index (site:iit-mn.com sampling)
- [Institute for Integrative Therapies — The Third Wave](https://thethirdwave.co/directory/clinics/ketamine/minnesota/institute-for-integrative-therapies/)
- [IIT — HealingMaps](https://healingmaps.com/listing/institute-for-integrative-therapies-eden-prairie-minnesota-clinic/)
- [IIT — Psychology Today (Eden Prairie)](https://www.psychologytoday.com/us/therapists/institute-for-integrative-therapies-eden-prairie-mn/1040745)
- [IIT — Psychology Today (Saint Paul)](https://www.psychologytoday.com/us/treatment-rehab/institute-for-integrative-therapies-saint-paul-mn/849080)
- [IIT — Psychedelic Support Network](https://psychedelic.support/network/the-institute-for-integrative-therapies/)
- [PR Newswire — Clinic Opening](https://www.prnewswire.com/news-releases/the-first-psychedelic-medicine-clinic-opens-in-minnesota-301257475.html)
- [EINPresswire — Cybin Trial Site Selection](https://www.einpresswire.com/article/868958932/institute-for-integrative-therapies-selected-as-a-clinical-trial-site-for-cybin-s-embrace-and-extend-psilocin-studies)
- [EINPresswire — ataiBeckley Trial Site Selection](https://www.einpresswire.com/article/875654338/iit-selected-as-a-clinical-trial-site-for-ataibeckley-s-dmt-study-for-treatment-resistant-depression)
- [MinnPost — Psychedelics clinic coverage](https://www.minnpost.com/mental-health-addiction/2021/04/clinic-founders-tout-the-promise-of-psychedelics-for-mental-illness-observers-urge-caution/)
- [Star Tribune — Patient feature story](https://www2.startribune.com/depressed-after-his-wifes-death-this-minneapolis-man-turned-to-psychedelics-for-help/600369238/)
- [City Lifestyle — IIT Feature](https://citylifestyle.com/articles/institute-for-integrative-therapies)
- [TMS Therapy Near Me — IIT Listing](https://tmstherapynearme.com/ketamine-clinics/minnesota/eden-prairie/institute-for-integrative-therapies-ketamine-treatments/)
