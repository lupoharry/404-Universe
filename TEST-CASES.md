# 404 Universe test cases

These acceptance and regression cases describe the expected behavior of the
standalone page. Open `index.html` in a browser with developer tools available.
Each case starts with a fresh page reload unless stated otherwise. The
[test report](TEST-REPORT.md) records one execution, including cases that were
not run.

## Page and layout

| ID | Scenario and steps | Expected result |
|---|---|---|
| TC-01 | Load the page. | The title is "404 Universe", the heading is visible, and the initial cat image loads. |
| TC-02 | At a 1078 x 818 viewport, inspect the canvas and cat area. | The canvas occupies the top 70%; a white cat area occupies the bottom 30%, with no gap or overlap. |
| TC-03 | Inspect 320 x 568, 375 x 667, 1920 x 1080 and 320 x 240 viewports. | The heading remains within the canvas area, the 70/30 split is preserved, and content does not cause viewport overflow. |
| TC-04 | Move the pointer to (300, 200) inside the canvas, then into the cat area. | The particle interaction is centered at the pointer; on leaving the canvas, the particle pointer is cleared. A particle near the pointer moves away more than a distant particle. |
| TC-05 | Move the pointer far to the right of an idle cat and wait for it to catch up. | The cat briefly shows a surprised sprite, moves toward the pointer with a walking sprite, then sits near the target. |
| TC-06 | Leave an idle cat undisturbed. Repeat or control randomness to exercise washing and sleeping. | The cat can wash, become sleepy and show sleep sprites. |
| TC-07 | Move the pointer, then move it out of the page and wait at least six seconds. | The cat digs for about five seconds, then stops digging and transitions to sleep while the pointer remains outside. |
| TC-08 | Load each image from `gif/1.GIF` through `gif/32.GIF`. | All 32 images load successfully. |

## Heart and accessibility

| ID | Scenario and steps | Expected result |
|---|---|---|
| TC-09 | Reload and observe two successive heart animation triggers. | The heart is triggered repeatedly at approximately five-second intervals. |
| TC-10 | Move the cat to the top edge of its area and wait for a heart. | The heart above the cat remains visible instead of being clipped by the cat area. |
| TC-11 | Enable the operating system or browser reduced-motion preference and wait for a heart. | The heart remains perceptible without requiring the normal moving animation. |
| TC-12 | Navigate with a keyboard and inspect the accessibility tree using assistive technology. | The heading and meaningful page content are available, and decorative animation does not trap focus. |
| TC-13 | Use a touch device or touch emulation to interact with the particle area and cat area. | Touch input does not break the page; supported pointer behavior remains usable. |

## SEO and runtime

| ID | Scenario and steps | Expected result |
|---|---|---|
| TC-14 | Inspect the document title, description, robots metadata, social metadata and JSON-LD. Parse the JSON-LD. | The title and description identify Harald Koehler and the QA focus; indexing is allowed by the robots meta tag; the Person data parses and includes the requested names and expertise. |
| TC-15 | Inspect the visible page content for the profile tagline. | The page visibly identifies Harald "Harry" Koehler, lupoharry, quality assurance, test management, team leadership and global teams. |
| TC-16 | Reload with the browser console open and inspect runtime and console errors. | No JavaScript exceptions or console errors occur on initial load. |
| TC-17 | Test the page in current Chrome, Firefox and Safari, including different device-pixel ratios. | The page renders and behaves consistently in each supported browser. |
| TC-18 | Test the deployed page's HTTP status, canonical URL, robots rules, sitemap and search engine indexing. | The intended indexable page returns an appropriate successful status and is discoverable; the deployed SEO configuration is consistent with the site's intent. |
| TC-19 | Exercise walking in all eight directions and digging at each edge. | The appropriate directional animations play, and the cat stays within its area. |
| TC-20 | Observe an active, visible page and test prolonged use, resizing and animation performance. | The particle field, cat and hearts animate smoothly, resize correctly and remain responsive without accumulating errors. |

TC-18 requires a deployed URL and server configuration. Cross-browser,
assistive-technology and performance expectations should be refined against the
project's supported-device matrix and measurable performance targets.
