[&larr; Back](./README.md)

# JavaScript Numbers: Explanation

In JavaScript, numbers are represented internally as _floating point numbers_, always as decimals, no matter if we write them as integers or as decimals: `25 === 25.0`. That's the reason why we have only one data type for all numbers.

Numbers are represented internally in a _64 base 2 format_. This means that numbers are always stored in a binary format, they're only composed of zeros and ones.

In this binary form it is very hard to represent certain fractions that are easy to represent in the base 10 system that we are used to. Base 10 is the numbers from 0 to 9, while binary is base 2, the numbers 0 and 1.

So there are certain numbers that are hard to represent in base 2. One example of that is the fraction `0.1` which can lead to unexpected behaviors, for example: `0.1 + 0.2 = 0.3000000000004`. JavaScript simply does not have a better way of representing this number.

- In base 10 - `1/10 = 0.1` - easy to represent.
- But for example - `10 / 3 = 3.3333333` - hard to represent.

In binary, the same thing happens with `0.1`, we get an infinite fraction.

In some cases, JavaScript does some rounding behind the scenes to try to hide these problems, but some operations such as - `0.1 + 0.2` - simply cannot mask the fact that behind the scenes it cannot represent certain fractions. Many other languages use the same system, for example PHP or Ruby. We just have to accept that it works this way, because we really cannot do anything against this.

So just be aware that you cannot do like really precise scientific or financial calculations in JavaScript, because eventually, you will run into a problem like this - `0.1 + 0.2 === 0.3 // false` - which in reality is true. This is simply an error in JavaScript that we have to accept.

<br>
