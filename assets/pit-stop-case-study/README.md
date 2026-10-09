# PIT STOP case study media

## Final screenshot inventory

The page combines four selected user-provided manual captures with three
previous automated captures. Each image shows one genuine application state;
no sessions were composited and no telemetry or Doc messages were altered.

| Final filename | Original / provenance | Dimensions | What it demonstrates |
| --- | --- | --- | --- |
| `hero.webp` | `Screenshot 2026-10-10 022951.png` | 1567 x 878 | Clear-weather race, lap 13/30, four separated cars, player P1, soft tyres, genuine Doc message |
| `race-progress.webp` | Earlier automated local capture | 1386 x 796 | Lap 4, P1, distance gap behind 11.20, fuel 57%, medium tyre life 67% |
| `strategy-before.webp` | Earlier automated local capture | 1440 x 1296 | Lap 5, P1; hard tyres, refuel and pit service queued in the lap log |
| `strategy-after.webp` | Same automated session as before image | 1440 x 1296 | Lap 6, P4, hard tyres, fuel 97%, tyre life 98% after service and resumed racing |
| `weather-system.webp` | `Screenshot 2026-10-10 024031.png` | 1386 x 796 | Controlled rain test at lap 24; wet tyres, fuel 12%, tyre life 0%, Doc reports DNF |
| `ai-race-engineer.webp` | `Screenshot 2026-10-10 023056.png` | 320 x 273 | Genuine Doc response: “Rain means wet tyres now; pit soon for safety.” in the controlled rain test |
| `canvas-race.webp` | `Screenshot 2026-10-10 023819.png` | 1050 x 500 | Controlled rain test at lap 29, three visibly separated competitors, wet track and rain effects |

The hero is a working clear-weather race session. The weather, Doc, and Canvas
manual images are authentic application output under a manually configured
rain condition, as documented by Joshua. They do **not** establish that
Open-Meteo returned rain. Captions and alt text preserve that distinction.
The player has already DNFed in the lap-24 weather capture; it is not presented
as a healthy wet-tyre strategy. Visible car separation is an observation of
these images, not a guarantee of successful AI requests.

The manual hero contains Doc's “23 laps ahead” wording at lap 13; that text was
preserved as genuine output, not corrected in the image or endorsed as an
accurate remaining-lap calculation. AI advice can contain errors or reflect
an earlier snapshot.

## Processing and presentation

- Hero: entire 1567 x 878 capture, no crop; retains all four competitors,
  telemetry, strategy/pit controls and Doc. High loading priority.
- Weather: crop `(x=260, y=71, width=1386, height=796)` from the 1905 x 901
  original removes background margins and navigation while retaining the
  full circuit, critical telemetry, controls and DNF message.
- Canvas: crop `(6, 6, 1050, 500)` removes surrounding UI edges from the
  focused 1066 x 522 original. The figure extends beyond the text column
  on desktop and scales within the mobile viewport.
- Doc: crop `(17, 10, 320, 273)` removes surrounding panel fragments from
  the 357 x 307 original. A centred inset stays at or below its native width.
- All four processed manual captures use browser Canvas WebP encoding at
  quality 94, with no upscaling, overlays, retouching or generated elements.
- Previous progression and strategy assets remain byte-for-byte unchanged.
  The pit pair stays sequential and full-width for legible telemetry and logs.
- Seven purposeful images cover six technical placements; only one cropped
  Doc panel is shown. All below-hero images have lazy loading and explicit
  dimensions. Every image has descriptive alt text and a figure caption.

The existing portfolio styling remains intact. Only two scoped CSS rules were
added for the native-size Doc inset and wider circuit figure. A scoped static
header override prevents the shared desktop sticky-header rule from covering
the hero image when scrolling. No dependencies
or new framework were introduced.

## Preserved originals and unused assets

All six `Screenshot 2026-10-10 ...png` originals remain unchanged for reference.
Only the four selected outputs were processed; originals are not referenced
by the page.

- `Screenshot 2026-10-10 023000.png`: genuine advice to monitor soft tyre wear
  before the final five laps. Optional, omitted to avoid repetitive Doc cards.
- `Screenshot 2026-10-10 023109.png`: genuine advice to retain wet tyres and
  push when fuel is sufficient. Optional, omitted for the same reason.
- `ai-race-engineer.png.png`: pre-existing extra capture, preserved and unused;
  the brief's named weather-aware capture is the selected primary image.
- `overview.png`: archived initial preview, 1300 x 1043. The original main
  portfolio preview in `assets/projects/Projects preview/` remains unchanged.
- `weather-api-initialization.webp`: archived previous `weather-system.webp`,
  unchanged 1050 x 500. It records a genuinely successful Open-Meteo response
  for documented emulated Manila coordinates; it is not the rain-test image.

No screenshot gaps remain for the requested narrative. Optional Doc captures
can be used later without generating additional duplicate outputs. Originals
and archive assets are retained rather than deleted or reorganized.

## Earlier weather API capture evidence

On 10 October 2026 the automated browser granted geolocation permission at
`http://127.0.0.1:8767` and used test coordinates 14.5995, 120.9842 (Manila city
centre), accuracy 25 m. Only the browser location input was emulated.
The application's actual Open-Meteo GET returned HTTP 200: 27.1 °C,
rain/showers/precipitation 0, wind 5.9 km/h. The response's current timestamp
was `2026-10-09T18:15` in the default UTC timezone. The UI mapped this to clear
and displayed the matching values. That capture is now archived separately.

The application still requests current weather once at initialization; no
polling or internal weather-transition simulation is claimed. The newer rain
captures demonstrate mechanics under controlled test conditions, not API rain.

