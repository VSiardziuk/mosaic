0. Intro

To describe the tokens, we use [Style-Dictionary](https://amzn.github.io/style-dictionary/#/architecture)


1. Add Design Tokens to project

Copy the contents of the design-tokens folder to the style folder of your project.
For example, to the default-theme folder

```
.
`-- src/
    |-- app
    |-- assets
    |-- environments
    |-- styles/
    |   |-- default-theme/
    |   |   |-- components/
    |   |   |   |-- alert.json5
    |   |   |   |-- autocomplete.json5
    |   |   |   |-- badge.json5
    |   |   |   |-- button.json5
    |   |   |   `-- ...
    |   |   |-- properties/
    |   |   |   |-- aliases.json5
    |   |   |   |-- colors.json5
    |   |   |   |-- font.json5
    |   |   |   `-- ...
    |   |   |-- _palette.scss
    |   |   |-- _theme.scss
    |   |   |-- _typography.scss
    |   |   |-- _variables.scss
    |   |   |-- config.json5
    |   |   `-- css-tokens.css
    |   |-- _common.scss
    |   |-- _fonts.scss
    |   `-- _variables.scss
    |-- favicon.ico
    |-- index.html
    |-- styles.scss
    `-- main.ts
```

2. Include Design Tokens in ```styles.scss```

```scss
@import './styles/fonts';

@import '~@ptsecurity/mosaic/visual.scss';
@import '~@ptsecurity/mosaic-icons/dist/styles/mc-icons.css';
@import '~pt-product-icons/dist/styles/Product';

@include mosaic-visual();

// Include Design Tokens
@import './styles/default-theme/theme';

$typography: mc-typography-config();

// Include all typography for the components.
@include mc-core($typography);

@mixin app-theme($theme) {

    $background: map-get($theme, background);
    $foreground: map-get($theme, foreground);

    background: mc-color($background, background);
    color: mc-color($foreground, text);

    @include mosaic-theme($theme);
}

.theme-default {
    &.active-blue {

        // Include all theme styles for the mosaic components.
        @include app-theme($default-light-theme);
    }
}

```
