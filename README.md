# AppADay 137: Pocket Hurdles

A first person hurdles runner you play with your body. Hold your phone upright, run in place, jump for real to clear hurdles, and lean left or right to switch lanes around the blue landing mats. No phone handy? It plays just as well with arrow keys and space, or with swipes and taps.

Category: G (Games and Interactive)
Live: https://augustineiacopelli.github.io/appaday-137-pocket-hurdles/
Portfolio: https://augustineiacopelli.github.io/appaday/

## How to play

Choose Play with Motion on a phone over HTTPS, allow motion access, and hold still for three seconds while the app calibrates. After the countdown, jump to clear the striped hurdles and lean to change lanes. Mats are too tall to jump, so you have to go around them. Speed climbs from 8 to 20 m/s, and your distance in meters is your score. Your best run is saved on the device.

Choose Play with Touch or Keys anywhere else. Arrow keys change lanes, space or up arrow jumps, and P or Escape pauses. On a touchscreen, swipe sideways to change lanes and tap to jump.

## Motion controls

A jump is detected as a push off spike in vertical acceleration followed by a brief free fall reading within 350 ms, then a 700 ms cooldown. Lanes come from how far the phone is rolled from your calibrated neutral position, with hysteresis so the right and left lanes engage at 12 degrees and release back to center below 6 degrees. Lean readings are frozen while a jump is in progress or when the phone is being shaken hard, so jumping never changes lanes by accident. If motion permission is denied or no sensor data arrives within one second, the game falls back to touch and keys automatically.

## Tuning

Tap Dbg in the lower right corner to open the debug overlay. It shows the filtered vertical ratio, total acceleration, roll offset, target lane, jump state, frame rate, and current thresholds. Use the plus and minus buttons to adjust the jump spike threshold in steps of 0.1 and the lean threshold in steps of 1 degree, and tick Invert lean if leaning right moves you left on your device. All settings save immediately.

## Tech

Single self contained index.html with inline CSS and JavaScript, a canvas renderer with a simple perspective projection, the DeviceMotion API with iOS permission handling, the Screen Wake Lock API, and Web Audio for jump and crash sounds. No frameworks and no build step. The only external resource is the Barlow Condensed font from Google Fonts.

Stored in localStorage: appaday137-best, appaday137-debug, appaday137-invert, appaday137-spike, appaday137-lean.

Part of AppADay, one complete web app shipped every day by Augustine Iacopelli.
