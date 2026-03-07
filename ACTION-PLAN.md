# SEO Action Plan — Institute for Integrative Therapies
## https://www.iit-mn.com

**Generated:** March 7, 2026
**Current SEO Health Score:** 52 / 100
**Target SEO Health Score:** 75 / 100 (achievable in 90 days)

---

## 🔴 CRITICAL — Fix Immediately (Week 1)

These issues block indexing, limit crawlability, or eliminate entire rich result categories.

---

### C1 — Fix robots.txt 403 Error

**Impact:** Technical SEO (crawlability) | **Effort:** Low

**Problem:** `/robots.txt` returns 403 Forbidden. Googlebot cannot read crawl directives. Per Google's documentation, a 403 on robots.txt may trigger temporary crawl suspension. All AI crawlers (GPTBot, ClaudeBot, PerplexityBot) are also affected.

**Fix:**
1. In Cloudflare dashboard → Security → WAF → add a firewall rule to bypass WAF for requests to `/robots.txt`
2. Or: In Cloudflare → Security → Bots → ensure verified bots (Googlebot) are not blocked
3. Verify fix: `curl -A "Mozilla/5.0 (compatible; Googlebot/2.1)" https://www.iit-mn.com/robots.txt`

**Minimum robots.txt content:**
```
User-agent: *
Allow: /

User-agent: Googlebot
Allow: /

# Allow AI crawlers
User-agent: GPTBot
Allow: /

User-agent: ClaudeBot
Allow: /

User-agent: PerplexityBot
Allow: /

Sitemap: https://www.iit-mn.com/sitemap.xml
```

---

### C2 — Generate and Submit XML Sitemap

**Impact:** Indexability | **Effort:** Low

**Problem:** No XML sitemap accessible at any standard path. Google must discover all pages through link-following alone, risking missed pages (staff bios, condition pages once created).

**Fix:**
1. In Webflow: Site Settings → SEO → enable "Auto-generate sitemap"
2. Verify sitemap renders at `https://www.iit-mn.com/sitemap.xml`
3. Submit to Google Search Console: Index → Sitemaps → enter sitemap URL
4. Add `Sitemap: https://www.iit-mn.com/sitemap.xml` to robots.txt

---

### C3 — Implement Homepage Schema (MedicalClinic + LocalBusiness)

**Impact:** Schema, AI Search, Local SEO | **Effort:** Low

**Problem:** Zero structured data detected sitewide. The homepage lacks the foundational MedicalClinic + LocalBusiness schema required for local Knowledge Panel, map pack eligibility, and AI Overview citations.

**Fix:** Add the following JSON-LD in a `<script type="application/ld+json">` block in the Webflow page `<head>` custom code section:

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
      "priceRange": "$$",
      "paymentAccepted": "Insurance, Cash, CareCredit",
      "sameAs": [
        "https://www.facebook.com/psychedelictherapymn/",
        "https://thethirdwave.co/directory/clinics/ketamine/minnesota/institute-for-integrative-therapies/",
        "https://healingmaps.com/listing/institute-for-integrative-therapies-eden-prairie-minnesota-clinic/",
        "https://psychedelic.support/network/the-institute-for-integrative-therapies/",
        "https://www.psychologytoday.com/us/therapists/institute-for-integrative-therapies-eden-prairie-mn/1040745"
      ]
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

**Validate at:** https://search.google.com/test/rich-results

---

### C4 — Rewrite All 14 Title Tags with Geo-Keywords

**Impact:** On-Page SEO, Local SEO, CTR | **Effort:** Low

**Problem:** Every title tag omits geographic keywords. This is a critical failure for a local medical clinic where conversion queries are geo-specific ("ketamine therapy Minnesota," "ketamine clinic Eden Prairie").

**Fix in Webflow:** Each page → SEO Settings → Title

