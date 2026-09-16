# Kumo Styling Conventions & Token System

Cloudflare Kumo uses **Tailwind CSS v4** coupled with a strict semantic token architecture.

---

## 1. Absolute Rule: Semantic Tokens Only

Components in Kumo must exclusively use semantic theme classes. Raw color values break theming and fail Oxlint rules.

| Element | Allowed Semantic Tokens | FORBIDDEN (Fails Lint) |
| :--- | :--- | :--- |
| **Backgrounds** | `bg-kumo-base`, `bg-kumo-elevated`, `bg-kumo-recessed`, `bg-kumo-brand`, `bg-kumo-danger` | `bg-blue-500`, `bg-gray-100`, `bg-slate-800` |
| **Text** | `text-kumo-default`, `text-kumo-subtle`, `text-kumo-muted`, `text-kumo-brand` | `text-gray-900`, `text-black`, `text-zinc-600` |
| **Borders** | `border-kumo-line`, `border-kumo-hairline`, `border-kumo-focus` | `border-gray-200`, `border-neutral-300` |
| **Rings** | `ring-kumo-hairline`, `ring-kumo-focus` | `ring-blue-400` |

### Exceptions
Only pure monochrome neutrals are allowed for specific contrast needs:
* `bg-white`, `bg-black`, `text-white`, `text-black`, `transparent`

---

## 2. No `dark:` Variant Prefix

* **Automatic Dark Mode**: Dark mode in Kumo is handled automatically via CSS custom properties using native `light-dark()` functions in `packages/kumo/src/styles/theme-kumo.css`.
* **Never use `dark:` in utility classes**:
  ```tsx
  // WRONG
  <div className="bg-white dark:bg-black text-gray-900 dark:text-gray-100" />

  // CORRECT
  <div className="bg-kumo-base text-kumo-default" />
  ```
* Mode/theme attributes are attached at a parent level:
  `data-mode="light"|"dark"` and optional `data-theme="fedramp"`.

---

## 3. Surface Hierarchy

When layering UI elements, adhere to the standard surface depth progression:

1. **`bg-kumo-base`**: Canvas/page background.
2. **`bg-kumo-elevated`**: Cards, modals, dropdowns, and popovers sitting above the base.
3. **`bg-kumo-recessed`**: Inset wells, code blocks, or nested secondary areas.

---

## 4. Class Composition with `cn()`

Always compose and merge class names using the project `cn()` utility:

```tsx
import { cn } from "../../lib/utils"; // or standard export

export const Card = ({ className, elevated, ...props }) => (
  <div
    className={cn(
      "bg-kumo-base border border-kumo-line rounded-md p-4",
      elevated && "bg-kumo-elevated shadow-sm",
      className
    )}
    {...props}
  />
);
```
