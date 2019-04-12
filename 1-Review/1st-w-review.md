# Review: JavaScript essentials: why you should know how the engine works

[JavaScript essentials: why you should know how the engine works](https://medium.freecodecamp.org/javascript-essentials-why-you-should-know-how-the-engine-works-c2cc0d321553) is really a great article which explains why good JS coding and strict typing like typescript can greatly benefit application performances.

## Two codes examples

The article starts with two codes which have different object data input. The data shape of first codes are all similar; while the second one is not. The test result ends up with first one 8 times faster than the second one.

## V8 engine optimization

Then article start to explain the reason causing the performance difference: V8 engine optimization of using `inline caching`. When codes object data has all same shape, then it has the best performance because: 

``` note
Inline Caching eliminates the expensive lookup for a property’s memory location. It works best when, at each property access, the object has the same object shape. This is called monomorphic IC.
```

In conclusion, Javascript dynamic features come with cost. In order to reduce such cost and get best performance introduced by V8 engine or other JS engine, we can use JS best practices, ES6 class, Typescript to get strict typing translator, uniform object data transformer, etc.