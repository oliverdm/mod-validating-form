# odm-validating-form

A container for `paper-input-decorator` or `input` elements that validates contained inputs when the form is submitted.
Implemented as web component using [Google Polymer](https://www.polymer-project.org).

### Features

 * Validates all input elements when the form is submitted
 * Validates input elements individually when `change` event is triggered
 * Prevents resubmission of the form

### Demo
[Simple form with paper-input-decorator and input elements](http://oliverdm.github.io/odm-validating-form/demo.html)

### Example

```
<odm-validating-form inputSelector="paper-input-decorator"
                     submitSelector="#submitBtn"
                     on-submit="{{ formSubmit }}">
    
  <paper-input-decorator label="Required field" error="Please enter a value">
    <input is="core-input" type="text" value="" required>
  </paper-input-decorator>
    
  <paper-input-decorator label="Optional field">
    <input is="core-input" type="text" value="">
  </paper-input-decorator>
    
  <button id="submitBtn">Submit</button>
  
</odm-validating-form>
...
Polymer({
  
  formSubmit: function(){
    // form is valid and submitted
  }
  
});
```

### API

More documentation in the source code...

##### `disabled` (property)

Enables or disables the form.
Disabled forms cannot be submitted.
Does not change disabled state of input elements.

##### `inputSelector` (property)

CSS selector that selects one or more input elements that are going to be validated.
Required.

Note: `paper-input-decorator` and `input` should not be used together in one selector as it can result in duplicate selection of `input` elements underlying `paper-input-decorator`.

##### `submitSelector` (property)

CSS selector that selects a single element that triggers a `tap` event to signal form submission, `button` or `paper-button` for example.
Required.

##### `invalidClass` (property)

Optional class name that is added to each input element that fails validation (and removed if it passes).

##### `clearErrors()` (method)

Removes `invalidClass` from all input elements and sets `paper-input-decorator.isInvalid = false`.
Does not change the actual value of the input.

##### `submit` (event)

Fired when the form is valid and submitted.
