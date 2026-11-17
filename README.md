# Talk

A two-person video call that translates what you say as you speak, in the browser at [mco.dev/talk](https://mco.dev/talk/). It works in English, French, German and Spanish.

It is a static app with no build step: open `index.html` from any web server. The two callers connect directly to each other using [PeerJS](https://peerjs.com/) (vendored in `vendor/`). Translation uses Google's Gemini with your own API key, and only one of the two callers needs one.

This repo is mounted in [mco-gh/mco.dev](https://github.com/mco-gh/mco.dev) as a git submodule at `static/talk`. After pushing a change here, update the submodule pointer there to publish it:

```bash
cd mco.dev
git submodule update --remote static/talk
git commit -am "Update talk"
git push
```

## Install on a phone

The app is an installable web app: `manifest.webmanifest` describes it, and `sw.js`
is a network-first service worker, so it is always current when online and still
opens offline. Nothing needs bumping on release. The icons in `icons/` are rendered
from the SVG sources by `bash build/icons/render.sh` (needs Google Chrome).
