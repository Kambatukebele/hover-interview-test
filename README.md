# Shopify Theme Development Notes

## Theme Setup

I’m developing a custom Shopify theme based on the **Dawn** starter theme.

To begin, I pulled the theme from my store using:

```bash
shopify theme dev --store hover-interview
```

This command starts a local development server and connects it to the specified store.

---

## Development Commands

### Start the development server

```bash
shopify theme dev
```

### Push local changes to the store

```bash
shopify theme push
```

### Pull the latest changes from the store

```bash
shopify theme pull
```

---

## Working with Multiple Stores

Since I’m managing multiple Shopify stores, I created a configuration file called **`shopify.theme.toml`** to handle different environments.

In it, I defined an environment flag called **`hover`** for my current store:

```toml
[environments.hover]
store = "hover-interview"
```

This helps ensure I don’t accidentally push or pull to the wrong store.

---

## Environment-Specific Commands

When using the environment flag, I can run these commands safely for the correct store:

### Start development server

```bash
shopify theme dev -e hover
```

### Pull theme changes

```bash
shopify theme pull -e hover
```

### Push theme changes

```bash
shopify theme push -e hover
```

---

## Additional Files

- **`README.md`** → Documenting development steps and workflow.
- **`shopify.theme.toml`** → Defines store environments and configuration.

---

## Summary

| Task                | Command                       |
| ------------------- | ----------------------------- |
| Start dev server    | `shopify theme dev -e hover`  |
| Pull latest changes | `shopify theme pull -e hover` |
| Push updates        | `shopify theme push -e hover` |

---

## Custom Snippets

During theme development, I created two reusable snippets to improve modularity and reusability across sections.

### 1. `product-action-card`

This snippet is responsible for displaying a product action layout (e.g., subscription cards, pricing options).

**Accepted variables:**

- `title`
- `isSales`
- `sales`
- `number`
- `price`
- `background_color`
- `backgroundColorTitle`
- `variables`

These parameters allow flexible control of layout appearance and behavior directly through Liquid or section settings.

### 2. `accordion-card`

This snippet renders a collapsible accordion block with smooth toggle behavior.

**Accepted variables:**

- `title`
- `description`
- `active`

This makes it simple to reuse across different content sections while maintaining consistent interaction styles.

---

## Accordion Section

I created a custom section named **Accordion** that renders multiple `accordion-card` blocks dynamically.

**Configuration details:**

- The section includes up to **5 blocks** (`limit = 5`).
- Each block corresponds to one `accordion-card`.
- The section is disabled for the **header** and **footer** using the `disable_on` key.
- A **custom main product** section was also created with a **limit of 1** to ensure only one instance is available per page.

---

## Section Settings

Within the custom main product section, I added several settings to improve flexibility and design customization.  
Each setting can be modified through the Shopify theme editor.

| Setting Type     | ID                     | Default / Example Value | Description                                             |
| ---------------- | ---------------------- | ----------------------- | ------------------------------------------------------- |
| `range`          | `product_paddingY`     | `45`                    | Controls vertical padding for the product section       |
| `select`         | `is_sticky_text`       | `"sticky"`              | Defines text block position behavior (sticky or normal) |
| `range`          | `product_card_radius`  | `30`                    | Controls border radius of product cards                 |
| `text_alignment` | `bottom_btn_text`      | `"center"`              | Aligns button text at the bottom                        |
| `range`          | `offer_radius`         | `15`                    | Controls border radius for offer cards                  |
| `color`          | `bg_btn`               | `#171714`               | Sets button background color                            |
| `color`          | `text_color_btn`       | `#ffffff`               | Sets button text color                                  |
| `color`          | `hover_bg_btn`         | `#e2f2f3`               | Sets button hover background color                      |
| `color`          | `hover_text_color_btn` | `#171714`               | Sets button hover text color                            |
| `range`          | `btn_radius`           | `100`                   | Defines the button border radius                        |

---

## Summary of Customization Features

- Modular snippets for product and accordion UI components
- Configurable section settings with live customization
- Accordion section with up to 5 collapsible blocks
- Section visibility disabled on header and footer
- Single-instance main product section for product detail pages

---

## Next Steps
