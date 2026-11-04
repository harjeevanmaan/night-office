# The night office landing page (2026-11-02)

Real page built from the style A mockup (`docs/agency/video/ideas/landing/A.html`). Static, no build step, no network: fonts, clips and posters are beside it. Open `index.html` in a browser or serve the folder. Published for review at https://claude.ai/artifact/VMWsFa2uuo6RdvZNcrebdN (an artifact copy of the page without the doctype wrapper, same files).

## What is on it
- Hero: the eight pieces playing muted on a loop behind the headline (`v/bg1.mp4` to `bg8.mp4`, 480x270, crf 30, about 90 KB each), paused when the hero scrolls out of view. Headline, sub, the blue button, "Watch the 90 second video" (opens the full cut in a lightbox, with sound, Escape or the X closes it).
- Eight rows, strictly alternating: `v/p1.mp4` to `p8.mp4` are the exact parts of cut 7 (`remotion/out/cut2/parts/`), video copied, silent audio tracks dropped except piece 3 which keeps the call audio ("Sound on" tag). Press play on the frame or "Watch this part" in the text; one plays at a time, native controls appear while playing, the frame resets to its poster at the end.
- Three outcomes (worst parts gone, tens of thousands saved, better service), drawn in HTML as in the mockup. The tally figures are placeholders marked EXAMPLE.
- Close panel: "Save tens of thousands while giving better service." / "Built on your TMS, your email, your phone, within 30 days, guaranteed." / a line that fills green through Day 3, 10, 30 the first time it scrolls into view (the video's last screen copy: "We tell you what we can deliver." / "We set it up for you." / "It's fully live."), one sentence under each. On phones the line runs down the left side.
- FAQ, footer with the placeholder contact line.

## Still placeholder
- Both buttons link to the close panel; no booking link yet. Footer contact "number to come". Price in the FAQ "to be decided". The tally amounts.

## Rebuild the clips
`v/p{n}.mp4`: `ffmpeg -i parts/NN-*.mp4 -c:v copy -an -movflags +faststart` (piece 3: `-c copy`). `v/bg{n}.mp4`: `-an -vf scale=480:270 -c:v libx264 -profile:v main -level 3.1 -pix_fmt yuv420p -crf 30 -preset slow -g 60 -movflags +faststart`. `v/full.mp4` is the 1500k copy of cut 7 (13 MB). Posters `img/p{n}.jpg` are the landing mockup's frames as JPEG q3.

## Checked
Laptop 1440 and phone layout (Chrome, 500 is the narrowest headless window; the phone media query applies): no horizontal overflow, fonts load, all ten hero loops play, play / pause / lightbox / line fill verified by script. Only console entry was the favicon 404, now an empty data: icon.
