# AimoneAdvisory.com — Custom Code

Webflow site ID: `6a18c6fe71e5ae144f192359`  
Production domains: `aimoneadvisory.com`, `www.aimoneadvisory.com`

## Files

### `site-head.html`
**Location in Webflow:** Site Settings → Custom Code → Head Code

- Applies global font smoothing
- On every page load, checks `sessionStorage.aa_seen`; if set, immediately injects CSS to hide `.loader-component` before Webflow IX2 renders it — preventing animation replay on internal navigation

### `home-footer.html`
**Location in Webflow:** Home page → Page Settings → Custom Code → Footer Code

- Fixes "Learn More" link hrefs to point at the correct sub-pages (`/organization-based-services`, `/individual-based-services`)
- Uses a `MutationObserver` to detect when Webflow IX2 hides `.loader-component` at the end of the intro animation
- Runs an invisible scroll pass (behind a full-screen cover overlay) to trigger all Webflow IX2 scroll-reveal animations, so the full page appears without requiring user scroll
- Sets `sessionStorage.aa_seen = '1'` so subsequent visits to home skip the animation entirely
- 7-second safety fallback in case the observer never fires
- Injects a Perspectives teaser section before the footer

### `individuals-footer.html`
**Location in Webflow:** For Individuals page → Page Settings → Custom Code → Footer Code

- Appends two new pricing items to `.pricing-track`: AI Readiness Assessment ($350) and Personal Automation (from $50 with link to /automation)
- Injects an automation teaser section below the page's last section

### `organizations-footer.html`
**Location in Webflow:** For Organizations page → Page Settings → Custom Code → Footer Code

- Inserts Team AI Workshop ($1,000-$2,500) and Org AI Readiness Assessment ($500) before the Diagnostic Session pricing item
- Adds a 501(c)(3) pro bono note below the pricing track

### `about-footer.html`
**Location in Webflow:** About page → Page Settings → Custom Code > Footer Code

- Injects a "Nonprofit & Pro Bono Advisory" section at the bottom of the page with anchor `#nonprofit`
- CTA links to /contact

### `automation-footer.html`
**Location in Webflow:** Automation Services page → Page Settings → Custom Code → Footer Code

- Appends 4 additional catalog items (CRM Digest, Document Summarizer, Research Brief, Custom Automation)
- Adds "How it works" process note below the catalog
- Updates CTA button text from "Book a Free Call" to "Book & Pay"
- Updates section subtitle to reflect pay-and-book model

## Navbar style fix
The `services-nav-toggle` style in Webflow has `padding-left: 0px; padding-right: 0px` — this removes the default Webflow `w-dropdown-toggle` padding (40px right) that was creating a gap between "Services" and "About" in the nav.

## Page structure
| Page | Slug | Webflow ID |
|------|------|------------|
| Home | `/` | `6a18c70171e5ae144f1923bf` |
| For Organizations | `/organization-based-services` | `6a588a5ab6207238247fde52` |
| For Individuals | `/individual-based-services` | `6a588a5ab2363838e6910b30` |
| Automation Services | `/automation` | `6a5a888d73e07b08da2b534e` |
| About | `/about` | `6a45651fe68180b39657f4bf` |
| Perspectives | `/perspectives` | `6a59aecacd81f1fb0f915bf2` |
| Projects | `/projects` | `6a456521ca2de91698e3597a` |

## Automation catalog (as of July 2026)
Set via Webflow Designer (pricing-item elements) + automation-footer.html:

| Automation | Price |
|-----------|-------|
| Daily Morning Brief | $50 |
| Email Response Drafter | $75 |
| Meeting Prep Package | $75 |
| Weekly Progress Report | $97 |
| AI Setup & Training (1:1) | $75/session |
| CRM / Pipeline Digest | $97 |
| Document Summarizer | $50 |
| Research Brief | $75 |
| Custom Automation | From $150 |
