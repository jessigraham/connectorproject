# We Want You · Connector recruiting page

Static site, no build step. In Vercel: import this repo, Framework Preset "Other", no build command, output directory = root.
Every push to `main` redeploys.

The creative brief and Connector Hub source documents live in `Documents/Ascend/Connector program`, not here:
this repo is public, so keep internal material out of it.

```
index.html                         the page (HTML, CSS, JS inline)
assets/brand-chime-cinematic.mp3   entry chime (4.4s)
assets/welcome-jessi.mp3           Jessi's welcome line (ElevenLabs, Jessi Voice 1, 4.9s)
assets/og.png                      link preview image, 1200x630
```

## Before launch

1. **Booking link.** In `index.html`, set `CONFIG.callUrl` to Jessi's booking link (Calendly or similar). Until then,
   the "Schedule a call with Jessi" buttons show a "coming soon" toast. The demo is not linked from this page;
   Jessi offers it on the call to qualified leads (brief, Revision 2).
2. **Welcome voice.** Done: `assets/welcome-jessi.mp3` was generated from "Jessi Voice 1" with the key in
   `~/.config/ascend/elevenlabs.env`. If the line changes, regenerate it and update `CONFIG.welcomeLine`
   so the caption matches. Without the file the page still works: the caption plays on its own.
3. **Domain.** Update `og:url` in the `<head>`. The og image path is relative; some text-message
   previewers want an absolute URL, so switch `og:image` to the full URL once the domain is known.
4. **Analytics.** Uncomment the Plausible script in the `<head>` and set the domain. Events tracked:
   `Arrival`, `Sound Toggle`, `Slider Used`, `Slider Set`, `Package Chip`, `Traits All Four`,
   `Share Click`, `Call Click`. (Google Analytics `gtag` also works if present.)

## How the arrival works

The page tries to play the chime on load. If the browser allows it, the pulse and chime run together
and Jessi's welcome follows at ~4.5s. If the browser blocks sound (most phones, most links from texts),
the screen rests on a glowing "Tap to begin" ring; the first tap fires the chime, pulse and welcome as
one moment. "Continue without sound" is always offered, and the mute toggle stays bottom right.
The arrival plays once per browser tab session. Reduced-motion visitors get a soft fade instead.

`?ref=<name>` on the page URL is passed through to the booking link, so a referral can be credited there.

## Guardrails held

Standard plan fees only. No client package pricing, deck process, scoring, scripts or Hub internals.
Zero em dashes.
