# Agents Guide - Benji Documentation

This document provides AI agents with comprehensive context about the Benji documentation site, its architecture, and key patterns.

## Project Overview

**Benji Docs** is a documentation site built with [Mintlify](https://mintlify.com/). It contains documentation for the Benji platform, including Pilot (admin dashboard), Benji Connect (member connection), integrations, and API reference.

### Tech Stack

| Technology | Purpose |
| ---------- | ------- |
| Mintlify   | Documentation framework |
| MDX        | Content format (Markdown + JSX components) |

## Directory Structure

```
docs/
├── docs.json              # Main configuration and navigation
├── pilot/                 # Platform/Pilot documentation
├── connect/               # Benji Connect documentation
│   ├── hosted/            # Hosted Connect pages
│   └── *.mdx              # SDK pages
├── integrations/          # Integration guides (Square, etc.)
├── api-reference/         # API documentation
│   ├── endpoint/          # API endpoint docs
│   └── webhooks/          # Webhook documentation
├── images/                # Static images
│   ├── connect/           # Connect-related images
│   └── pilot/             # Pilot-related images
├── logo/                  # Logo assets
└── snippets/              # Reusable MDX snippets
```

## Key Files

| File | Purpose |
| ---- | ------- |
| `docs.json` | Main configuration: navigation, theme, colors, API settings |
| `*.mdx` | Documentation pages in MDX format |

## Navigation Structure

The documentation is organized into tabs defined in `docs.json`:

| Tab | Content |
| --- | ------- |
| **Platform** | Pilot dashboard documentation |
| **Benji Connect** | Hosted Connect and SDK integration guides |
| **Benji Integrations** | Third-party integration guides (Square) |
| **API Reference** | API endpoints, authentication, webhooks |

## MDX Page Format

Every MDX page starts with frontmatter:

```mdx
---
title: "Page Title"
description: "Brief description for SEO and previews."
sidebarTitle: "Sidebar Label"
---

## Content starts here
```

### Common Mintlify Components

```mdx
<Tip>
  Helpful tip content
</Tip>

<Warning>
  Warning content
</Warning>

<Card title="Card Title" icon="icon-name" href="/path/to/page">
  Card description
</Card>

<CardGroup cols={2}>
  <Card>...</Card>
  <Card>...</Card>
</CardGroup>
```

### Tables

Use standard Markdown tables:

```markdown
| Column 1 | Column 2 |
| -------- | -------- |
| Value 1  | Value 2  |
```

### Images

Reference images from the `/images` directory:

```mdx
![Alt text](/images/folder/image.png)
```

## Adding New Pages

1. Create the `.mdx` file in the appropriate directory
2. Add frontmatter with title, description, and sidebarTitle
3. Add the page path to `docs.json` in the correct navigation group

### Example: Adding a new page to Benji Connect

1. Create `connect/new-page.mdx`
2. Add to `docs.json`:
```json
{
  "group": "Benji Connect SDK",
  "pages": [
    "connect/introduction",
    "connect/new-page"  // Add here
  ]
}
```

## Modifying Navigation

All navigation is controlled in `docs.json` under the `navigation.tabs` array. Each tab contains groups, and each group contains pages.

```json
{
  "tab": "Tab Name",
  "groups": [
    {
      "group": "Group Name",
      "pages": [
        "path/to/page"
      ]
    }
  ]
}
```

## Content Guidelines

- Use bullet points (not numbered lists) unless order matters
- Keep descriptions concise
- Use `<Tip>` for helpful information
- Use `<Warning>` for important cautions
- Use `<Card>` components for linking to related pages
- Include comparison tables when explaining alternatives

## Git Workflow

- Always verify the current branch before making changes
- Create descriptive branch names related to the documentation changes
- Commit messages should describe the documentation changes made
