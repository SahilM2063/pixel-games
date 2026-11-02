# Pixel Games

Small nostalgic browser games drawn as isometric pixel dioramas, in plain JavaScript with no build step and no image files.

## Games
| Game | What you do | Input |
|------|-------------|-------|
| [Mango Raid](mango-raid/) | Knock mangoes off uncle's tree while he naps, without waking him or the dog | Drag back and release; arrows + space |
| [Rooftop Patang](rooftop-patang/) | Kite festival on three rooftops: cut the neighbours' kites, loot the ones that fall, fly into the night | Hold to pull towards the pointer, let go to give string; space + arrows |

## Run
```bash
node serve.mjs
```
Then open http://127.0.0.1:5300/. Any static file server works, and the site deploys as plain static files (GitHub Pages included).

## Credits
This project stands on someone else's work, and it would not exist without it.

- **[pixel-plays](https://github.com/amirmushichge/pixel-plays)** by **[Amir Mushich](https://x.com/AmirMushich)** (MIT): the renderer in `engine.js` and the menu in `shell.js`, adapted here. The pixel-diorama concept is by **[abhi](https://x.com/awwbhi2)**.
- Visual reference for the style: **[Small plays](https://x.com/zzzzshawn/status/2111546123546661289)** by **shawn**.
- Sound recordings in `mango-raid/` and `rooftop-patang/sounds/` come from [Pixabay](https://pixabay.com/sound-effects/) and [Mixkit](https://mixkit.co/free-sound-effects/) (uploaders kave_msri, freesound_community, oxidvideos, storegraphic). Check each site's licence before reusing them. Everything else is synthesised in code.

## Changes to the engine
`engine.js` has small additions for these games: a `knee` option so figures can have bare legs, `width`, `height` and `zoom` scene options, and a `shadowBase` for shadows on raised roofs.

## How it is put together
- `engine.js`: the shared software renderer (camera, depth buffer, colour ramps, dither, shadows, edges, figures, wind).
- `shell.js`: the game menu, Rules popup and credits.
- Each game is one `index.html`: `bake()` draws the static scene once, `update(dt)` runs the rules, `draw()` paints the moving parts every frame.

## Add a game
Create `<id>/index.html`, load `../shell.js`, call `PixelPlays.mount({ id, rules })`, set `window.PP_SCENE`, load `../engine.js`, then add the game to `GAMES` in `shell.js`. The page needs a `#mute` button.

## Licence
The code is under the [MIT Licence](LICENSE), which includes the original copyright notice for pixel-plays. Sound recordings keep their own licences.
