# Passing by value and by reference
---

```javascript
var myObject = {
  price: 20.99,
  get_price: function() {
    return this.price;
  }
};

var customObject = Object.create(myObject);
customObject.price = 19.99;
delete customObject.price;
console.log(customObject.get_price());
```


**Explanation:**
In this code snippet, we create an object `myObject` with a `price` property set to `20.99` and a `get_price` method that returns the value of `price` using `this`.


We then create a new object `customObject` using `Object.create(myObject)`, which establishes a prototype chain where `customObject` inherits properties and methods from `myObject`.

Next, we explicitly set the `price` property of `customObject` to `19.99`. However, we then delete the `price` property from `customObject` using `delete customObject.price`.

When we call `customObject.get_price()`, it attempts to retrieve the `price` property from `customObject`. Since `customObject` no longer has its own `price` property after deletion, it looks up the prototype chain and finds the `price` property in `myObject`. Thus, `customObject.get_price()` returns `20.99`.

Therefore, when we log the result of `customObject.get_price()`, it prints `20.99` to the console.

In case we execute 
```javascript
var myObject = {
  price: 20.99,
  get_price: function() {
    return this.price;
  }
};

var customObject = Object.create(myObject);
customObject.price = 19.99;
// delete customObject.price;
console.log(customObject.get_price());
```
It will log `19.99`.