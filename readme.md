# Phurix Laravel 12 compatibility fork

This branch is maintained as `phurix/html` for the Phurix portal. It preserves the `Collective\Html` namespace and Form/Html facades while targeting Laravel 12 and PHP 8.2 or newer. Support and issue tracking are in this repository; upstream LaravelCollective is abandoned. The original MIT licence and credits are retained below. This compatibility branch does not change the older Laravel 11 branch used by existing deployments.

## Laravel 12 release lane

PR #1 targets the dedicated `12.x` branch. The `6.x-laravel-11` branch remains at its existing Laravel 11 implementation; merging the Laravel 12 change must not replace that legacy branch.

Proposed first release: `v12.0.0` as `phurix/html`, retaining the Collective namespace and Form/Html discovery aliases. After review and merge into `12.x`, tag the reviewed merge commit, rather than the unreviewed feature head. Do not add a manual version to composer.json or move an existing tag.

Composer derives a VCS package's name from the repository default branch. The current default `6.x` still identifies `laravelcollective/html`, so a tag alone is insufficient. Before publication, coordinate the package-identity transition and make the reviewed `12.x` branch the default; verify a fresh Composer cache resolves `phurix/html` at `v12.0.0`. Existing locked Laravel 11 installations retain their pinned source revision, but fresh legacy VCS resolution under the old package name can change after this switch. Audit/migrate those consumers or explicitly freeze their dependency updates during the transition. Preserving the branch alone does not preserve Composer's old name discovery.

The portal should then require `phurix/html: ^12.0` through the normal public VCS repository, remove its root package metadata and its old `laravelcollective/html` requirement, and regenerate the lockfile from the release. Never install both namespace providers. Packagist registration may replace the VCS entry later, but is not assumed to exist. Validate package discovery, existing rendered forms, Composer audit and the portal's isolated suite before approving adoption.

PHP 8.2/8.3/8.4 compatibility is covered by the package CI matrix. The inherited `strftime` deprecation remains visible; changing locale/date formatting behaviour is separate work. No default-branch switch, tag publication or deployment is performed by preparing this release lane.

![LaravelCollective HTML](LaravelCollectiveHTML-banner.png)

[![Build Status](https://travis-ci.org/LaravelCollective/html.svg)](https://travis-ci.org/LaravelCollective/html)
[![Total Downloads](https://poser.pugx.org/LaravelCollective/html/downloads)](https://packagist.org/packages/laravelcollective/html)
[![Latest Stable Version](https://poser.pugx.org/LaravelCollective/html/v/stable.svg)](https://packagist.org/packages/laravelcollective/html)
[![Latest Unstable Version](https://poser.pugx.org/LaravelCollective/html/v/unstable.svg)](https://packagist.org/packages/laravelcollective/html)
[![License](https://poser.pugx.org/LaravelCollective/html/license.svg)](https://packagist.org/packages/laravelcollective/html)

Official documentation for Forms & Html for The Laravel Framework can be found at the [LaravelCollective](https://laravelcollective.com/docs) website.

## Replacement
If you're looking to replace this package due to it's retirement we recommend using [Shift](https://laravelshift.com/convert-laravelcollective-html-to-spatie-laravel-html)
