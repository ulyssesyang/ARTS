# Share: Common Object operations in Javascript

Below are some tips for Object related operations by using Javascript.

## Protect the source data 对原始数据进行保护

Before you do any further operations on your source object data, the first thing you should do is protecting it, in case someone changes it in accident.

### Use `Const`

`Const` applies to bindings(variables) and creates an immutable binding.

```javascript
const object1 = {
  property1: 42
};
object1 = 33;
// Throws an error in strict mode
```

### Use `Object.freeze()`

`Object.freeze` makes object values immutable

```javascript

const object1 = {
  property1: 42
};

const object2 = Object.freeze(object1);

object2.property1 = 33;
// Throws an error in strict mode

console.log(object2.property1);
// expected output: 42
```

## Enumerate object 对象数据枚举

### use `for...in obj` loops

```javascript
var string1 = "";
var object1 = {a: 1, b: 2, c: 3};

for (var key in object1) {
  string1 += object1[key];
}

console.log(string1);
// expected output: "123"
```

### use `Object.keys(obj)`

```javascript
const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};

console.log(Object.keys(object1));
// expected output: Array ["a", "b", "c"]
```

### use `Object.getPropertyName(obj)`

```javascript
const object1 = {
  a: 1,
  b: 2,
  c: 3
};

console.log(Object.getOwnPropertyNames(object1));
// expected output: Array ["a", "b", "c"]
```

## Shallow copy object data 对象数据浅拷贝

Shallow copy is very straight forward, but only duplicate top-level properties of object data

### use `Object.assign`

```javascript
let obj = {
  a: 1,
  b: {
    c: 2,
  },
}
let newObj = Object.assign({}, obj);
console.log(newObj); // { a: 1, b: { c: 2} }
obj.a = 10;
console.log(obj); // { a: 10, b: { c: 2} }
console.log(newObj); // { a: 1, b: { c: 2} }
newObj.a = 20;
console.log(obj); // { a: 10, b: { c: 2} }
console.log(newObj); // { a: 20, b: { c: 2} }
newObj.b.c = 30;
console.log(obj); // { a: 10, b: { c: 30} }
console.log(newObj); // { a: 20, b: { c: 30} }
```

## Deep copy object data 对象数据深拷贝

Deep copy operation will do full copy of object properties

### use `JSON.parse(JSON.stringify(object))`

Note: The source object MUST be JSON safe

```javascript
let obj = { 
  a: 1,
  b: { 
    c: 2,
  },
}
let newObj = JSON.parse(JSON.stringify(obj));
obj.b.c = 20;
console.log(obj); // { a: 1, b: { c: 20 } }
console.log(newObj); // { a: 1, b: { c: 2 } }
```

### use recursive function call

Note: Write recursive function could be tricky in case of checking object property type, like Array, Function, etc

```javascript
function cloneObject(obj) {
    var clone = {};
    for(var i in obj) {
        if( Array.isArray(obj[i])) {
            clone[i] = obj[i].slice(0);
        } else if(obj[i] != null &&  typeof(obj[i])=="object")
            clone[i] = cloneObject(obj[i]);
        else
            clone[i] = obj[i];
    }
    return clone;
}
```

### use third party library like `lodash(Underscore)` library api or `jQuery` api

Note: in my opinion, use popular library to handle deep copy is the most effective way. There is a discussion on this topic in the StackOverFlow: [What is the most efficient way to deep clone an object in JavaScript?
](https://stackoverflow.com/questions/122102/what-is-the-most-efficient-way-to-deep-clone-an-object-in-javascript)

For example, `lodash.clonedeep` function, the source code covers some many edge cases, like checking nested property type, etc.

If someone already invents good wheel, then just use it!