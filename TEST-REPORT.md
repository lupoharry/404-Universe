# 404 Universe test report

**Execution date:** 2026-11-06  
**Scope:** [test cases](TEST-CASES.md) for the page, Oneko, hearts and SEO  
**Environment:** Windows, VS Code integrated browser (Electron 43.8.3,
Chromium 150.0.7871.250), local `file:` URL. The page was hidden during the
execution; animation frames did not advance normally.  
**Approach:** BDD-style acceptance and regression scenarios. Browser-driven
scripts inspected the DOM, dispatched pointer events, loaded images and
observed timer events. Cat and particle frame logic was also driven directly
to compensate for the hidden page. This is not a TDD run or a substitute for
testing live animations on a visible page.

## Results

| ID | Result | Evidence |
|---|---|---|
| TC-01 | Pass | Heading and document title were present; the initial cat GIF loaded. |
| TC-02 | Pass | At 1078 x 818, canvas ended at y=572.59 and the white zone started there, matching the 70/30 split. |
| TC-03 | Pass | At all four listed viewport sizes, measured heading bounds stayed within the canvas and document scroll dimensions matched the viewport, subject to subpixel rounding. No visual screenshot inspection was performed in this run. |
| TC-04 | Pass | A synthetic pointer at (300, 200) mapped to approximately (300, 200); entering the cat zone cleared it. In one controlled frame, a nearby particle moved 2.61 px horizontally away versus 0.02 px for a distant particle. Continuous visual tracking was not checked. |
| TC-05 | Pass | With synthetic pointer input and direct cat ticks, the cat showed `32.GIF`, moved right by 24 px with `6.GIF`, and eventually sat at x=884 near the x=900 target. |
| TC-06 | Pass | With controlled random values and direct ticks, the idle cat entered wash (`26.GIF`), sleepy (`27.GIF`) and sleep (`29.GIF`) states. Real-time transitions were not observed. |
| TC-07 | Fail | After 50 direct digging ticks, the cat entered idle/sleep; the next tick restarted digging instead of displaying sleep. See F-01. |
| TC-08 | Pass | All 32 GIFs loaded in the browser; each reported intrinsic dimensions of 32 x 32. |
| TC-09 | Pass | Two successive heart class triggers were observed at approximately 5,152 ms and 10,141 ms after observation began, 4,989 ms apart. This verifies triggering, not visible animation. |
| TC-10 | Fail | With the cat at the top boundary, the heart's entire measured rectangle was above the zone's clipping boundary. See F-02. |
| TC-11 | Fail | With reduced motion emulated, the heart animation duration was 0.01 ms and its opacity was 0, making it effectively imperceptible. See F-03. |
| TC-12 | Not run | Keyboard and assistive-technology testing were not performed. |
| TC-13 | Not run | Touch input was not tested. |
| TC-14 | Pass | Title, description and robots metadata were present; JSON-LD parsed as a Person with the requested names and expertise. Social tags were inspected in the source, not validated by a social platform. |
| TC-15 | Fail | No `.tagline` element or visible profile text was present in the page body. See F-04. |
| TC-16 | Pass | No page exceptions or console errors were observed on initial reload. This does not cover every later interaction. |
| TC-17 | Not run | Only the integrated Chromium-based browser was used. |
| TC-18 | Not run | No deployed URL or server configuration was tested. |
| TC-19 | Not run | The complete direction and edge matrix was not exercised. |
| TC-20 | Not run | The browser reported the page as hidden, so live animation, visual smoothness and performance could not be assessed reliably. |

**Summary:** 20 cases: 10 passed, 4 failed, 6 not run. A pass applies only to
the evidence and environment described above.

## Findings

### F-01: Digging restarts instead of transitioning to sleep

- **Impact:** Oneko does not settle after the pointer leaves the page.
- **Reproduce:** Move the pointer onto the page, move it outside, and keep it
  outside for over five seconds. For a deterministic logic check, dispatch a
  pointer move and `pointerleave`, then call `catTick()` 51 times in the
  developer console.
- **Observed:** Tick 50 sets `catState` to `idle` and `idleAction` to `sleep`;
  tick 51 sets `catState` back to `digging`.
- **Expected:** The cat should remain asleep after the digging period until
  the pointer returns or another intended wake-up event occurs.
- **Location:** `catTick()` in [index.html](index.html).

### F-02: Heart is clipped at the top of the cat zone

- **Impact:** The periodic heart can be invisible when the cat is near the top
  boundary of its area.
- **Reproduce:** Place the cat at the upper boundary, trigger a heart, and
  compare its bounding rectangle with the zone boundary.
- **Observed:** In a controlled position check, the heart rectangle was
  entirely above the white zone, whose `overflow` is `hidden`.
- **Expected:** The heart should be visible above the cat throughout its
  allowed movement area.
- **Location:** `.oneko-zone` and `.heart` styles in [index.html](index.html).

### F-03: Reduced-motion heart is effectively invisible

- **Impact:** Users requesting reduced motion cannot meaningfully see the
  periodic heart.
- **Reproduce:** Emulate `prefers-reduced-motion: reduce` and trigger the
  heart; inspect the animation duration and opacity.
- **Observed:** The animation lasts 0.01 ms and ends at opacity 0.
- **Expected:** Show a perceptible static or minimally animated heart for a
  reasonable duration.
- **Location:** Reduced-motion styles in [index.html](index.html).

### F-04: Profile tagline is absent

- **Impact:** The requested profile and expertise terms appear in metadata but
  not as visible page content. A prior completion message described a visible
  tagline, but this execution found none.
- **Reproduce:** Reload the page and inspect the body or search for
  `.tagline`.
- **Observed:** The stylesheet defines `.tagline`, but there is no corresponding
  element in the body.
- **Expected:** The previously described profile tagline is visible without
  obscuring the heading or the cat area.
- **Location:** Body markup in [index.html](index.html).

## Execution notes and limitations

- No application test runner, automated test suite or CI configuration was
  introduced. The cases above are reusable manual acceptance cases; the
  browser-driven checks were executed through the integrated Playwright tool,
  not through a repository command or a persistent automated suite.
- A first asynchronous chase attempt timed out because the shared page was
  hidden and its animation loop did not advance. The subsequent direct-tick
  checks are narrower logic checks; they do not prove real-time rendering.
- Local-file checks cannot establish HTTP status, actual indexing, canonical
  behavior or social preview rendering. Search engines generally do not index
  a page served with an HTTP 404 status.
- No CI run, cross-browser run, touch test, assistive-technology audit,
  performance benchmark or full security assessment was performed.
- The application was not modified as part of this test-report task.
