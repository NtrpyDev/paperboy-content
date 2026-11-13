# paperboy-content

Published feed and explainers for the [Paperboy](https://github.com/NtrpyDev/paperboy-app) app.

The Paperboy pipeline writes to this repository. The app does not read it directly: the Paperboy worker at https://paperboy.ntrpydev.workers.dev serves these files, fetching each one from here the first time it is asked for.

## Layout

- `feed/v1/head.json`: the head. Says how many chunks exist, how many items they hold, and the lowest app version that can read the feed.
- `feed/v1/chunks/<6 digit number>.json`: chunks of up to 40 feed items, numbered from the oldest. Only the highest numbered chunk ever changes.
- `feed/v1/upgrades.json`: explainers added later to items in chunks that no longer change.
- `papers/<paper id>/`: one folder per paper. `meta.json` is the full record. A paper with an explainer also has `index.html` (the explainer) and `hero.webp` and `hero-night.webp` (the card image for the light and the dark theme).
- `state/`: the pipeline's own bookkeeping: which days each source has been read through, which papers are already in the feed, and which are waiting for an explainer.

The record shapes are JSON schemas in the app repository's `schema/` folder.

Explainers are machine written and can be wrong. Each one says so and links the paper it explains.

## License

See `LICENSE`.
