# Neon HUD Demo

A glowing, hand tracking interactive display built for tabling and festival showcases. No touching, no controller, just a webcam and two hands.

**Live demo:** https://rafiaauthoi.github.io/neon-hud-demo/c

## What it does

- **Idle mode**: a pulsing scan ring and drifting ambient particles keep the screen visually alive, pulling attention from a distance when nobody is interacting.
- **Active mode**: the moment a hand enters frame, a "TARGET ACQUIRED" flash fires, a glowing hand skeleton and fingertip dots trace both hands independently, and a side energy bar rises and falls with hand height.
- **Pinch**: touching thumb and index finger together sends out a glowing particle burst from the pinch point, along with a soft chime.
- **Two-hand combo**: pinching with both hands within half a second of each other triggers a bigger screen-wide pulse, a particle explosion, and a "COMBO" flash.
- **Charge and release**: holding a hand up near the top of frame for about half a second fully charges the energy bar, triggering a full screen flash, a large particle burst, and a triumphant tone.
- **Melody**: each hand's height maps to a note on a musical scale, so moving your hands plays an actual, listenable melody rather than a raw pitch sweep.

## How to run it

1. Clone this repo.
2. Open the folder in VS Code.
3. Right click `index.html` and choose "Open with Live Server" (or open the file directly in a browser).
4. Click "Start Demo" first. This step is required before any audio will play, browsers block sound until a real click happens.
5. Allow camera access when prompted.
6. Step back so your hand and some space around it are visible, then move one or both hands into frame to trigger active mode.

No installs, no build step, no account, and no paid services. Everything runs client side in the browser using MediaPipe's hand landmark model and Tone.js for audio, both loaded from public CDNs.

## Tools used

- MediaPipe Tasks Vision (two-hand landmark detection)
- Canvas API (all visual rendering)
- Tone.js (melody, pinch chimes, combo chord, charge tone)

## Customizing the music

Near the top of the script, this line controls every note the demo can play:

```javascript
const SCALE = ['C4', 'D4', 'E4', 'G4', 'A4', 'C5', 'D5', 'E5', 'G5', 'A5'];
```

Add, remove, or reorder notes freely, any valid Tone.js note name works. You can also change the tone's character by editing the `oscillator: { type: 'sine' }` settings on any of the synths further down, try `'triangle'` or `'square'` for a different timbre.

## Notes for tabling setup

- Works best with a clear, mostly static background. Extra people or hands passing through frame can distract detection.
- Pinch threshold and charge timing are tuned to be forgiving but deliberate, adjust `PINCH_DISTANCE_THRESHOLD`, `CHARGE_FULL_THRESHOLD`, and `CHARGE_HOLD_MS` near the top of the script if they feel too sensitive or not sensitive enough for your specific camera and lighting.
- The bordered display box scales with the browser window (`width` and `max-width` on `#video-wrapper` in the CSS) rather than using a fixed pixel size, so it adapts to whatever monitor it's shown on. Test and adjust these two values on the actual showcase display beforehand.
- Run the browser in fullscreen (F11) for the actual event for maximum visual impact.
- A real external speaker (not laptop speakers) is recommended if sound is enabled, festival environments are loud enough that laptop speakers alone likely won't be heard.

## Status

Complete.
