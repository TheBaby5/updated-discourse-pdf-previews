# Discourse PDF Previews (Updated)

> Forked from [discourse/discourse-pdf-previews](https://github.com/discourse/discourse-pdf-previews)

## What It Does

Displays PDF attachments as inline previews in posts instead of plain download links.

## Features

- **Inline Mode**: Embeds PDF in an iframe directly in the post
- **New Tab Mode**: Adds icon, opens PDF in new tab on click
- **Mobile**: Automatically disabled on mobile devices
- **Per-file override**: Start filename with space to force "New Tab" mode

## Settings

| Setting | Options | Default |
|---------|---------|---------|
| `preview_mode` | Inline / New Tab | Inline |

## Changes from Original

- **FIX**: Moved `site.mobileView` check inside `decorateCookedElement` callback
- Fixes Discourse 3.5+ deprecation warning about static viewport initialization
- Clean console output (no deprecation warnings)

## How It Works

```
1. User uploads PDF attachment to post
2. Plugin detects .pdf links in rendered post
3. Fetches PDF as blob (bypasses Content-Disposition: attachment)
4. Either embeds iframe (Inline) or adds click handler (New Tab)
5. Skips processing on mobile devices
```

## Files

```
javascripts/discourse/initializers/initialize-for-pdf-preview.js  # Main logic
common/common.scss                                                  # Styles
settings.yml                                                        # Config
```

## Original Docs

[Inline PDF Previews - Discourse Meta](https://meta.discourse.org/t/inline-pdf-previews/157649)
