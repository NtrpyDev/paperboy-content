# paperboy-content

Published feed and explainers for the [Paperboy](https://github.com/NtrpyDev/paperboy-app) app.

The Paperboy pipeline writes to this repository. The app does not read it directly: the Paperboy worker at https://paperboy.ntrpydev.workers.dev serves these files, fetching each one from here the first time it is asked for.

## Layout

- `feed/v1/head.json`: the head. Says how many chunks exist, how many items they hold, the current kit version, and the lowest app version that can read the feed.
- `feed/v1/chunks/<6 digit number>.json`: chunks of up to 40 feed items, numbered from the oldest. Only the highest numbered chunk ever changes.
- `papers/<paper id>/`: one folder per paper. `index.html` is the explainer, `meta.json` is the full record, and `hero.webp` is the card image when there is one.

The record shapes are JSON schemas in the app repository's `schema/` folder.

## Test fixture

The only item so far, `doi-10.0000-paperboy.fixture`, is a test fixture and describes no real paper. Its explainer is a copy of the kit gallery page.

## License

See `LICENSE`.
