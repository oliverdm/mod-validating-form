# odm-validating-form

A container for `input` or `paper-input` elements that validates inputs when the form is submitted.
Implemented as web component using [Google Polymer 1.0](https://www.polymer-project.org).

### Features

 * Validates all input elements when the form is submitted
 * Validates input elements individually when `change` event is triggered
 * Prevents resubmission of the form

### Demo & Example

[Demo](http://oliverdm.github.io/odm-validating-form/demo.html)

```
<odm-validating-form input-selector="paper-input-container"
                     submit-selector="#submitBtn"
                     on-submit="formSubmit">
    
  <paper-input-container>
    <label>Required field</label>
    <input is="iron-input" type="text" value="" required>
    <paper-input-error>Please enter a value</paper-input-error>
  </paper-input-decorator>
    
  <paper-input-container>
    <label>Optional field</label<
    <input is="iron-input" type="text" value="">
  </paper-input-container>
    
  <button id="submitBtn">Submit</button>
  
</odm-validating-form>
...
Polymer({
  is: 'my-custom-element',

  formSubmit: function(){
    // form is valid and submitted
  }
  
});
```

### API

All properties are also available as attributes of the element when the name is converted (camelCase to dash, e.g. `inputSelector -> input-selector`).
Only changes to the `disabled` property are reflected back to HTML.

More documentation is available in the source code.

##### `disabled` (property)

Enables or disables the form.
Disabled forms cannot be submitted.
Does not change disabled state of input elements.
Reflected back to HTML.

##### `inputSelector` (property)

CSS selector that selects one or more input elements that should be validated.
Required.

##### `submitSelector` (property)

CSS selector that selects a single element that triggers a `tap`-like event to signal form submission, `button` or `paper-button` for example.
Required.

##### `invalidClass` (property)

Optional class name that is added to each input element that fails validation (and removed if it passes).

##### `clearErrors()` (method)

Removes `invalidClass` from all input elements.
Does not change the value of the input.

##### `submit` (event)

Fired when the form is valid and submitted.