| Page | New Title |
|---|---|
| Homepage | `Ketamine Clinic Eden Prairie MN \| Institute for Integrative Therapies` |
| About | `About Our Ketamine Clinic in Minnesota \| IIT` |
| Ketamine Infusions | `Ketamine Infusion Therapy Minnesota \| IIT` |
| KAP | `Ketamine-Assisted Psychotherapy (KAP) Eden Prairie \| IIT` |
| KAP Externship | `KAP Guided Externship for Therapists \| IIT Minnesota` |
| KAP Intro | `Intro to KAP: Ketamine Therapy Training for Therapists \| IIT` |
| Dr. Doss | `Dr. Manoj Doss, DO — Addiction Medicine & Ketamine \| IIT` |
| Contact | `Contact IIT — Ketamine Clinic Eden Prairie MN` |
| Pricing | `Ketamine Therapy Cost & Pricing \| IIT Eden Prairie MN` |
| Get Started | `Start Ketamine Therapy in Minnesota \| IIT` |
| FAQ | `Ketamine Therapy FAQs — Common Questions Answered \| IIT` |
| Research | `Ketamine & Psychedelic Research Program \| IIT Minnesota` |
| News | `Psychedelic Medicine News & Media \| IIT Minnesota` |
| Training | `Ketamine-Assisted Psychotherapy Training \| IIT` |

---

### C5 — Write Custom Meta Descriptions for All Pages

**Impact:** CTR, YMYL trust signals | **Effort:** Low

**Problem:** No custom meta descriptions on any page. Google auto-generates snippets that lack CTA, location, insurance information, and conversion signals.

**Fix in Webflow:** Each page → SEO Settings → Meta Description

Priority 5 pages:

| Page | Meta Description |
|---|---|
| Homepage | Minnesota's first psychedelic medicine clinic. Ketamine infusions, KAP, and SPRAVATO in Eden Prairie, MN. In-network with BCBS, Cigna, Aetna & more. Call (651) 280-8774. |
| KAP | Ketamine-Assisted Psychotherapy (KAP) combines ketamine with psychotherapy for lasting relief from depression, PTSD, and anxiety. Serving Eden Prairie & the Twin Cities. |
| Pricing | Ketamine infusions from $500/session. In-network with Blue Cross Blue Shield, Cigna, Aetna, UCare, and HealthPartners. Financing available through CareCredit. |
| FAQ | Answers to common questions about ketamine therapy in Minnesota — treatment process, insurance, costs, and what to expect. Call IIT at (651) 280-8774. |
| Dr. Doss | Dr. Manoj Doss, DO is a board-certified Addiction Medicine specialist and founder of IIT — Minnesota's leading ketamine and psychedelic-assisted therapy clinic. |

---

## 🟠 HIGH PRIORITY — Fix Within 2 Weeks

---

### H1 — Add FAQPage Schema to /faq/ and Key Service Pages

**Impact:** Rich results, AI Overview eligibility | **Effort:** Low

Add JSON-LD FAQPage schema (see full code in FULL-AUDIT-REPORT.md Section 4.4) to:
- `/faq/` — primary FAQ page
- `/healing/ketamine-assisted-psychotherapy/` — KAP-specific FAQs
- `/pricing/` — insurance and cost FAQs

---

### H2 — Add Physician Schema to Staff Pages

**Impact:** E-E-A-T, YMYL trust | **Effort:** Low

Add `Physician` JSON-LD schema (see FULL-AUDIT-REPORT.md Section 4.3) to:
- `/staff/manoj-doss/` — priority 1
- `/staff/ranji-varghese/` — priority 2
- All other staff bio pages

---

### H3 — Add BreadcrumbList Schema Sitewide

**Impact:** SERP URL display, site structure signals | **Effort:** Medium (requires per-page or template implementation)

Implement via Webflow embed on each page or inject via a sitewide script. Follow pattern in FULL-AUDIT-REPORT.md Section 4.5.

---

### H4 — Noindex /legal/opt-out-preferences/ and Review /covid-19/

**Impact:** Crawl budget, indexability quality | **Effort:** Very Low

- `/legal/opt-out-preferences/`: Add `<meta name="robots" content="noindex, follow">` in Webflow page settings
- `/covid-19/`: Either update with current information, 301 redirect to `/faq/`, or noindex

---

### H5 — Audit and Fix Core Web Vitals

**Impact:** Rankings, user experience | **Effort:** Medium

1. Temporarily allow PageSpeed Insights bot or run from inside network
2. Identify LCP element (likely hero image) — add `loading="eager"`, explicit `width`/`height`
3. Add `<link rel="preconnect" href="https://fonts.googleapis.com">` if Google Fonts used
4. Audit third-party scripts — defer/async all non-critical scripts
5. Enable WebP image format in Webflow site settings

---

### H6 — Fix Internal Linking Structure

**Impact:** Authority distribution, E-E-A-T | **Effort:** Low-Medium

