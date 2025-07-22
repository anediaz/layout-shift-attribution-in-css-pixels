# Layout Shift Attribution in CSS Pixels

This repository contains the explainer and supporting materials for a proposed change to the [Layout Instability API](https://wicg.github.io/layout-instability/), part of the [Web Performance APIs](https://developer.mozilla.org/en-US/docs/Web/API/Performance_API).

## Goal

The goal of this proposal is to improve the usability and consistency of layout shift attribution data by reporting attribution rectangles (`prevRect` and `currentRect`) in **CSS pixels** instead of **device pixels**.

Currently, these rectangles are resolution-dependent and vary based on `devicePixelRatio`, which makes them hard to interpret and combine with other layout data (e.g., `getBoundingClientRect()`). By aligning attribution with CSS pixels, we make layout shift metrics easier to analyze, visualize, and debug across devices.

## Status

This is an early-stage explainer associated with an [Intent to Prototype](https://groups.google.com/a/chromium.org/g/blink-dev/) in the Chromium project. Feedback and discussion are welcome.

## Key Links

- [Explainer](./Explainer.md)
- [Chrome Platform Status entry](https://chromestatus.com/feature/5155103518228480)
- [Chromium issue](https://issues.chromium.org/issues/399058544)
- [Initial implementation CL](https://chromium-review.googlesource.com/c/chromium/src/+/6624567)

## License

This project is licensed under the [W3C Software and Document License](https://www.w3.org/Consortium/Legal/2015/copyright-software-and-document).
