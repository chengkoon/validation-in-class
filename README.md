# validation-in-class
* What are different types of validations?
* Which ones could be useful?
* How do we use validations?

# what are different types of validations?
client side
 regex for example
 plus point - able to validate quicker, and to prevent someone from flooding the server

server side
 schema for example
 plus point - a second layer of validation. it's not a bad idea to have more validations

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

Custom validators
If the built-in validators aren't enough, there's the custom ones - they are declared by passing a validation function.

For eg:
```js
var userSchema = new Schema({
      phone: {
        type: String,
        validate: {
          validator: function(v) {
            return /\d{3}-\d{3}-\d{4}/.test(v);
          },
          message: '{VALUE} is not a valid phone number!'
        },
        required: [true, 'User phone number required']
      }
    });
//OR

function dummyEmailValidator(candidate) {
  return candidate === 'mustBeThis@email.com'
}
var schema = mongoose.Schema({
  email: {
    type: String,
    required: true,
    validate: {
      dummyEmailValidator,
      'please enter the right email add'
    }
  }
})
```
# practice!
Create a Model with LOTS of validations, to demonstrate the possibilities. Test that it works by sending a POST request in postman/curl and return the errors.
