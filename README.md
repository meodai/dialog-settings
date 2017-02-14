```scss
$module-name: 'somerandommodule';

@include settings((
  gutter         : 1rem,
  color          : silver,
  color-contrast : gold
));

.#{$module-name} {
  padding: setting('gutter');
  &__submodule {
    color: setting(color);
  }
}
```
