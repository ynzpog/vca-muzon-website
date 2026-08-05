# Hero Scroll Indicator Fade Update

## Update summary

The homepage scroll indicator now automatically fades out when the visitor begins scrolling and reappears when the page returns to the top.

## Behavior

- The indicator remains visible while the page is at the top.
- Scrolling away from the top adds the `is-hidden` state.
- The hidden state fades the indicator to transparent and removes pointer interaction.
- `visibility: hidden` prevents the invisible anchor from receiving keyboard focus.
- Returning to the top removes the hidden state and restores the indicator.

## CSS changes

File: `css/vca_style.css`

- Added `visibility` to the existing transition.
- Added `.hero-scroll-indicator.is-hidden` with:
  - `opacity: 0`
  - `visibility: hidden`
  - `pointer-events: none`
  - A delayed visibility change so the opacity transition completes first.

## JavaScript changes

File: `js/vca_js.js`

- Selects `.hero-scroll-indicator` only when it exists.
- Checks whether `window.scrollY` is greater than zero.
- Toggles the `is-hidden` class only when the visibility state changes.
- Uses a passive scroll listener to avoid blocking page scrolling.
- Runs the visibility check on initial page load so restored scroll positions display correctly.

## Validation

- `git diff --check` completed successfully for the CSS and JavaScript changes.
- Node.js is not installed in the current environment, so `node --check` was unavailable.

## Status

- Date: July 13, 2026
- Status: Implemented locally; not yet committed or pushed.
