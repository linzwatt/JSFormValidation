# JSFormValidation
Small and simple JavaScript library for form validation, one line of JavaScript to enable validation on a form, and declare validation paramaters inline in HTML.

JQuery not required.

FormValidation takes the form element as it's only parameter and provides full validation
of that form asuming that the form has been setup correctly.
Each form input that requires validation must have a `data-validation` attribute.
`data-validation` attribute can contain any number of the below properties, sepparated by a single space

 - `req`
 - `len:<min>-<max>`
 - `regex:<pattern_name>`
 - `match:<name_of_input_to_match>`
 - `radio:<shared_name_of_radio_buttons>`
 - `checkbox:<shared_name_of_checkboxes>:<min_checked>:<max_checked>`
 - `select`
 - `select-req`

eg.
```html
<input name='username' type='text' data-validation='req len:5-16 regex:letters'>
```

This input above will not appear valid until the field contains characters (req),
satisfies 5 < length < 16 (len:5-16), and matches the letters regex (regex:letters).

Each input with a data-validation attribute also needs a matching `<span>` located somewhere
near the input. The span must have an id of `input_name + "-status"`

eg.
```html
<span class="status" id="username-status"></span> for the input example shown above
```

This span will display an error to the user. The span will gain a class of `'status-error'`
when there is an error message and a class of `'status-success'` if the input is valid. These styles can be defined in
CSS, perhaps red for an error and green for a success.

FormValidation automatically finds the submit button and sets its `'disabled'` property true unless all fields are valid.
