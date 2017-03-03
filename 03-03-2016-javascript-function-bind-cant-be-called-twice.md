
Javascript Function.prototype.bind can't be called twice
========================================================

The `this` keyword in javascript may refer to

1. The caller, if your function is called in the format caller.func();
2. Whatever object is bound to it, if you call func.bind(obj);
3. window, the fallback if the previous don't apply.

Specifically about `2`, this is a trivial example:

```javascript
function getValue(){
    return this.value;
}

var returnsZero = getValue.bind({value: 0});
returnsZero();
// 0

```

One interesting thing is that you can't bind a function that has already been bound.
What is the result of this call bellow?

```javascript
var retunsTwo = getValue.bind({value: 2});
returnsTwo();
// 2
var returnsWhat = returnsTwo.bind({value: 3});
returnsWhat();
// 2
```

Yes, 2. Since returnsTwo has already been bound, it can't be bound again.

That's why if you pass a bound function as a event handler in jquery, it won't
rebind `this` to `event.currentTarget`, for example.

