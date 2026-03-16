# Repository Structure Audit — IKIRA Affiliate Assistant

## Top-Level Structure

- `/components` — reusable UI and feature components.
- `/components/admin` — admin dashboard module components (affiliate hub, feeds, shortlinks, payouts, branding).
- `/components/layout` — global shell components (header, footer disclosure, layout wrapper).
- `/components/ui` — base design-system primitives (button, card, input, modal, table, tabs, etc.).
- `/contexts` — React context providers for cross-cutting client state.
- `/data` — static mock datasets used to drive UI behavior.
- `/docs` — requirements/architecture planning documents for target-state platform.
- `/hooks` — shared hooks (e.g., toast interaction helpers).
- `/pages` — route-level page modules.

Additional root configuration/app files:
- `App.tsx`, `index.tsx`, `index.html` — app entry and runtime shell.
- `types.ts` — shared TypeScript domain interfaces.
- `vite.config.ts`, `tsconfig.json`, `package.json` — toolchain/build/config.

---

## Directory Purpose Breakdown

### `/pages`
Contains user-facing and admin-facing route handlers as React components:
- commerce discovery and decision flows (`HomePage`, `QuizPage`, `BundlesPage`, `ComparePage`, `ProductPage`)
- content/community discovery (`StoriesPage`, `StorefrontsPage`, `StorefrontDetailPage`)
- operational/admin view (`AdminPage`)
- redirect simulation page (`GoRedirectPage`)

### `/components`
Implements composable, reusable front-end building blocks:
- Product presentation (`ProductCard`, `CouponBadge`, `DealDnaChip`, `PriceSparkline`)
- visual assets and icon wrappers (`icons.tsx`)
- submodules grouped by concern (`admin`, `layout`, `ui`)

### `/contexts`
Implements app-wide state domains:
- theme toggling and persistence,
- compare-list state and constraints,
- toast notifications.

### `/data`
Holds mock domain objects:
- products,
- stories,
- storefronts,
- affiliate programs,
- feed records,
- shortlinks.

### `/docs`
Contains conceptual architecture/requirements artifacts. These documents describe planned backend/platform capabilities and are useful for roadmap context, but they are not direct evidence of implementation.

---

## Module Organization Pattern

The codebase follows a **feature + layer hybrid** organization:
- Route-level features live under `/pages`.
- Shared concerns are extracted into layered folders (`components`, `contexts`, `hooks`, `data`).
- UI primitives are separated from feature-specific components via `/components/ui`.
- Admin functionality is isolated in `/components/admin` and mounted through the admin page.

This structure is appropriate for a frontend prototype and can evolve into a larger monorepo/service architecture by introducing backend packages or separate services later.
