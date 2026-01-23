# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

ALMUÑÉCAR 38 is a luxury real estate marketing landing page for 38 exclusive private residences on Spain's Costa Tropical. The site captures leads (name, email, phone) and submits them to Google Sheets.

## Architecture

**Single-file static site** - All HTML, CSS, and JavaScript are contained in `index.html`. No build system, no dependencies, no frameworks.

### Key Sections in index.html

- **Lines 1-32**: Meta tags, Open Graph, Google Fonts (Cormorant Garamond, Inter)
- **Lines 34-491**: CSS with custom properties, glassmorphism effects, ambient animations (vignette, fog, grain, floating words)
- **Lines 612-982**: JavaScript for multi-language system, form handling, Google Sheets integration

### CSS Custom Properties

```css
--bg: #0b0b0c       /* Dark background */
--text: #e9e7e2     /* Cream text */
--gold: #c9a76a     /* Accent color */
```

## Multi-Language System

5 languages supported: German (de, default), English (en), Spanish (es), Swedish (sv), Finnish (fi)

Content structure in `content` object (line 632):
- UI element translations
- 6 rotating headlines per language (cycles every 8.5s)
- Background floating words
- All form/modal/cookie texts

Language preference persisted in localStorage.

## Lead Capture Flow

1. User clicks CTA → form expands with animation
2. Form collects: name (required), email (required), phone (optional)
3. Data POSTed to Google Apps Script webhook (line 879)
4. Success modal displayed on completion

**Google Script URL constant**: `GOOGLE_SCRIPT_URL` (line 879)

## Development Workflow

No build commands - edit `index.html` directly and deploy. Static file hosting only.

## Google Sheets Integration Setup

If you need to change the Google Script:
1. Create Google Sheet → Extensions → Apps Script
2. Deploy as Web App (Execute as: Me, Access: Anyone)
3. Update `GOOGLE_SCRIPT_URL` constant with new deployment URL
