# Control Flow: Operators

## Learning Goals

- Use common comparison methods for control flow (`==`, `!=`, `>`, `<`)
- Use common operators for control flow (`&&`, `||`, `!`, `?:`)
- Understand the differences in syntax between Ruby and JavaScript

## Introduction

Just like JavaScript, Ruby has several ways we can control the flow of execution
in our programs:

- We can use conditional statements like `if/else` and `switch/case`
- We can use looping constructs like `loop` (Ruby) and `while` (JavaScript)

Using these control flow constructs means we're taking our code out of the
normal flow of execution (top-to-bottom, one line at a time) and instead
providing some instructions to change that order. As you've surely seen in
JavaScript, conditional statements and loops are critical for writing
applications.

In the next series of lessons, we'll explore common approaches to control flow,
and learn some new syntax that is unique to Ruby.

## Conditional Operators

In general, using control flow in any language means running certain code **if
some condition is met**. That means that in order to use control flow
effectively, it's important to be know how to use conditional operators to
compare values.

## Comparison Operators

In Ruby, many built-in classes have the following methods that can be used to
compare two values:

- `>`: greater than
- `>=`: greater than or equal to
- `<`: less than
- `<=`: less than or equal to
- `==`: equal to
- `!=`: not equal to

Unlike in JavaScript, the `==` method in Ruby **will not coerce strings to
numbers** before comparing them, or perform some of the other type coercions
that JavaScript does. For example, in JavaScript, using the `==` operator can
lead to some strange behavior:

```js
"1" == 1
// => true
0 == []
// => true
[] == ![]
// => true 🤔
```

In Ruby, the `==` method checks if the objects on both sides are considered the
equivalent values:

```rb
"1" == 1
# => false
1 == 1
# => true
```

There are some differences between Ruby's `==` and JavaScript's `===` though. In
JavaScript, the `===` operator checks if both objects have the same identity,
i.e. refer to the same space in memory. For example, in JavaScript, this example
returns `false` because the two arrays are unique objects in memory:

```js
[1, 2, 3] === [1, 2, 3];
// => false
```

In Ruby, this example returns `true` because Ruby considers these to have
equivalent values:

```rb
[1, 2, 3] == [1, 2, 3]
# => true
```

Ruby will also check if an Integer has the equivalent value to a Float, even
though they're technically different data types:

```rb
1.0 == 1
# => true
```

The reason for this is because in Ruby, the `==` operator is actually a _method_
that has unique behavior that **depends on which class the method is defined
in**! The code above is equivalent to the following method call:

```rb
1.0.==(1)
```

Because Ruby is heavily favors object-orientation as a language, you'll find
that many features other languages would define as operators (like `==`, `>`,
even math operators like `+` and `*`) are actually methods. If you're unsure
what these methods do in a particular scenario, check the class definition in
the documentation for the data type on the left-hand side of the `==` (for
example, here is the documentation for the [Array class][array ==] and the
[Integer class][integer ==]).

[array ==]: https://ruby-doc.org/core-2.7.3/Array.html#method-i-3D-3D
[integer ==]: https://ruby-doc.org/core-2.7.3/Integer.html#method-i-3D-3D

> **Note**: While Ruby does have a `===` method, **it is not used the same way
> as it is in JavaScript**. There are very few scenarios when you want to use
> the `===` method in Ruby; in general, for comparing data, you want to use the
> `==`. [See here for examples][ruby ===] if you're curious about what this
> method does.

[ruby ===]: https://stackoverflow.com/questions/3422223/vs-in-ruby/3422349#3422349

## Logical Operators

Ruby has the same logical operators you'll find in many other languages,
including JavaScript:

- `&&`: Logical **and**. Are both values truthy?
- `||`: Logical **or**. Is one or the other value truthy?
- `!`: **not**. Coerces the data to its boolean equivalent, then reverses it
  (`true` becomes `false`, and vice versa).

```rb
true && true
# => true
false && true
# => false
true || true
# => true
false || true
# false
!true
# false
!!true
# true
```

Ruby also has the ternary operator (`?:`) for writing an inline conditional
statement:

```rb
age = 1

age < 2 ? "baby" : "not a baby"
```

This is the equivalent of the following `if/else` statement:

```rb
age = 1
if age < 2
  "baby"
else
  "not baby"
end
```

## Conclusion

In the coming lessons, we'll be writing some methods that use control flow, so
make sure to keep these methods for comparing data in mind — they'll be
very important to your ability to write conditional logic and looping code
successfully!

## Resources

- [Ruby equality](https://www.rubyguides.com/2017/03/ruby-equality/)
- [Ruby operators](https://www.rubyguides.com/2018/07/ruby-operators/)
