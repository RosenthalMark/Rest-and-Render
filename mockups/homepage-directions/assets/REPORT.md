# Asset Preparation Report (`mockups/homepage-directions/assets/`)

All derivatives were written to `mockups/homepage-directions/assets/`.

## Deliverables Summary

| Filename | Pixel Dimensions | File Size | Summary of Processing |
| --- | --- | --- | --- |
| `machine-hero.jpg` | `1024 × 1600` | `213,270 B` (`208.3 KB`) | Cleaned outer background to flat `#000000`, straightened `+0.35°` clockwise and centered horizontally (`knobCenter.x = 0.5`), extended canvas below the dispensing slot (`+249 px` in source scale, `235 px` below cabinet bottom at output scale), resized to long edge `1600 px` at JPEG quality `82`. |
| `machine-bar.png` | `400 × 180` | `105,297 B` (`102.8 KB`) | Cut out only the rotating `"1 TURN"` chrome crossbar with a 4× supersampled feathered alpha mask, counter-rotated `-0.15°` so its rest angle is `0°`, centered on the shared knob/ring pivot, scaled to long edge `400 px`. |
| `machine-knob-ring.json` | N/A (JSON) | `543 B` (`0.5 KB`) | Recorded front-end knob/ring/bar geometry in fractions of `machine-hero.jpg` width and height, plus 1-decimal-place percentage and pixel representations. |
| `poster-web.jpg` | `1200 × 1200` | `236,937 B` (`231.4 KB`) | Composited `bunny-poster.png` onto `#000000`, resized from `2500 × 2500` to `1200 × 1200` (Lanczos), saved at JPEG quality `82`. |
| `artwork-web.jpg` | `1600 × 901` | `195,932 B` (`191.3 KB`) | Extracted `homepage-directions/assets/homepage-artwork.png` (`2870 × 1617`) from `mockups/homepage-directions.zip` without modifying the archive, resized to `1600 px` wide, saved at JPEG quality `82`. |
| `intro-h264.mp4` | `1920 × 1080` | `2,686,622 B` (`2.56 MB`) | Transcoded `bunny-intro.mp4` from HEVC/H.265 to H.264 (`High` profile, `yuv420p`, CRF `25`, maxrate `3.2 Mbps`) + AAC (`96 kbps`), preserved `1920 × 1080` and `8.23s` duration, enabled `+faststart`. |
| `hero-portrait-h264.mp4` | `720 × 1280` | `1,796,340 B` (`1.71 MB`) | Transcoded the owner's CapCut export `1102(1).mp4` (HEVC/H.265, `1080 × 1920`, `60 fps`, `13.8 Mbps`, AAC stereo) to H.264 (`High` profile, `yuv420p`, CRF `26`, maxrate `1.6 Mbps`, preset `slow`), Lanczos downscale to `720 × 1280`, frame rate reduced to `30 fps`, audio dropped because the hero plays muted, `8.37s` duration preserved, `+faststart` enabled. Serves as the Paper Neon hero's portrait source on phones; `intro-h264.mp4` stays the landscape source. |
| `poster-portrait.jpg` | `1080 × 1920` | `235,353 B` (`229.8 KB`) | Pulled the frame at `1.2s` from the owner's `1102(1).mp4` master at its native `1080 × 1920`, saved at JPEG `-q:v 4`. Used as the Paper Neon hero's portrait poster so the still shown before playback — and the only thing shown when autoplay is blocked or Reduced Motion is on — matches the 9:16 phone frame instead of cropping the square `poster-web.jpg` down to a sliver. |
| `store-room.jpg` | `1600 × 893` | `378,174 B` (`369.3 KB`) | Resized `Store_art.jpeg` (`1376 × 768`) to `1600 px` wide (Lanczos), saved at JPEG quality `82`. |
| `tokyo-band.jpg` | `1400 × 1030` | `231,889 B` (`226.5 KB`) | Resized `Tokyo_art.png` (`871 × 641`) to `1400 px` wide, darkened overall (`0.78×` + `1.08` highlight gamma + `0.78×` top-band gradient over the upper signage) so baked-in text recedes, saved at JPEG quality `80`. |
| `REPORT.md` | N/A (Markdown) | ~`3.8 KB` | This summary report, measured knob geometry, tool/command log, and quality notes. |

**Total added bytes (all 11 deliverables):** `6,084,173 B` (`5.80 MiB`, still under the `8 MB` cap). The owner-supplied source `1102(1).mp4` (`14,414,598 B`) is kept locally as the master and is not a page deliverable.

---

## Measured Knob Geometry (`machine-knob-ring.json`)

