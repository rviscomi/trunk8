trunk8
======

About
-----

**trunk8** is an intelligent text truncation extension to jQuery. When applied to a large block of text, trunk8 will cut off just enough text to prevent it from spilling over.

Unlike conventional truncation that just limits the character length of text, trunk8 measures the content area for spill-over and intelligently chooses the text that best fits in the given space.

Play with the [live demo](http://jrvis.com/trunk8/?rel=github).

*Bonus: [Global heatmap of trunk8 stargazers](http://jrvis.com/trunk8/stars.html).*

Usage
-----

**Default Settings**
```js
$('.too-long').trunk8(); // Lorem ipsum dolor sit amet, consect…
```

By default, trunk8 will add an ellipsis (`&hellip;`) after the truncated text.

**Method Invocation**
```js
$('.too-long').trunk8('update', new_string); // Lorem ipsum dolor sit amet, consect…
```

To invoke built-in trunk8 methods, supply the method name as a string. Method arguments are listed after the method name as necessary. See the section below entitled Methods for a full specification.

**Custom Settings**
```js
$('.too-long').trunk8({
    fill: '[snip]',
    side: 'center'
}); // Lorem ipsum dol[snip]id est laborum.
```

You may change the settings at any time by passing an object to trunk8. In the example above, the filler text is overwritten from an ellipsis to a custom string and the placement of the truncation is overwritten from the right side to the center. Continue reading the section below for a full list of customizable settings.

Settings
--------

* **fill** _(Default: '`&hellip;`')_ The string to insert in place of the omitted text. This value may include HTML.
* **lines** _(Default: `1`)_ The number of lines of text-wrap to tolerate before truncating. This value must be an integer greater than or equal to 1.
* **side** _(Default: `'right'`)_ The side of the text from which to truncate. Valid values include `'center'`, `'left'`, and `'right'`.
* **tooltip** _(Default: `true`)_ When true, the `title` attribute of the targeted HTML element will be set to the original, untruncated string. Valid values include `true` and `false`.
* **width** _(Default: `'auto'`)_ The width, in characters, of the desired text. When set to `'auto'`, trunk8 will maximize the amount of text without spilling over.

Public Methods
-------

**[Constructor]**
Initializes the settings and immediately truncates the targeted HTML element. This method is called when arguments are omitted and when the first argument is an object. When supplied with an object, trunk8 will merge the user-defined settings with the predefined settings object and immediately truncate the targeted HTML element with the custom settings.

```js
/* default settings */
$('.too-long').trunk8();

/* custom settings */
$('.too-long').trunk8({
   lines: 2
});
```

**update**
Updates the text value of the targeted HTML elements while maintaining truncation.

```js
/* Truncate the original text. */
$('.too-long').trunk8(); // Lorem ipsum...

/* Define the new text. */
var new_string = 'Torquent sollicitudin.';

/* Truncate the new text. */
$('.too-long').trunk8('update', new_string); // Torquent so...
```

**revert**
Reverts the text value of the targeted HTML elements to their untruncated states.

```js
$('.too-long').trunk8('revert'); // Torquent sollicitudin.
```

**getSettings**
Returns an object representation of the settings currently in effect. Because a return value is expected, this method does not promote the jQuery pattern of method chaining:

```js
/* good */
var setings = $('.too-long').trunk8('getSettings'); // {...}

/* bad */
$('.too-long').trunk8('getSettings').addClass('wrong'); // error
```

MIT License
-------
Copyright (c) 2012 Rick Viscomi (rviscomi@gmail.com)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
