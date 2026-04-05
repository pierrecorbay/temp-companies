# Frontend Contract

This file is filled by the **CTO** when opening the paired build stage. It defines the formal interface between the **Senior Designer** (frontend slice) and the **Product Engineer** (backend slice). The **Product Engineer** does not begin implementation until this contract exists and is agreed.

---

## Feature / Stage

_Name of the feature or pipeline stage this contract covers._

## Shared Review Target

_Branch name or PR URL where both slices will be committed._

---

## Routes and Pages

| Route | Page / Screen | Owner |
|-------|---------------|-------|
| _(e.g. /dashboard)_ | _(e.g. Dashboard Page)_ | Senior Designer |
| _(e.g. /api/data)_ | _(e.g. Data API endpoint)_ | Product Engineer |

---

## Component Interface

List the components the frontend will render and the data contracts the backend must satisfy.

| Component | Props / Inputs | Events / Callbacks | Data Source (API or state) |
|-----------|---------------|-------------------|---------------------------|
| _(e.g. UserCard)_ | `userId: string` | `onSelect(userId)` | `GET /api/users/:id` |

---

## API Endpoints

List all API endpoints the frontend will call.

| Method | Path | Request Shape | Response Shape | Auth Required |
|--------|------|--------------|---------------|---------------|
| GET | `/api/...` | — | `{ ... }` | yes / no |

---

## Visual States

For each interactive or async area, both owner must agree which states exist:

| Area | States Required |
|------|----------------|
| _(e.g. User list)_ | loading, empty, populated, error |
| _(e.g. Submit button)_ | default, hover, focus, loading, disabled, success |

---

## Design Tokens in Use

List any design system tokens or CSS variables this feature introduces or depends on.

| Token | Value | Purpose |
|-------|-------|---------|
| _(e.g. --color-primary-500)_ | _(e.g. #0066CC)_ | _(e.g. CTA buttons)_ |

---

## Breakpoints

| Breakpoint | Layout Behavior |
|------------|----------------|
| Mobile (`< 768px`) | _(describe)_ |
| Tablet (`768px – 1024px`) | _(describe)_ |
| Desktop (`> 1024px`) | _(describe)_ |

---

## State Management Boundary

Describe what state each owner manages and the handoff point:

- **Frontend (Senior Designer)**: _(e.g. UI state, form inputs, optimistic updates)_
- **Backend (Product Engineer)**: _(e.g. persisted data, API responses, auth tokens)_
- **Shared contract**: _(e.g. data shape from API that both sides must agree on)_

---

## Acceptance Bar

What must be true for the CTO to sign off on the frontend slice as complete?

1. _(e.g. All named visual states render correctly at all breakpoints)_
2. _(e.g. Error states display the correct user-facing message)_
3. _(e.g. Loading states do not flash on fast connections)_
4. _(e.g. No design-system token bypasses — all spacing from the token scale)_

---

## Known Risks / Open Questions

| Risk or Question | Owner to Resolve | Deadline |
|-----------------|-----------------|---------|
| _(describe)_ | _(Senior Designer / Product Engineer / CTO)_ | _(before build / before review)_ |

---

_Filled by: CTO_
_Frontend owner: Senior Designer_
_Backend owner: Product Engineer_
_Review target: (see above)_
