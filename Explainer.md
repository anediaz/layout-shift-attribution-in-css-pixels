# Explainer: Layout Instability Attribution in Physical Pixels

## Overview

The Layout Instability API, accessed via `PerformanceObserver` entries of type `"layout-shift"`, currently reports attribution data (`prevRect` and `currentRect`) in **device pixels**. These values depend on the resolution of the device on which shift was captured, specifically on its `devicePixelRatio`. However, other Web APIs, such as `getBoundingClientRect()`, report values in **CSS pixels**, making the Layout Instability API inconsistent by comparison. This mismatch makes it harder to visualize layout shifts accurately or to combine this data with other metrics in a unified coordinate space.

## Motivation

- **Consistency:**  Attribution data should follow the same coordinate convention as other Web Performance APIs, which typically use CSS pixels for layout-related measurements. For example, `getBoundingClientRect()` reports positions in CSS pixels.
- **Accuracy:** Device or physical pixel values vary with `devicePixelRatio` and screen resolution, making attribution inconsistent across devices.
- **Clarity:** Representing layout shifts in CSS pixel space aligns better with how developers reason about layout and visual changes.

## Use Cases

- Web performance tools measuring layout shift origins (e.g., Core Web Vitals).
- Visual regression tools that overlay shift attribution.
- Analytics platforms reporting layout instability irrespective of screen DPI.

## Proposed Solution

Report attribution rectangles in **CSS pixels**:

```javascript
{
  prevRect: { x: number, y: number, width: number, height: number },
  currentRect: { ... },
  // previously device-pixel-based values, now CSS pixels
}