## Sekyord / Groq integration

The Alpha source uses Sekyord as an access layer before requesting Groq
strategy decisions. Source references: `js/doc.js`, `myKey()` at lines 38–52
and `askDoc()` at line 248. Local integration testing needs an authorized
origin. The manually supplied screenshots show genuine successful Doc output
from Joshua's working application; no AI screenshot gap remains.

Earlier local testing encountered an upstream origin rejection and a downstream
401. That historical result did not establish an invalid stored Groq key.
No credentials or integration configuration were inspected in the published
notes, exposed, or changed by this reconciliation.

## Technical verification and remaining issues

- Content follows source behavior in the sibling application's modules,
  including the separately timed simulation and Canvas rendering loops.
- Circuit surfaces/sprites are Canvas. Weather text, lap counter and the
  rain overlay are HTML; captions do not attribute all rain effects to Canvas.
- The current `resetDoc()` no longer assigns to a constant cooldown. The
  previous page's reset-to-constant limitation was removed after reinspection.
- Pit timers and AI requests still lack cancellation/session checks; a pit
  request with no selected service can leave a car stopped.
- AI responses are real, but accuracy, reliability, user metrics, and measured
  performance gains are not established by these screenshots.
- Demo URL: https://jbalagantio.github.io/PIT-STOP/
- Source URL: https://github.com/jbalagantio/PIT-STOP
  Canonical main commit verified during reconciliation:
  `eb1c07b7f2432fbc902c400700600348963adf07`. Local text sources match it;
  deployed-demo parity remains unverified. Unrelated links are preserved.
- The existing portfolio preview path typo (`assets/project/...` versus
  `assets/projects/...`) remains outside this case study change.
- First-person intent/reflection follows Joshua's supplied editorial draft.

PIT STOP source, credentials, and configuration are read-only for this task.
The application working tree is clean at this reconciliation. Its local Git
remote still names the old repository; it was left unchanged because this task
treats PIT STOP as read-only. Case-study links use the canonical repository.

## Future weather improvements

### 1. Weather initialization timing

The race can begin before the initialization request completes, so weather may
be populated after the start. This is asynchronous initialization, not evolving
weather. A future improvement could establish a defined starting condition or
coordinate race startup with weather loading.

Evidence: `js/weather.js`, initialization `getLocation()` at line 135 and
`getWeather()` handling at lines 55–87; `js/main.js`, `startRace()` starts the
simulation without awaiting weather.

### 2. Geolocation failure fallback

Weather API failure sets a fallback, but denied/unavailable geolocation only
logs an error and does not establish a default condition. A future improvement
could provide one consistent condition for denied or unavailable location.

Evidence: `js/weather.js`, `error()` at lines 37–51, unsupported-browser branch
at lines 24–34, API fallback at lines 78–87; `js/state.js`, initial weather at
lines 8–13. Neither improvement was implemented as part of this task.

## Final browser verification

At 360, 768, and 1440 px, all seven images loaded with matching natural and
declared dimensions. No horizontal overflow, invalid local anchors, broken
relative paths, or browser runtime exceptions were found. The desktop hero
shows all four competitors; the circuit image shows three separated visible
competitors; Doc is capped at 320 px wide. A desktop screenshot was visually
reviewed after the sticky-header correction. PIT STOP hashes remained unchanged.

## Final source reconciliation — 10 October 2026

Canonical repository: https://github.com/jbalagantio/PIT-STOP
Branch: `main`
Commit: `eb1c07b7f2432fbc902c400700600348963adf07`

All 16 canonical JavaScript, HTML, CSS, and Markdown files matched the workspace
content after CRLF/LF normalization, including seven active modules, the entry
point, fallback script, legacy presentation and technical notes. The canonical
README identifies the project as Alpha. No Git fetch, checkout, remote update,
application edit, or credential/configuration change was made.

Verified reset behavior:

- `js/doc.js:26` defines the five-second cooldown as a constant;
  `docDecisionCycle()` checks elapsed time at line 622.
- `resetDoc()` at lines 661–669 resets the tracked condition, decision lap,
  in-flight flag and last-request timestamp without assigning to the constant.
  The previously documented constant-assignment defect is resolved.
- `js/main.js:157`, `startRace()` guards against starting an already running
  race. The current Start handler hides the button during the race.
- `resetRace()` at lines 176–233 clears race/car state, restores Start,
  resets visual positions, calls `resetDoc`, clears resource-warning flags,
  hides final results, and renders the starting state.
- Executing the exact reset function bodies with real initial state and stubbed
  UI callbacks completed without exception. All four cars returned to baseline;
  Doc's lap became -1, its in-flight flag false, timestamp 0, and cooldown stayed
  5000 ms. Start visibility and summary/visual callbacks were verified. This
  is a focused reset check, not a full end-to-end integration test.

Still supported by current source, and therefore retained:

- Pit service timers at `js/race.js:266` and `:276` have no cancellation/session
  guard. A no-service pit request still has no release timer.
- The awaited Doc request has no post-response race-session check before its
  decision is applied (`js/doc.js:649` onward). Resetting the in-flight flag
  does not cancel an older request.
- `resetRace()` does not call `disableCarControls()`, and does not retain/cancel
  the simulation timeout. Complete race-boundary robustness is not confirmed.
- Weather startup timing and geolocation fallback opportunities remain valid.
- Deployed-demo parity and live integration reliability were not re-tested.

Both case-study source links now point to the canonical repository. Public
security-shortcoming discussion was removed as requested; this editorial change
is not a claim about application changes. Screenshot files, figure captions,
alt text, CSS, and responsive layout were preserved. Local path and whitespace
checks passed.