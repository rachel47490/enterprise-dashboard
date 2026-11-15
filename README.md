# Responsive Enterprise Dashboard Layout System

A responsive "Admin Control Panel" layout for a fintech client, built with semantic HTML and CSS only (no JavaScript, no frameworks).

## Files
- `index.html`: semantic page structure
- `styles.css`: tokens, reset, layout and responsive rules, with comments justifying each choice

## How to run
Download or clone the repo and open `index.html` in a browser.

## Layout approach
- **CSS Grid** builds the page shell (sidebar, header, main, footer) with named areas, because the page layout is two-dimensional.
- **Flexbox** handles the one-dimensional parts: the nav list, the header and footer rows, and the card contents.
- **Metric cards** use `repeat(auto-fit, minmax(min(14rem, 100%), 1fr))`, so the column count adapts without breakpoints.
- **One breakpoint (`48em`)** turns the sidebar into a swipeable top nav on small screens.

## Key technical decisions
- Semantic landmarks: `header`, `nav`, `main`, `footer`, with a logical heading order.
- Custom properties for all colours and spacing, so there are no magic numbers.
- `box-sizing: border-box` for predictable sizing.
- `100dvh` instead of `100vh`, to avoid the mobile address-bar jump.
- `minmax(0, 1fr)` on the content column, so wide content can't break the layout.
- System font stack and no images, for fast loading.
- `clamp()` for fluid text and `rem`/`em` units, so the page respects user font settings.

## Accessibility
- Labelled navigation landmark (`aria-label="Primary"`).
- Visible `:focus-visible` outlines with enough contrast on light and dark areas.
- Trend arrows (▲/▼) back up the red and green colours.
- Reduced-motion support.

## Edge cases handled
- 320px screens, with no card overflow.
- Ultra-wide screens, with a max width on the card grid.
- Long values, which wrap inside cards.
- Print, which hides the sidebar.

## Trade-off
`auto-fit` doesn't fix the number of columns. If the client needs exactly four columns on desktop, switch to `repeat(4, 1fr)` and add one breakpoint.