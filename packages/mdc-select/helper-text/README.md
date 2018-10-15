<!--docs:
title: "Select Helper Text"
layout: detail
section: components
excerpt: "The helper text provides supplemental information and/or validation messages to users"
iconId: menu
path: /catalog/input-controls/select-menus/
-->

# Select Helper Text

Helper text gives context about a select, such as how the selection will be used. It should be visible either persistently or only on focus.

## Design & API Documentation

<ul class="icon-list">
  <li class="icon-list-item icon-list-item--spec">
    <a href="https://material.io/go/design-selects">Material Design guidelines: Text Fields</a>
  </li>
  <li class="icon-list-item icon-list-item--link">
    <a href="https://material-components.github.io/material-components-web-catalog/#/component/select">Demo</a>
  </li>
</ul>


## Basic Usage

### HTML Structure

```html
<p class="mdc-select-helper-text" aria-hidden="true">
```

> NOTE: Make sure there are no white-space characters before helper text content.

### Styles

```scss
@import "@material/select/helper-text/mdc-select-helper-text";
```

### JavaScript Instantiation

```js
import {MDCSelectHelperText} from '@material/select/helper-text';

const helperText = new MDCSelectHelperText(document.querySelector('.mdc-select-helper-text'));
```

#### Accessibility

Note that in every example where the helper text is dependent on the state of the input element, we
assign an id to the `mdc-select-helper-text` element and set that id to the value of the
`aria-controls` and `aria-describedby` attributes on the input element. We recommend doing this as well as it will help
indicate to assistive devices that the display of the helper text is dependent on the interaction with
the select element.

```html
<div class="mdc-select">
  <input type="text" id="username" class="mdc-select__input"
         aria-controls="username-helper-text"
         aria-describedby="username-helper-text">
  <label for="username" class="mdc-floating-label">Username</label>
  <div class="mdc-line-ripple"></div>
</div>
<p id="username-helper-text" class="mdc-select-helper-text" aria-hidden="true">
  This will be displayed on your public profile
</p>
```

When using our vanilla JS component, if the browser sees that the input element has an `aria-controls`
attribute, it will look for an element with the id specified and treat it as the Select's helper
text element, taking care of adding/removing `aria-hidden` and other accessibility attributes. Adding
and removing classes and attributes to the helper text element can also be done using the
MDCTextFieldHelperText API, which is described below.

## Style Customization

### CSS Classes

CSS Class | Description
--- | ---
`mdc-select-helper-text` | Mandatory.
`mdc-select-helper-text--persistent` | Makes the helper text permanently visible.
`mdc-select-helper-text--validation-msg` | Indicates the helper text is a validation message.

### Sass Mixins

Mixin | Description
--- | ---
`mdc-select-helper-text-color($color)` | Customizes the color of the helper text following a text-field.
`mdc-select-helper-text-validation-color($color)` | Customizes the color of the helper text when it's used as a validation message.

## `MDCTextFieldHelperText` Properties and Methods

Property | Value Type | Description
--- | --- | ---
`foundation` | `MDCTextFieldHelperTextFoundation` | Returns the helper text's foundation. This allows the parent `MDCTextField` component to access the public methods on the `MDCTextFieldHelperTextFoundation` class.

## Usage Within Frameworks

If you are using a JavaScript framework, such as React or Angular, you can create a Helper Text for your framework. Depending on your needs, you can use the _Simple Approach: Wrapping MDC Web Vanilla Components_, or the _Advanced Approach: Using Foundations and Adapters_. Please follow the instructions [here](../../../docs/integrating-into-frameworks.md).

### `MDCTextFieldHelperTextAdapter`

Method Signature | Description
--- | ---
`addClass(className: string) => void` | Adds a class to the helper text element.
`removeClass(className: string) => void` | Removes a class from the helper text element.
`hasClass(className: string) => boolean` | Returns true if classname exists for the helper text element.
`setAttr(attr: string, value: string) => void` | Sets an attribute with a given value on the helper text element.
`removeAttr(attr: string) => void` | Removes an attribute on the helper text element.
`setContent(attr: string) => void` | Sets the text content for the helper text element.

### `MDCTextFieldHelperTextFoundation`

Method Signature | Description
--- | ---
`setContent(content: string) => void` | Sets the content of the helper text.
`setPersistent(isPersistent: boolean) => void` | Sets the helper text as persistent.
`setValidation(isValidation: boolean) => void` | Sets the helper text as a validation message.
`showToScreenReader() => void` | Makes the helper text visible to the screen reader.
`setValidity(inputIsValid: boolean) => void` | Sets the validity of the helper text based on the input validity.
