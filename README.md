# WP Packages Changelog Action

[![Follow Roots](https://img.shields.io/badge/follow%20@rootswp-1da1f2?logo=twitter&logoColor=ffffff&message=&style=flat-square)](https://twitter.com/rootswp)
[![Sponsor Roots](https://img.shields.io/badge/sponsor%20roots-525ddc?logo=github&style=flat-square&logoColor=ffffff&message=)](https://github.com/sponsors/roots)

Automatically comment WordPress plugin changelogs on pull requests when [WP Packages](https://wp-packages.org/) dependencies change in your `composer.lock`.

## Support us

We're dedicated to pushing modern WordPress development forward through our open source projects, and we need your support to keep building. You can support our work by purchasing [Radicle](https://roots.io/radicle/), our recommended WordPress stack, or by [sponsoring us on GitHub](https://github.com/sponsors/roots). Every contribution directly helps us create better tools for the WordPress ecosystem.

## Features

- Detects changes to [WP Packages](https://wp-packages.org/) plugins in `composer.lock`
- Fetches changelogs from WordPress.org API
- Warns about unstable versions when installed version > WP.org's stable tag for the plugin

## Usage

### Basic Setup

Create a workflow file in your repository (e.g., `.github/workflows/wp-packages-changelog.yml`):

```yaml
name: WP Packages Changelog

on:
  pull_request:
    paths:
      - 'composer.lock'

jobs:
  changelog:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      pull-requests: write
    steps:
      - name: Comment changelogs on PR
        uses: roots/wp-packages-changelog-action@v3
```

## Example Comment

The action creates a formatted comment like this:

> # 🔌 WordPress Plugin Changelogs
>
> ## woocommerce (v10.2.0)
>
> > ⚠️ **Warning:** Installing version 10.2.0 but stable tag is 10.1.2. This may be an unstable version.
>
> <details>
> <summary>View changelog</summary>
>
> #### 10.2.2 2025-09-29
> **WooCommerce**
> - Fix - Check if template part is from file system before building the result from file #61171
> - Fix - Fix low-resolution images displayed in the Classic Template block gallery #61182
> - Fix - Make legacy gallery filters available while rendering blocks #61173
>
> [View full changelog on WordPress.org](https://wordpress.org/plugins/woocommerce/#developers)
>
> </details>

## Community

Keep track of development and community news.

- Join us on Discord by [sponsoring us on GitHub](https://github.com/sponsors/roots)
- Join us on [Roots Discourse](https://discourse.roots.io/)
- Follow [@rootswp on Twitter](https://twitter.com/rootswp)
- Follow the [Roots Blog](https://roots.io/blog/)
- Subscribe to the [Roots Newsletter](https://roots.io/subscribe/)
