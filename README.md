![dialog(size)](media/logo.png)
# dialog(settings) :book:
[![GitHub version](https://badge.fury.io/gh/meodai%2Fdialog-size.svg)](https://badge.fury.io/gh/meodai%2Fdialog-size)
[![npm version](https://badge.fury.io/js/dialog-size.svg)](https://badge.fury.io/js/dialog-size)
[![travis build](https://travis-ci.org/meodai/dialog-size.svg?branch=master)](https://travis-ci.org/meodai/dialog-size)

A simple key value store for module settings, to make modules more portable.
With the nice side-effect that all settings can be output as native CSS variables.

## Installation 💾

```
npm install dialog-settings
```

## Basic usage ☝️

1. Import `dialog-settings.scss`

    ```scss
    @import 'dialog-settings/dist/dialog-settings';
    ```
    PS: make sure to add `node_modules` to your [import paths](https://github.com/sass/node-sass#includepaths)

2. Setup your module by setting a names-pace and calling the setting mixin
    ```scss
    $module-name: 'somerandommodule';

    @include settings((
      gutter         : 1rem,
      color          : silver,
      color-contrast : gold
    ));
    ```

3. Call the `setting()` function.

    ```scss
    .#{$module-name} {
      padding: setting('gutter');
      &__submodule {
        color: setting(color);
      }
    }
    ```

## License 👮🏼

Created with ♥ by [meodai](//github.com/meodai). Licensed under the [MIT License](LICENSE).