| Action | Pages Involved |
|---|---|
| Link Dr. Doss staff page from KAP, Ketamine Infusions, and Research pages | 4 pages |
| Link FAQ from Pricing, Get Started, and KAP pages | 4 pages |
| Link Research page from About and KAP pages | 3 pages |
| Link Training section from About page | 2 pages |
| Link Get Started from Pricing page | 2 pages |

---

### H7 — Embed On-Site Patient Testimonials

**Impact:** Trustworthiness, conversion | **Effort:** Medium

- Embed Google Reviews widget on homepage and key service pages
- Create a `/patient-stories/` page with consented anonymized patient narratives
- Add `AggregateRating` schema once on-site reviews are embedded

---

### H8 — Add MedicalTherapy Schema to Service Pages

**Impact:** Treatment-level entity understanding | **Effort:** Low

Add `MedicalTherapy` or `MedicalProcedure` JSON-LD to:
- `/healing/ketamine-infusions/`
- `/healing/ketamine-assisted-psychotherapy/`
- Future `/healing/spravato/` page

---

### H9 — Add Content Review Dates and Medical Disclaimers

**Impact:** YMYL compliance | **Effort:** Low

- Add "Last reviewed by [Dr. Name], [Month Year]" to footer of all service and FAQ pages
- Add brief outcome variability disclaimer to service pages: "Results vary. Ketamine therapy is not appropriate for all patients. Schedule a consultation to determine if you are a candidate."
- Surface HIPAA notice link in site footer

---

## 🟡 MEDIUM PRIORITY — Fix Within 30 Days

---

### M1 — Create Condition-Specific Landing Pages

**Impact:** Organic search traffic, conversions | **Effort:** High (content creation)

**Highest priority pages to create:**

1. `/conditions/treatment-resistant-depression/` — largest search volume, strongest evidence base
2. `/conditions/ptsd/` — high search demand; IIT has clinical trial credibility
3. `/conditions/anxiety/` — broad search intent; good conversion potential
4. `/conditions/chronic-pain/` — already a separate pricing tier; deserves its own page
5. `/conditions/addiction/` — Dr. Doss's board specialty; significant content authority opportunity

**Minimum page structure for each:**
- H1: "Ketamine Therapy for [Condition] in Minnesota"
- What is [condition] and why standard treatments fail
- How ketamine works for [condition] (mechanism + evidence)
- IIT's approach (bio-psycho-spiritual model)
- What to expect (4-phase protocol)
- Is ketamine right for you? (candidacy criteria)
- FAQ section (with FAQPage schema)
- CTA: Schedule a free discovery call

---

### M2 — Create Dedicated SPRAVATO Page

**Impact:** Organic traffic, REMS compliance | **Effort:** Medium

Create `/healing/spravato/` covering:
- What is SPRAVATO (esketamine)?
- FDA approval and REMS program requirements
- Eligibility: treatment-resistant depression + current antidepressant
- In-office administration requirements
- Insurance coverage (distinct from IV ketamine)
- Comparison with IV ketamine infusions

---

### M3 — Launch Original Blog with Physician Bylines

**Impact:** Authoritativeness, AI citations, long-tail traffic | **Effort:** High (ongoing)

**Recommended first 6 articles:**
1. "What to Expect During Your First Ketamine Infusion at IIT"
2. "How Ketamine Differs from SSRIs for Treatment-Resistant Depression"
3. "Ketamine-Assisted Psychotherapy vs. Ketamine Infusions: Which Is Right for You?"
4. "IIT's Research Partnerships: What Phase 3 Clinical Trials Mean for Patients"
5. "Understanding Insurance Coverage for Ketamine Therapy in Minnesota"
6. "Minnesota's Psychedelic Medicine Landscape in 2026"

**Requirements:** All articles must have physician byline (Dr. Doss or Dr. Varghese), publication date, last-reviewed date, and references to research sources.

---

### M4 — Create /insurance/ Standalone Page

**Impact:** Trustworthiness, conversion | **Effort:** Medium

Create `/insurance/` covering:
- In-network insurers: BCBS, Cigna, Aetna, UCare, HealthPartners
- What's covered vs. what's out-of-pocket
- Pre-authorization process
- Out-of-network reimbursement path
- CareCredit 0% financing (6-month terms)
- Step-by-step: how to use insurance at IIT

---

### M5 — Add Course Schema to Training Pages

**Impact:** Rich results for professional audience | **Effort:** Low

