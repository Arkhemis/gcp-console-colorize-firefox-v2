gcp-console-colorize-firefox-v2
===

A Firefox (and Zen, LibreWolf, other Gecko browsers) build of [yfuruyama/gcp-console-colorize](https://github.com/yfuruyama/gcp-console-colorize), the extension that changes the header color of the GCP console per project.

e.g.) Change header color to red for a production project.

![screenshot](https://raw.github.com/yfuruyama/gcp-console-colorize/master/image/gcp-console-colorize.png)

## Why a v2

The previous Firefox port, [araigumaG/gcp-console-colorize-firefox](https://github.com/araigumaG/gcp-console-colorize-firefox), is no longer maintained and stopped working when the GCP console changed its header markup.

This fork tracks the official extension directly instead. The only differences are Firefox compatibility tweaks, so upstream fixes can be merged as-is:

- `manifest.json`: `background.scripts` alongside `background.service_worker` (Firefox does not support service workers for extensions; Chrome ignores `scripts`), plus `browser_specific_settings.gecko` for AMO signing.
- `icon/icon_16x16.png`: resized to a true 16x16, as AMO rejects non-square icons.

## Install

Download the signed `.xpi` from the [releases](https://github.com/Arkhemis/gcp-console-colorize-firefox-v2/releases), then in Firefox/Zen open `about:addons` → ⚙️ → *Install Add-on From File…*.

On first use, Firefox may ask you to allow the extension on `console.cloud.google.com` (Manifest V3 host permissions).

## Build

```sh
make package
```

produces `package.zip`, ready to upload to [AMO](https://addons.mozilla.org/developers/) for signing.

## Credits

Original extension by [yfuruyama](https://github.com/yfuruyama/gcp-console-colorize), first Firefox port by [araigumaG](https://github.com/araigumaG/gcp-console-colorize-firefox). Licensed under Apache 2.0.
