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

## Navbar style fix
The `services-nav-toggle` style in Webflow has `padding-left: 0px; padding-right: 0px` — this removes the default Webflow `w-dropdown-toggle` padding (40px right) that was creating a gap between "Services" and "About" in the nav.

## Page structure
| Page | Slug | Webflow ID |
|------|------|------------|
| Home | `/` | `6a18c70171e5ae144f1923bf` |
| For Organizations | `/organization-based-services` | `6a588a5ab6207238247fde52` |
| For Individuals | `/individual-based-services` | `6a588a5ab2363838e6910b30` |
| Projects | `/projects` | `6a456521ca2de91698e3597a` |
