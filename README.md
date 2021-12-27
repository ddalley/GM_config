GM_config
=========
A library to help you set up configure in greasemonkey script.

**This project was forked from https://github.com/eight04/GM_config. You are encouraged to use that version
in your own projects. This version will make breaking changes without warning.**

Features
--------
* Create a dialog to show, edit settings.
* Reset settings to default.
* Save setting depends on different domains.
* Import, export settings.
	- Note: export function will only grab settings on current domain.
* Supported input type:
	- checkbox (boolean)
	- number (number)
	- text (string)
	- textarea (string)
	- radio (string)
	- select (string or array)

Demo
----

* [demo](https://rawgit.com/ddalley/GM_config/master/demo/demo.html)

API
---

### Methods

#### GM_config.init(scriptId, configDefinition)

##### scriptId

A unique ID that serves as a namespace for the script's settings

##### configDefinition

The definition is a map object look like:
```
{
	title: "title",
	fields: {
		key: {
			label: "the label of the input",

			// input type. could be text, number, checkbox, textarea, radio, or
			// select.
			type: "text",

			// could be String, Number, Boolean, or Array. See following example.
			default: "default value"
		}, ...
	}
}
```
Example Fields:
```
{
	text: {
		label: "Text field",
		type: "text",
		default: "a string"
	},
	number: {
		label: "Number field",
		type: "number",
		default: 12345
	},
	checkbox: {
		label: "Checkbox field",
		type: "checkbox",
		default: true
	},
	textarea: {
		label: "Textarea field",
		type: "textarea",
		default: "multi\nline"
	},
	radio: {
		label: "Select your language",
		type: "radio",
		default: "en",
		options: {
			en: "English",
			tw: "Traditional Chinese",
			cn: "Simplified Chinese"
		}
	},
	select: {
		label: "Choose a color",
		type: "select",
		default: "orange",
		options: {
			red: "Red",
			orange: "Orange",
			yellow: "Yellow"
		}
	},
	multipleSelect: {
		label: "Multiple select",
		type: "select",
		default: ["n1", "n3"],
		options: {
			n1: "1",
			n2: "2",
			n3: "3"
		},
		multiple: true
	}
}
```

#### GM_config.open()

Open config dialog.

#### GM_config.get([key])

If `key` is not setted, return a key-value map of the config.  
If `key` is a string, return the config value of the key.  
If `key` is an object, copy all properties from the config to the object.

### Properties

#### GM_config.onclose = function(saveFlag)

Called when the dialog is closed.

##### saveFlag

`true` if the user pressed "Save" button.

#### GM_config.onload = function

Called when the config is saved.

Build
-----
Using NodeJS, Bower, Grunt:
```
npm install
bower install
grunt
```

Todos
-----
* Create dialog with htmlString?
* Add `white-space: nowrap` to dialog footer.
* Refactor
	- Pull out createInput from createInputs.
	- Pull out grabDialogSetting from close.

License
-------
LGPL version 3 or any later version; http://www.gnu.org/copyleft/lgpl.html
