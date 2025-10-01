# GSAP Scrolling Mask Animation

A simple, eye-catching scroll-driven “mask” effect using GSAP 3 and ScrollTrigger over a full-viewport background video. As you scroll, the headline scales massively while the section is pinned, creating a bold reveal/mask look powered by CSS blend modes.

## Demo

![Demo – GSAP Scrolling Mask Animation](./screendemon.gif)

## Demo summary

- Pinned section with smooth scrubbed animation
- Huge scaling text using GSAP
- Video background with CSS blend to simulate a masking effect

## How it works

- The video is fixed and covers the viewport.
- The `.mask` layer sits above the video using `mix-blend-mode: screen` with a white background, affecting how the text blends with the video.
- GSAP’s `ScrollTrigger` pins the container and scrubs the `scale` of the `h2` from its initial size up to 300, over a long scroll distance.

Key snippet:

```js
gsap.to("h2", {
  scale: 300,
  scrollTrigger: {
    trigger: ".container",
    scrub: 1,
    pin: true,
    start: "top top",
    end: "+=5000",
    ease: "none",
  },
});
```

## Project structure

- `index.html` – Markup with GSAP + ScrollTrigger via CDN and the inline animation.
- `style.css` – Layout, font, and blend-mode styling.
- `README.md` – This file.

## Run it locally

This is a static page—no build step required.

- Double-click `index.html` to open it in your browser, or
- Use the VS Code Live Server extension, or
- From Windows Command Prompt (cmd):

```bat
start "" "index.html"
```

Note: Some browsers restrict autoplaying videos; the `<video>` tag is `muted` and `autoplay` to improve compatibility. If the video doesn’t play, try serving via Live Server or replace the video source with a local `.mp4` file.

## Customization

- Change the headline: edit the `<h2>` text in `index.html`.
- Adjust animation strength:
  - Tweak `scale`, `start`, `end`, and `scrub` in the GSAP config.
- Swap the video:
  - Replace the `<source>` `src` with your own direct `.mp4` URL or a local file (e.g., `assets/video.mp4`). Some sites provide “download” links that aren’t direct media URLs; prefer a direct `.mp4` path or host locally.
- Styling: modify fonts/colors in `style.css`. The mask effect relies on `.mask { mix-blend-mode: screen; background: #fff; }`.

## Dependencies

- GSAP 3.12 (CDN)
- ScrollTrigger (GSAP plugin via CDN)

CDN links are included in `index.html`; no installation needed.

## Troubleshooting

- Video doesn’t show/play: use a direct `.mp4` URL or a local file; try serving with Live Server.
- Nothing animates: check that the CDN scripts load (network tab) and there are no console errors.
- Hard edges/contrast: experiment with `mix-blend-mode`, background colors, or add a subtle overlay.

## Credits

- Animation: GSAP (GreenSock) and ScrollTrigger.
- Stock video: Pexels (replace with your own asset as needed).

## License

No license file is included. If you plan to publish or reuse, add a LICENSE to this repository.
