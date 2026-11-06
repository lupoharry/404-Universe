## Testing and Quality Assurance (QA)

- **Visual verification:** Treat the page as a browser-rendered visual experience. After making changes, open `index.html` in a browser and verify the actual rendered output. Do not rely on code inspection alone.

- **Test infrastructure:** There is currently no test runner or build setup. Do not invent test commands, assume testing frameworks are available, or claim automated test coverage. If new test infrastructure is introduced, document the setup and use the actual commands it provides.

- **Smoke testing:** Verify the following after each relevant change:
  - Initial page load and rendering.
  - Animation behavior, including start-up and continuous playback.
  - Pointer interactions, including pointer movement and pointer exit.
  - Responsive behavior when resizing the browser window.
  - Both narrow and wide viewport layouts.
  - Heading visibility, positioning, and readability over the canvas.

- **Browser compatibility and rendering:** Check the browser console for JavaScript errors, warnings, and runtime issues. Verify that the canvas renders correctly at different device-pixel ratios (DPR), without noticeable blurring, distortion, layout shifts, or unwanted scrollbars.

- **Accessibility and input:** For changes affecting accessibility or user interaction, ensure that all essential semantic content remains available independently of the decorative canvas. Verify relevant keyboard navigation, touch interactions, focus behavior, and assistive-technology compatibility.

- **Verification reporting:** Summarize the checks performed after completing changes. Clearly distinguish between manual visual verification, browser-based smoke tests, and automated tests. Explicitly identify anything that could not be tested or remains unverified.

- **Quality standard:** Do not consider a change complete until the affected functionality has been reviewed in the browser and any discovered regressions have been addressed.