Add `Course` JSON-LD to:
- `/training/intro-to-kap/`
- `/training/kap-guided-externship/`

---

### M6 — Configure Security Headers via Cloudflare

**Impact:** Technical security score | **Effort:** Low-Medium

In Cloudflare Transform Rules, add response headers:
- `Strict-Transport-Security: max-age=31536000; includeSubDomains`
- `X-Content-Type-Options: nosniff`
- `X-Frame-Options: SAMEORIGIN`
- `Referrer-Policy: strict-origin-when-cross-origin`

---

### M7 — Add Remaining Staff Bio Pages

**Impact:** E-E-A-T, team authority | **Effort:** Medium

Confirm and complete bio pages for all 12 team members. Currently named staff without confirmed `/staff/[name]/` pages: Allyson, Olivia, Amie, Abbie Shain. Each page should include: full name + credentials, specialties, populations served, training, and `Physician` or `Person` schema.

---

## 🟢 LOW PRIORITY — Backlog (30–90 Days)

---

### L1 — Create /patient-stories/ Page

Consented, anonymized patient narratives with specific conditions, treatment modality, and outcomes. Cite the Star Tribune story as proof of concept.

### L2 — Create /research/publications/ Page

List Dr. Doss as co-author or PI on any published papers. Include ClinicalTrials.gov NCT numbers for active trials. This is a direct E-E-A-T signal.

### L3 — Create Minnesota Psychedelic Policy Resource Page

Own the informational niche for Minnesota's psychedelic medicine regulatory landscape. The MN Department of Health Psychedelic Medicine Task Force is active; IIT is a natural authority source.

### L4 — Add /llms.txt File

Create `/llms.txt` listing key pages and their summaries for AI model discovery. This emerging standard is increasingly adopted by healthcare and professional service sites.

### L5 — Optimize Google Business Profile

Ensure GBP NAP (Name/Address/Phone) matches schema markup exactly. Add services, photos, Q&A, and posts. Respond to all existing reviews. This is the primary local pack ranking signal.

### L6 — Add WebSite SearchAction Schema

Adds sitelink search box eligibility in Google. Already included in C3 homepage schema block above — verify rendering after C3 implementation.

### L7 — Create /conditions/grief-and-loss/ and /conditions/end-of-life-anxiety/

Niche differentiators backed by Star Tribune coverage and clinical experience. Lower search volume but high authority and conversion potential.

---

## Score Projections

| Timeline | Actions Completed | Projected Score |
|---|---|---|
| Current | None | 52/100 |
| Week 1 | C1–C5 completed | ~60/100 |
| Week 2 | + H1–H4 | ~65/100 |
| Month 1 | + H5–H9 | ~70/100 |
| Month 3 | + M1–M7 | ~78/100 |
| Month 6 | + L1–L7 + blog cadence | ~85/100 |

---

## Quick Reference Checklist

### Week 1 (Critical)
- [ ] C1: Fix robots.txt 403 in Cloudflare
- [ ] C2: Enable sitemap in Webflow + submit to GSC
- [ ] C3: Add MedicalClinic + LocalBusiness schema to homepage
- [ ] C4: Rewrite all 14 title tags with geo-keywords
- [ ] C5: Write meta descriptions for all pages

### Week 2 (High)
- [ ] H1: Add FAQPage schema to /faq/ and service pages
- [ ] H2: Add Physician schema to all staff bio pages
- [ ] H3: Add BreadcrumbList schema sitewide
- [ ] H4: Noindex /legal/opt-out-preferences/ + review /covid-19/
- [ ] H9: Add content review dates and medical disclaimers

### Month 1
- [ ] H5: CWV audit and image/font optimization
- [ ] H6: Fix internal linking structure (5 actions)
- [ ] H7: Embed on-site patient testimonials + AggregateRating schema
- [ ] H8: Add MedicalTherapy schema to service pages
- [ ] M5: Add Course schema to training pages
- [ ] M6: Configure security headers in Cloudflare

### Month 2–3
- [ ] M1: Create condition-specific landing pages (start with Depression + PTSD)
- [ ] M2: Create dedicated SPRAVATO page
- [ ] M3: Launch blog — publish first 3 articles with physician bylines
- [ ] M4: Create /insurance/ standalone page
- [ ] M7: Complete remaining staff bio pages

### Month 3–6 (Backlog)
- [ ] L1–L7: Patient stories, publications page, GBP optimization, llms.txt
