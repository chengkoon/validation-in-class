# validation-in-class
* What are different types of validations?
* Which ones could be useful?
* How do we use validations?

# what are different types of validations?

# which ones could be useful?

# how do we use validations?
For SchemaTypes (String,Number,Date,Buffer,Boolean,Mixed,Objectid,Array), the built-in **required** validator can be used.
For **Numbers**, in addition to required; there is a **min** and **max** validator that caps the integer passed into the Schema.
For **Strings**, there are also  **enum**, **maxlength** and **minlength** validators.
max length and min length caps the length of the strings passed into the schema.

For eg:
```js
var breakfastSchema = new Schema({
    eggs: {
      type: Number,
      min: [6, 'Too few eggs'],
      max: 12
    },
    bacon: {
      type: Number,
      required: [true, 'Why no bacon?']
    },
    drink: {
      type: String,
      enum: ['Coffee', 'Tea']
    }
  });
```
# practice!
Create a Model with LOTS of validations, to demonstrate the possibilities. Test that it works by sending a POST request in postman/curl and return the errors.
