![dialog(settings)](media/logo.png)

# dialog(settings) :book:

[![GitHub version](https://badge.fury.io/gh/meodai%2Fdialog-settings.svg)](https://badge.fury.io/gh/meodai%2Fdialog-settings)
[![npm version](https://badge.fury.io/js/dialog-settings.svg)](https://badge.fury.io/js/dialog-settings)
[![travis build](https://api.travis-ci.org/meodai/dialog-settings.svg?branch=master)](https://travis-ci.org/meodai/dialog-settings)

A simple key value store for module settings, to make modules more portable.
With the nice side-effect that all settings can be rendered as native CSS variables. Play with the [demo](http://www.sassmeister.com/gist/230dc13729262d55d92f1efbcd2a69a5).

## Why ⁉️️
1. Easy way to switch between rendered values and CSS variables.
2. Better portabily: Only have to rename one string, not tons of variable names as well, when renaming/moving a module.
3. Warn when variables are missing instead of failing the build. Allows to mock the CSS for a module withought knowing the values for each property.

### Before
```scss
$module-name: 'mymodule';

$mymodule-background: $colors-dark;
$mymodule-color: $colors-contrast;
$mymodule-margin: 2rem;

.#{$module-name} {
  color: $mymodule-color;
  background: $mymodule-background;
  margin: $mymodule-margin;
}
```
### With dialog(settings)
```scss
$module-name: 'mymodule';

@include settings((
  color: $colors-dark,
  background: $colors-contrast,
  margin: 2rem
));

.#{$module-name} {
  color: setting(color);
  background: setting(background);
  margin: setting(margin);
}
```
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

2. Setup your module by setting a name-space and calling the setting mixin
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

4. By setting the global variable `$module-cssvariables` the variable are rendered as `CSS` variables.

## Usage with [node-sass-json-importer](https://github.com/Updater/node-sass-json-importer)
 
It can be usefull to store design settings in a seperate file, to create a nice API with the designer.
Using [node-sass-json-importer](https://github.com/Updater/node-sass-json-importer) settings can be stored in a `JSON` file.

**module-design-specs.json**
```JSON
{
  "settings": {
    "background-color": "#fff",
    "stack": "1rem",
    "color": "#212121"
  }
}
```

**module.scss**
```scss
@import 'module-design-specs.json';
@include settings($settings);
.module {
  color: setting(color);
  background: setting(background-color);
  margin-bottom: setting(stack);
}
```


## License 👮🏼

Created with ♥ by [meodai](//github.com/meodai). Licensed under the [MIT License](LICENSE).
