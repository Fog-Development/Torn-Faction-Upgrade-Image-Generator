# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static single-page application that generates PNG images of Torn faction upgrade data. It's a client-side only HTML/JavaScript application designed for Netlify hosting with no build process.

## Development Commands

This is a static HTML/JavaScript project with no build process. To develop:

- **Local development**: Open `index.html` directly in a browser or use a simple HTTP server
- **Testing**: Manual testing in browser (no automated test suite)
- **Deployment**: Direct upload to static hosting (designed for Netlify)

## Architecture

**Single File Application**: The entire application is contained in `index.html` with embedded CSS and JavaScript.

**Key Components**:
- **API Integration**: Fetches data from Torn API v2 `/faction/upgrades` endpoint using user's API key
- **Canvas Rendering**: Uses HTML5 Canvas API to generate 400px wide images with dynamic height
- **LocalStorage**: Persists user preferences (API key, color settings) across sessions
- **Color Customization**: Background, header, and text colors with transparent background option

**Data Flow**:
1. User provides Torn API key (requires "Minimal" access level)
2. App fetches faction upgrade data focusing on "peace" branch upgrades
3. Upgrades are sorted by category order and rendered on canvas
4. Generated image can be downloaded as PNG

**Upgrade Processing**:
- Categories are sorted by their `order` field
- Each category contains upgrades with `name` and `ability` properties
- Text is wrapped using canvas `measureText()` for proper layout
- Only categories with active upgrades are displayed

## API Requirements

- Uses Torn API v2 with minimal access level API key
- Endpoint: `https://api.torn.com/v2/faction/upgrades`
- Authorization header: `ApiKey ${userApiKey}`
- Focuses specifically on `data.upgrades.peace` branch

## Styling

Uses CSS custom properties for theming with a modern gradient design. All styling is embedded in the HTML file using CSS-in-JS patterns for dynamic color application during canvas rendering.