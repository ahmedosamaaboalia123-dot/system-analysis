# Codex instructions — RIHLA Design System V3.2

> هذه التعليمات ملزمة لأي وكيل برمجي يعمل على تطبيق الهوية داخل المشروع. لا تستبدلها باجتهادات شكلية.

## 0. Scope and precedence

- Scope: **Approved UI/UX design system implementation**. For the standalone Trips prototype, business behavior is governed by `modules/trips/User_Story.txt`, its original requirements, and `modules/trips/Codex_Instructions.txt`; never infer production backend rules.
- Ground truth for **appearance and interaction**: `reference/RIHLA_Design_System_V3_2_REFERENCE.html` + `docs/01_DESIGN_DECISIONS.md` + `docs/02_COMPONENTS_AND_BEHAVIOR.md`.
- Ground truth for **brand tokens**: `tokens/rihla-tokens.json` / `.css`.
- Existing repository architecture, security rules and business requirements remain authoritative for non-UI choices.
- If sources conflict or a detail is not specified, **report the conflict, do not invent a product requirement**.

## 1. Strict rules (must not violate)

1. DO NOT replace the approved V3.2 layout with a different reference style, font, color scheme, or a new design direction.
2. DO NOT use "ERP" in the primary brand name: display «رحلة». A descriptive subtitle «نظام إدارة شركات الحج والعمرة» is allowed where appropriate.
3. DO NOT introduce gold as a brand color. Semantic warning amber is allowed **only for warning/status messaging**, not branding.
4. Use **Almarai** for Arabic UI. Available font weights: `300`, `400`, `700`, `800`. Don't assume a native 500/600 Almarai weight.
5. All end-user UI defaults to **Arabic RTL**. Preserve readable LTR behavior for reference codes, dates where needed, and technical identifiers.
6. Sidebar starts **collapsed/icon-only on desktop**. Clicking a module icon navigates/selects its screen **without expanding** the Sidebar. Only the explicit toggle controls expansion.
7. The sidebar toggle must be placed **inside the Sidebar at its top**; expanded mode reveals names and nested groups.
8. Expanded Sidebar group indicators use compact, rotating chevrons. Clicking empty sidebar space closes an expanded group; clicking a child item navigates normally.
9. **Header and Sidebar remain fixed**. Scrolling occurs **inside Main Workspace only**. Do not let changing views remove the Header.
10. Workspace upper corners have **22px radius at scrollTop≈0**, then **0px radius when workspace scrollTop>2px**; restore when returned to top. Mobile reference uses 16px. Respect reduced motion.
11. Unified shell uses `--app-shell: #E4E9E6`; Workspace surface remains white with a clear visual boundary. Header matches V3.2 reference geometry and search presentation.
12. Keep approved semantic Alert pattern: lightly tinted backgrounds, distinct **right-hand** colored strip, appropriate accessible contrast. No oversized circular icons.
13. Style checkboxes/radios with brand color rather than browser blue. Focus must remain visible.
14. Distinguish main **navigation tabs** (persistent selected state) from **action buttons** (no permanent selected state). Hover must revert when pointer leaves.
15. Inputs show inline invalid indicator **inside input** plus explanatory message below. Use designed custom dropdowns and calendar visuals, not the browser's default blue option list/date popup.
16. Current logo and sidebar icons are **replaceable assets**, not final requirements. Provide swappable logo and icon mapping components; never hardcode demo icons as module semantics.
17. Do not attach real business actions to showcase controls without the related module specification and backend contract.
18. Maintain keyboard accessibility, semantic HTML, focus management and `aria-expanded`/`aria-current` states for navigation and overlays.
19. Avoid giant copy-pasted markup or stacked `!important` overrides from the reference. For this Trips prototype, maintain a self-contained `code/index.html` with organized reusable CSS/JS sections; no framework or build step. This does not require typed framework components.
20. Never claim a feature is implemented or tested until relevant checks actually run. Report unverified items explicitly.

## 2. Required workflow

**Phase A — Inspect**: Identify project stack, current UI structure, routes, shared components, icons, accessibility and available test tools. Do not modify files yet.

**Phase B — Plan**: List affected files and components, behavioral invariants, test cases and migration approach. For the specific Trips prototype, record a concise plan in Module_Report and **continue directly to implementation without waiting for approval between phases**. Keep design invariants separate from business rules.

**Phase C — Tokens**: Integrate palette, semantic colors, font, spacing and corner tokens in one place.

**Phase D — Shell**: Implement fixed Sidebar, fixed Header, independently scrolling Workspace; verify both collapsed/expanded states and geometry.

**Phase E — Components**: Implement reusable tabs, action buttons, inputs, dropdowns, calendar, tables/filters, alerts, modals, step forms, file-upload patterns and checkboxes/radios.

**Phase F — Integration**: Replace placeholder logo/icons with replaceable props/registry; bind real routes only after inspecting project modules.

**Phase G — QA**: Verify each item in `checklists/ACCEPTANCE_TESTS.md`; test real navigation, scroll, radius, Arabic layout, keyboard and small windows.

**Phase H — Delivery**: Provide file-by-file change log, screenshots/test report if possible, passed/failed checks and remaining risks. Seek approval before any new visual direction.

## 3. Stop conditions

For the **Trips standalone HTML prototype only**, the stack and route scope are already established: HTML/CSS/Vanilla JS and in-module navigation. **Do not stop for an approval gate after planning**. Stop only if mandatory reference files are inaccessible, required authorization is missing, or an action would be irreversible/impact actual backend data. On unresolved business rules, keep a clearly labeled demo-only simulation or show BLOCKED; do not invent production rules. This exception does not authorize changes to the approved design, other modules, main branch, or live systems.
