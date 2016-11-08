# i-sticky

"position: sticky" jQuery plugin / polyfill.

<!-- MarkdownTOC autolink=true autoanchor=true bracket=round depth=0 -->

- [Limitations](#limitations)
- [Usage](#usage)
- [Methods](#methods)
- [Options](#options)
- [TODO](#todo)
- [License](#license)
- [Contributors](#contributors)
- [Examples in the wild](#examples-in-the-wild)
- [Changelog](#changelog)

<!-- /MarkdownTOC -->

<a name="limitations"></a>
## Limitations

- only vertical direction is supported
- if native position:sticky support is detected, and no `force` option is set, the plugin does nothing
- you shouldn't set `left` or `right` CSS properties on sticky positioned element
- you should set `top`, `bottom` or `margin-left` properties in pixels only
- parent block of position:sticky element MUST have position different from static (f.e., relative is a good choice)


<a name="usage"></a>
## Usage

jQuery is required (tested with 1.8.3 .. 1.10.2, should work with 1.7.0 or newer). Then write some JS:

```js
$('.i-sticky').iSticky();
```

You should write CSS rules by yourself, as you normally would. For example:

```css
/* sticky element */
.i-sticky {
    position: relative;
    position: -webkit-sticky;
    position: sticky;
    top: 0;
    height: 30px;
}
/* don't forget to change positioning of parent element */
.some-sticky-parent {
    position: relative;
}
```


<a name="methods"></a>
## Methods

Remove sticky style

```js
$('.i-sticky').iSticky('unstick');
```


<a name="options"></a>
## Options

- `holderClass`: sets up className for the placeholder element, which is created to hold original element's place in flow. Default value is `i-sticky__holder`.
- `holderAutoHeight`: when true, the plugin will recalculate placeholder's height. Otherwise, your CSS should define it. Defaults to `true`.
- `force`: applies the plugin even if the browser has native position:sticky support. May be useful for testing.
- `debug`: writes some info to browser's console.
- `fixWidth`: copies parent's width.
- `stuckClass`: class added when sticked

Example with options:

```js
$('.i-sticky').iSticky({
    holderClass:      'i-sticky__holder',
    holderAutoHeight: false
});
```

```css
/* if holderAutoHeight is off, don't forget to set some styles
   for the placeholder, generated by plugin */
.i-sticky + .i-sticky__holder {
    height: 30px;
}
```


<a name="todo"></a>
## TODO

- Position:sticky should not work if one of ancestors has overflow (auto/scroll/hidden) or overflow-x/overflow-y styles.
- Position:sticky should work as position:relative on table element.
- Plugin should set position:relative to stiky's parent.
- Margin-top & margin-bottom support.
- Crossbrowser testing, including native support tests and comparison with the plugin's behavior.


<a name="license"></a>
## License

MIT

- Copyright (c) 2014 Sergey Ermakov
- Copyright (c) 2016 REG.RU LLC


<a name="contributors"></a>
## Contributors

- [@podkot](https://github.com/podkot/)
- [@anagami](https://github.com/anagami/)
- [@DesTincT](https://github.com/destinct/)
- Initially based on [position--sticky- polyfill](https://github.com/matthewp/position--sticky-) by Matthew Phillips.


<a name="examples-in-the-wild"></a>
## Examples in the wild

[REG.COM domain checker](https://www.reg.com/choose/domain/?domains=position+sticky)


<a name="changelog"></a>
## Changelog

- 2016-11-08 2.2.2 transfering project to github/regru
- 2016-11-07 2.2.1 fixes. By @DesTincT
- 2016-11-07 2.2.0 `stuckClass` option. By @DesTincT
- 2016-03-26 2.1.0 `fixWidth` option.
- 2015-12-14 2.0.0 Rewritten to support both `top` & `bottom` at the same time. New `force` and `debug` options. `holderAutoHeight` defaults to `true`.
- 2015-06-15 1.1.8 Min-width issue. By @anagami.
- 2015-06-08 1.1.7 Test html pages. Positioning issue. By @anagami.
- 2015-06-04 1.1.6 Positioning issue. By @anagami.
- 2015-06-04 1.1.5 Holder is hidden when block is not sticked. Position issue. By @anagami.
- 2015-03-30 1.1.4 Firefox issue. By @anagami.
- 2015-03-30 1.1.3 Unstick issue. By @anagami.
- 2015-03-27 1.1.2 Small refactoring. By @anagami.
- 2015-03-27 1.1.1 Holder is removed when unstick. By @anagami.
- 2015-03-27 1.1.0 New 'unstick' method. By @anagami.
- 2014-10-08 1.0.0 Initial release.
