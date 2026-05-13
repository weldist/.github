<div align="center">

<img src="https://raw.githubusercontent.com/weldist/.github/master/assets/weld_ist-logo.svg" width="360" alt="weld.ist" />

**We weld the missing pieces onto big open source packages.**
Small, focused, reversible — packages that bolt onto what you already use.

[![PHP](https://img.shields.io/badge/PHP-8.3%2B-777BB4?style=flat-square&logo=php&logoColor=white)](https://www.php.net)
[![Laravel](https://img.shields.io/badge/Laravel-11_%7C_12-FF2D20?style=flat-square&logo=laravel&logoColor=white)](https://laravel.com)
[![License](https://img.shields.io/badge/License-MIT-22c55e?style=flat-square)](https://opensource.org/licenses/MIT)
[![Website](https://img.shields.io/badge/weld.ist-0ea5e9?style=flat-square&logo=googlechrome&logoColor=white)](https://weld.ist)

</div>

---

<table align="center"><tr><td align="center" width="25%">
<h3>🎯</h3><b>Focused</b><br/><sub>One package, one problem</sub>
</td><td align="center" width="25%">
<h3>🧪</h3><b>Tested</b><br/><sub>Across the parent's range</sub>
</td><td align="center" width="25%">
<h3>🔌</h3><b>Low coupling</b><br/><sub>Uses idiomatic extension points</sub>
</td><td align="center" width="25%">
<h3>↩️</h3><b>Reversible</b><br/><sub><code>--dry-run</code> + inverse commands</sub>
</td></tr></table>

---

## 🧠 Why "weld"?

Big, stable packages — `spatie/laravel-medialibrary`, `inertiajs`, `laravel/octane` — are excellent. But every now and then a project needs a small change upstream won't accept because it doesn't fit the package's policy.

The usual answers are bad:

- **Fork it** → permanent merge burden
- **Rewrite it** → lose a decade of edge cases
- **Workaround in your app** → rediscover the same thing three projects later

We take a fourth path. If the package offers an extension point — a plugin, a driver, an event — we ship a **small, focused package that uses it idiomatically**. It bolts the missing piece on, brings its own tests, then stays out of your way.

---

## 📦 Packages

<table>
<tr>
<td width="33%" valign="top">

### 🗂️ [`spatie-medialibrary-uuid-path-generator`](https://github.com/weldist/spatie-medialibrary-uuid-path-generator)

[![Packagist](https://img.shields.io/badge/composer-F28D1A?style=flat-square&logo=packagist&logoColor=white)](https://packagist.org/packages/weldist/spatie-medialibrary-uuid-path-generator)

Replaces `spatie/laravel-medialibrary`'s flat ID-based file layout with a UUID-based `PathGenerator` that shards media into a four-level tree, plus a cascading `FileRemover`, two-way `--dry-run` migration commands, and `media:prune-uuid-paths` to reclaim orphaned directories that `media-library:clean` misses.

</td>
<td width="33%" valign="top">

### 🖼️ [`spatie-medialibrary-webp-downloader`](https://github.com/weldist/spatie-medialibrary-webp-downloader)

[![Packagist](https://img.shields.io/badge/composer-F28D1A?style=flat-square&logo=packagist&logoColor=white)](https://packagist.org/packages/weldist/spatie-medialibrary-webp-downloader)

An inline, idempotent conversion layer for `spatie/laravel-medialibrary` that turns URL-downloaded images into WebP **before they're written to disk** — no extra queue job, no double storage — plus a restartable artisan command to backfill already-stored media on the queue.

</td>
<td width="33%" valign="top">

### 💓 [`laravel-pulse-md5-patch`](https://github.com/weldist/laravel-pulse-md5-patch)

[![Packagist](https://img.shields.io/badge/composer-F28D1A?style=flat-square&logo=packagist&logoColor=white)](https://packagist.org/packages/weldist/laravel-pulse-md5-patch)

Makes `laravel/pulse` work on MySQL servers without the `MD5()` function (MySQL 9.6+, managed offerings where the Legacy Hashing component can't be installed) by swapping Pulse's generated `key_hash` column for a plain `char(32)` and computing the hash in PHP instead of the database.

</td>
</tr>
</table>

---

## 🚀 Install

```bash
composer require weldist/<package-name>
```

> Each repo's README has setup, config, migration, and usage examples.

---

## 📐 What we aim for

| | |
|---|---|
| 🎯 **One package, one problem** | No utility belts, no god objects, no kitchen-sink namespaces. |
| 🧪 **Solid foundation** | Every package ships with its own test suite, targeting the parent's supported range. |
| 🔌 **Minimum coupling** | Each package depends only on what it actually extends — not the whole framework. |
| ↩️ **Reversible operations** | Commands that move data come with `--dry-run` and an inverse. What they do, you can undo. |
| ✍️ **Honest naming** | `Migrate` migrates, `Prune` prunes. If you need to read three classes to understand one method, we got it wrong. |
| 🏷️ **Semver discipline** | Breaking changes mean a major bump and a migration guide. No surprises in a patch release. |

---

## 👋 Behind it

weld.ist is run by [@X-Adam](https://github.com/x-adam) — a one-person workshop. We say "we" not because of size, but because every package ships with the care of a team behind it. Everything here came from real points where we got stuck on real projects; instead of keeping it to ourselves, we share it in the hope someone else can use it too.

If it helped with something of yours, we'd love to hear about it.

---

<div align="center">

### 🤝 Contributing

Issues, ideas, patches — welcome in each package's own repo.
Hit a gap that fits our principles? Open an issue. The next weld might be yours.

<br/>

[![All repos](https://img.shields.io/badge/All_repos-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/orgs/weldist/repositories)
[![Packagist](https://img.shields.io/badge/Packagist-F28D1A?style=for-the-badge&logo=packagist&logoColor=white)](https://packagist.org/packages/weldist/)
[![weld.ist](https://img.shields.io/badge/weld.ist-0ea5e9?style=for-the-badge&logo=googlechrome&logoColor=white)](https://weld.ist)

<sub>MIT licensed · With our mind and heart</sub>

</div>
