# GHL Theme Usage & Client Intake Manual — v1.0

> **Status:** Approved and published to GitHub.  
> **Repository:** [mgbdomingo/ghl-theme-temp](https://github.com/mgbdomingo/ghl-theme-temp)  
> **Current theme:** [elevate_safe_sidebar_v2.css](https://github.com/mgbdomingo/ghl-theme-temp/blob/main/elevate_safe_sidebar_v2.css)  
> **Audience:** Agency admins, implementers, and client-facing team members.

## 1. What this theme does

The current Elevate Tax Solutions v2.0 stylesheet is a **minimal sidebar theme** for the desktop HighLevel web application. It changes:

- Sidebar background to deep purple (`#3F294C`).
- Sidebar navigation text to white (`#FFFFFF`).
- Navigation hover background to purple (`#563765`).
- Active navigation background to a lighter purple (`#674476`).
- Keyboard-focus outline to muted gold (`#D8BB87`).

**Not included:** dashboard-wide colors, buttons, forms, logos, icon replacement, font changes, JavaScript, or structural layout changes.

**Important:** CSS selectors are based on public examples and the earlier account stylesheet. They have **not been verified in every current GHL screen or in your logged-in account**. A HighLevel UI update may change which selectors work.

## 2. Before installing (required)

1. Confirm you have appropriate **Agency** settings access.
2. Choose a time when you can test the affected account immediately.
3. Copy the **entire current Custom CSS** into a dated backup file (example: `backup-before-elevate-2026-10-23.css`). Keep this backup outside GHL.
4. Confirm the change scope with the client. **Agency-level Custom CSS can affect client-facing views across the agency; do not assume it only changes one sub-account.**
5. Check which format your specific GHL Custom CSS editor accepts. Your previous working stylesheet was **raw CSS**. HighLevel's Company Settings guide recommends wrapping CSS with `<style>...</style>`, while other official examples show raw CSS. Follow your field's instructions; do not add wrappers blindly.
6. Do **not** combine the old theme and new theme. Duplicate rules may conflict.

## 3. Install the current Elevate theme

1. Open the [CSS file on GitHub](https://github.com/mgbdomingo/ghl-theme-temp/blob/main/elevate_safe_sidebar_v2.css).
2. Open **Raw** and copy the entire stylesheet.
3. In your HighLevel **Agency View**, go to **Settings → Company → Whitelabel → Custom CSS**. (The label/location may vary slightly by account UI.)
4. Save your current Custom CSS as a backup before making any changes.
5. **Replace** the previous theme CSS with the new theme CSS (not append). If your editor explicitly requires style tags, use its required format; otherwise retain the raw-CSS format that already works for your account.
6. Save the setting, refresh the desktop dashboard, and test the screens below.
7. Record the date, version, tested account, and result in your change notes.

**Important:** If you want only **one client's sub-account** branded differently, **stop here** and confirm an officially supported account-specific injection method or validated account-scoped selector. This repository's current file does not implement client-specific scoping. Applying it at agency level can affect other clients.

## 4. Post-install test checklist

Check each item after applying the CSS:

- [ ] Sidebar opens, closes, and scrolls normally.
- [ ] Sidebar text and icons are visible on dark and highlighted backgrounds.
- [ ] Active menu is readable; hover state is readable.
- [ ] Keyboard Tab focus is visible on sidebar links.
- [ ] Location/account switcher is readable and clickable.
- [ ] Dashboard opens; cards and buttons are still usable.
- [ ] Contacts, Conversations, Opportunities, Calendars, and Settings work normally.
- [ ] Documents/Contracts and any frequently used builders are not visually distorted.
- [ ] Test at normal and narrower browser widths.
- [ ] Test at least one account that could be affected by the agency-level change.

**Pass criteria:** readable text, no missing controls, no unintended color changes outside the sidebar, and no navigation problems. If any check fails, revert before doing further customization.

## 5. How to change branding safely

Edit only these tokens under `:root` in `elevate_safe_sidebar_v2.css`:

```css
:root {
  --ets-sidebar-bg: #3F294C;      /* Default sidebar */
  --ets-sidebar-hover: #563765;   /* Hovered menu item */
  --ets-sidebar-active: #674476;  /* Current page */
  --ets-sidebar-text: #FFFFFF;    /* Menu text */
  --ets-gold: #D8BB87;            /* Keyboard focus */
}
```

Recommended editing workflow: **change one or two variables → test → keep or revert**. Always verify normal-size text against each relevant background at **4.5:1 contrast or higher** (WCAG AA). Do not assume an accent color is suitable for text. Fonts and unrelated components are intentionally excluded from v2.0; request them as separate revisions.

## 6. Troubleshooting and rollback

| Symptom | First check | Safe action |
|---|---|---|
| Sidebar text disappears | Text/icon/background contrast | Restore the backup CSS |
| Links, dropdowns, or switcher look wrong | Selector affecting nested UI | Restore; document the screen and screenshot |
| Changes don't appear | Save state, cache, or CSS field format | Refresh; check editor instructions; avoid stacking multiple copies |
| Only some screens update | Different markup or updated selectors | Inspect the affected element before proposing a targeted change |
| Multiple clients changed unexpectedly | Agency-level scope | Revert and validate a client-specific approach |

**Rollback:** Replace the theme in the Custom CSS editor with your saved, known-good CSS (or temporarily clear the theme CSS), save, and refresh. If you cannot reach settings, contact an agency admin or HighLevel support. Do not rely on incognito mode to bypass centrally injected CSS.

## 7. Revision request — copy, fill in, and send

Copy this checklist into a message or GitHub issue. Fields marked **Required** are the minimum needed to make a safe change.

- **[Required] Current theme version / CSS file:**
- **[Required] What exactly should change?** (sidebar background / hover / active / text / font / other)
- **[Required] Where does the change apply?** (entire agency / specific client sub-account / unknown)
- **[Required] What is wrong now, or what outcome do you want?**
- **[Required] Exact brand colors or website URL:**
- **[Required] Screenshot of the affected GHL screen:** (redact client data)
- Desired font and source/license, if changing typography:
- Components to leave untouched:
- Browser/device and GHL screen tested:
- Current Custom CSS backup available? (yes/no)
- Approval contact and preferred test/rollout process:

**Example request:** "For Elevate v2.1, change the sidebar background to `#442C52` and active state to `#755087`. Only adjust the sidebar. All client accounts in this agency may be affected. Attached: Dashboard and Settings screenshots. Preserve button styles."

## 8. New client branding intake — copy, fill in, and send

**Required inputs**

1. **Client/business name:**
2. **Client website URL:**
3. **Logo or brand assets:** (link or upload; original files preferred)
4. **Brand colors:** (HEX codes if available; otherwise authorize approximation from the website)
5. **Coverage:** (dedicated agency, shared agency, single sub-account, or unknown)
6. **Target GHL screens/components:** (sidebar only / header / buttons / cards / other)
7. **A screenshot of the current client GHL interface:** (redact private data)
8. **Who can test and approve the change, and how can we roll it back?**

**Optional preferences**

9. Preferred font (name and loading source), or use a readable system font:
10. Light or dark sidebar / light or dark main workspace:
11. Accent color and hover style:
12. Accessibility requirements or client style guide:
13. Specific elements that must **never** change:
14. Timing/version label and GitHub filename preference:

**New-client rule:** A new branding palette is **not automatically safe for a shared agency**. Confirm real CSS scope and supported injection before reuse. Create a distinct file per brand, e.g. `client-name_sidebar_v1.css`, and do not overwrite the Elevate theme.

## 9. Review and release workflow

1. Prepare draft CSS/manual changes outside the production GHL editor.
2. Compare changes against the current GitHub version and review potentially broad selectors.
3. Have the client or account owner review a summary and approve the target scope.
4. Test in a suitable nonproduction account or controlled window when possible.
5. Back up the live CSS, install **one version**, run the checklist, and record results.
6. Commit the approved revision to GitHub with a meaningful description (e.g., `docs: add GHL theme usage manual` or `style: adjust Elevate sidebar contrast`).
7. Keep previous versions and rollback notes.

**Publication note:** This manual was approved for publication as `README.md`. The existing `elevate_safe_sidebar_v2.css` remains unchanged.

## 10. Verification references

- [HighLevel: Agency Company Settings](https://help.gohighlevel.com/support/solutions/articles/48000982604-an-inside-look-at-agency-company-settings-what-you-need-to-know) — settings path, Custom CSS guidance, platform caveats.
- [HighLevel: Agency Settings custom CSS example](https://help.gohighlevel.com/support/solutions/articles/48001065654-hide-the-smtp-setup-help-doc-link) — raw CSS example and agency-level reach.
- [WCAG 2.2 contrast minimum](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html) — text contrast guidance.
- [GHL CSS in this repository](https://github.com/mgbdomingo/ghl-theme-temp/blob/main/elevate_safe_sidebar_v2.css) — exact selectors and tokens covered here.