### Source Measurements (`Vending_art.jpg`, `1296 × 1776`)
- **Outer chrome bezel circle:** `x = 468.5 .. 808.5`, `y = 1028.5 .. 1368.5` → center `(638.5, 1198.5)`, outer radius `170.0 px`.
- **Inner chrome ring / recessed disc groove:** `x = 502.5 .. 774.5`, `y = 1062.5 .. 1334.5` → center `(638.5, 1198.5)`, inner radius `136.0 px`.
- **Crossbar (`"1 TURN"` handle):** `x = 497.5 .. 775.5` (outer bevel ends; inner raised ridge is `x = 507.5 .. 767.5`), `y = 1139.0 .. 1258.0` → center `(636.5, 1198.5)`, outer bevel half-length `139.0 px` (inner raised face `130.0 px`), rest angle `-0.15°` counter-clockwise.
- **After straightening (`+0.35°` CW), centering (`x_center = 648.0`), extending bottom canvas (`1296 × 2025`), and scaling (`64/81 = 0.790123×`) to `1024 × 1600` (`machine-hero.jpg`):**
  - `knobCenter`: `(512.0, 947.0)` px = `(0.5, 0.5919)` of `(w, h)` = `(50.0%, 59.2%)`
  - `ringOuterRadius`: `134.3 px` = `0.1312` of width (`13.1%`) / `0.0840` of height (`8.4%`)
  - `ringInnerRadius`: `107.5 px` = `0.1049` of width (`10.5%`) / `0.0672` of height (`6.7%`)
  - `barHalfLength`: `109.8 px` = `0.1073` of width (`10.7%`) / `0.0686` of height (`6.9%`)
  - `barAngleRestDeg`: `0`

```json
{
  "image": {
    "w": 1024,
    "h": 1600
  },
  "knobCenter": {
    "x": 0.5,
    "y": 0.5919
  },
  "ringOuterRadius": 0.1312,
  "ringInnerRadius": 0.1049,
  "barHalfLength": 0.1073,
  "barAngleRestDeg": 0,
  "percent": {
    "knobCenter": {
      "x": 50.0,
      "y": 59.2
    },
    "ringOuterRadius": 13.1,
    "ringInnerRadius": 10.5,
    "barHalfLength": 10.7
  },
  "pixels": {
    "knobCenter": {
      "x": 512.0,
      "y": 947.0
    },
    "ringOuterRadius": 134.3,
    "ringInnerRadius": 107.5,
    "barHalfLength": 109.8
  }
}
```

---

## Honest Quality & Limitation Notes

1. **Background neutralization & canvas extension on `machine-hero.jpg`:**
   - The supplied `Vending_art.jpg` (`1296 × 1776`) already had a near-black (`rgb(0,0,0)` with minor JPEG ringing up to `rgb(8,6,10)` along the cabinet boundary) exterior rather than a light-grey right background. We masked the cabinet silhouette with a 1 px feathered edge to eliminate all exterior JPEG mosquito noise to pure `#000000` (`rgb(0,0,0)`) and extended the bottom canvas with matching `#000000` (`235 px` below the cabinet bottom lip, `308 px` below the dispensing slot center in the `1024 × 1600` output). Because the background is `#000000`, the bottom extension is completely seamless with zero smearing or stretching of cabinet pixels, though a separate cast drop shadow outside the cabinet silhouette cannot be seen against pure `#000000` (the cabinet's natural shaded bottom lip rolloff at `y = 1362..1368` provides the grounding edge).
2. **Cabinet straightening vs. perspective taper:**
   - In `Vending_art.jpg`, the upper marquee slopes upward to the right by `-0.55°` to `-0.67°` while the lower door and dispensing plate are nearly level (`±0.05°`), and the left and right outer walls flare outward toward the bottom by `-1.04°` and `+1.37°` (camera perspective keystoning). We applied a rigid `+0.35°` clockwise rotation rather than a non-uniform perspective warp so that the chrome knob ring remains a true circle (`r_x = r_y = 134.3 px`) and cabinet pixels are not stretched. A small residual perspective flare (`~1.2°` per side) remains inherent to the original camera angle.
3. **Baked-in crossbar in `machine-hero.jpg` when `machine-bar.png` rotates:**
   - At rest (`0°`), `machine-bar.png` registers cleanly over the crossbar in `machine-hero.jpg`. Because `machine-hero.jpg` is a photograph of the real cabinet with the horizontal crossbar baked into the recessed inner disc (`"INSERT COIN"` face), rotating `machine-bar.png` away from `0°` in the front end will reveal the stationary horizontal bar underneath unless the front end masks or darkens the inner disc (`ringInnerRadius`) behind the rotating bar during rotation. Inpainting the recessed metal texture and `"INSERT COIN"` engraving behind the bar was not attempted with local tools to avoid synthetic blur artifacts on the hero photograph.
