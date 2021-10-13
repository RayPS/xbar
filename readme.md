# bitbar

> Simplifies [BitBar](https://github.com/matryer/bitbar) app plugin creation

Create your plugin using a nice API instead of having to manually construct a big string.

*Requires BitBar 1.9 or higher.*

<img src="screenshot.png" width="232" height="196">

## Install

```sh
npm install bitbar
```

## Usage

```js
#!/usr/bin/env node --input-type=module
import bitbar, {separator, isDarkMode} from 'bitbar';

bitbar([
	{
		text: '❤',
		color: isDarkMode ? 'white' : 'red',
		dropdown: false
	},
	separator,
	{
		text: 'Unicorns',
		color: '#ff79d7',
		submenu: [
			{
				text: ':tv: Video',
				href: 'https://www.youtube.com/watch?v=9auOCbH5Ns4'
			},
			{
				text: ':book: Wiki',
				href: 'https://en.wikipedia.org/wiki/Unicorn'
			}
		]
	},
	separator,
	'Ponies'
]);
```

Create a file with the above code in the BitBar plugins directory and make sure to `chmod +x filename.js` it. [Read more.](https://github.com/matryer/bitbar#installing-plugins)

*Change `node` in `#!/usr/bin/env node` to the path of your Node.js binary. This is a [known issue](https://github.com/matryer/bitbar/issues/36) in BitBar.*

## API

### bitbar(items, options?)

#### items

Type: `Array<string | object>`

An item can be a string with the text or an object with the text in a `text` property and any of the `options`. The text can be multiple lines, but for the first item, only the first line will be shown in the menubar.

##### submenu

Type: `Array<string | object>`

It will add a submenu to the current item. A submenu is composed of an array of items.

#### options

Type: `object`

You can use any of the [supported options](https://github.com/matryer/bitbar#plugin-api).

Applies to all items unless overridden in the item.

### separator

Add a separator.

### isDarkMode

A boolean of whether macOS dark mode is enabled.
