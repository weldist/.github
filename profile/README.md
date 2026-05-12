# weld.ist

> We weld the missing pieces onto big open source packages — small, focused, reversible.

## Who we are

There are big, stable open source packages we genuinely enjoy using — `spatie/laravel-medialibrary`, `inertiajs`, `laravel/octane`, and the like. Excellent packages; we use them every day.

But every now and then we need a small change in one of them that our project requires — something upstream doesn't support because it doesn't fit the package's own policy or the wider community's priorities.

The usual answers are bad: fork the package (and take on a permanent merge burden), rewrite it from scratch (and lose a decade of accumulated edge cases), or paste a workaround into your application (and rediscover the same thing three projects later).

We take a fourth path. We **weld** — if the package offers an extension point (a plugin, a driver, an event/listener), we ship a small, focused package that uses that point idiomatically: it bolts the missing piece onto the existing structure, comes with its own tests and maintenance commands, and then stays out of your way.

What we work on isn't tied to one ecosystem: if we hit a gap and see how to fix it, we go there — whatever the ecosystem.

## What we aim for

- **One package, one problem.** No utility belts, no god objects, no kitchen-sink namespaces.
- **Solid foundation.** Every package ships with its own test suite and targets the version range the parent package supports.
- **Minimum coupling.** Each package depends only on the parts of the parent package it extends — not on the whole framework.
- **Reversible operations.** Commands that move data or files come with a `--dry-run` preview and an inverse command. Anything those commands do, you can undo.
- **Honest naming.** A `Migrate` command migrates; a `Prune` command prunes. If you need to read three classes to understand one method, we've done it wrong.
- **Semver discipline.** Breaking changes come with a major version bump and a migration guide. No surprises in a patch release.

## Packages

### [`weldist/spatie-medialibrary-uuid-path-generator`](https://github.com/weldist/spatie-medialibrary-uuid-path-generator)

**Problem.** [`spatie/laravel-medialibrary`](https://github.com/spatie/laravel-medialibrary) stores every media item in a flat directory named after its sequential numeric ID — slow at scale, easily guessable, leaving empty parent directories behind on deletion, and `media-library:clean` can only reclaim the numeric ones.

**Solution.** A UUID-based `PathGenerator` that shards items across a four-level directory tree, a `FileRemover` that cascades upward to clear empty parents, idempotent `--dry-run` migration commands that move between the two layouts both ways, and `media:prune-uuid-paths` to reclaim the orphaned directories `media-library:clean` misses — full details in the [repo](https://github.com/weldist/spatie-medialibrary-uuid-path-generator).

### [`weldist/spatie-medialibrary-webp-downloader`](https://github.com/weldist/spatie-medialibrary-webp-downloader)

**Problem.** Adding media from a URL — OAuth avatars, profile photos, image fields from an external API — stores whatever format the source serves (usually JPEG or PNG) as-is, turning optimization into a separate later step with an extra queue job, double storage until the original is deleted, and a worker.

**Solution.** An inline, synchronous, idempotent conversion layer that turns URL-downloaded images into WebP **before they're written to disk** — no queue job, no double storage, no worker — plus a separate, restartable artisan command that backfills already-stored media on the queue via `ConvertMediaToWebpJob` — full details in the [repo](https://github.com/weldist/spatie-medialibrary-webp-downloader).

## Behind it

weld.ist is run by [@X-Adam](https://github.com/x-adam) — a one-person workshop. We say "we" not because of size, but because every package ships with the care of a team behind it, with its own documentation. Everything here came from real points where we got stuck on real projects; instead of keeping it to ourselves, we share it in the hope someone else can use it too. If it helped with something of yours, we'd love to hear about it.

## Contributing

Issues, ideas, and patches are welcome in each package's own repo. If you've hit a gap that fits our principles — focused, reversible, honest — open an issue and tell us about it, whatever the ecosystem. The next weld might come from your suggestion.

---

With our mind and heart! · [weld.ist](https://weld.ist)
