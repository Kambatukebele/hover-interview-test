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
