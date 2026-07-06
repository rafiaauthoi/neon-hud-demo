# Neon HUD Demo

A glowing, hand tracking interactive display built for tabling and festival showcases. No touching, no controller, just a webcam and a hand.

## What it does

- **Idle mode**: a pulsing scan ring and drifting ambient particles keep the screen visually alive, pulling attention from a distance when nobody is interacting.
- **Active mode**: the moment a hand enters frame, a "TARGET ACQUIRED" flash fires, fingertip glow trails appear, and a side energy bar rises and falls with hand height.
- **Pinch**: touching thumb and index finger together sends out a glowing pulse ring from the pinch point.

## How to run it

1. Clone this repo.
2. Open the folder in VS Code.
3. Right click `index.html` and choose "Open with Live Server" (or open the file directly in a browser).
4. Allow camera access when prompted.
5. Step back so your hand and some space around it are visible, then move your hand into frame to trigger active mode.

No installs, no build step, no account, and no paid services. Everything runs client side in the browser using MediaPipe's hand landmark model, loaded from a public CDN.

## Tools used

- MediaPipe Tasks Vision (hand landmark detection)
- Canvas API (all visual rendering)

## Notes for tabling setup

- Works best with a laptop propped up so the camera has a clear, mostly static background. Faces or other hands entering frame can distract detection since this demo tracks a single hand.
- The pinch threshold is tuned for a clean, deliberate pinch. If it triggers too easily or not easily enough for your specific camera and lighting setup, adjust `PINCH_DISTANCE_THRESHOLD` near the top of the script.
- Consider running it fullscreen (F11 in most browsers) for the actual event, so the video frame fills more of the visible screen space.

## Status

Complete.