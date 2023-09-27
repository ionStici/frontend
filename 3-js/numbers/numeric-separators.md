[&larr; Back](./README.md)

# Numeric Separators

Numeric Separators (ES2021 features) - formatting numbers.

When representing a large number, we make it readable by using a comma separator:

`287460000000 = 287,460,000,000`

In JavaScript as well, we can make large numbers readable by using the new numeric separator.

Numeric separators are underscores `_` that we can place anywhere in our numbers.

`287_460_000_000 === 287460000000; // true`

When reading the number, the engine ignores these underscores. We can use underscores to give meanings to certain parts of our numbers: thousands, cents, etc.

### Restrictions where we can place the underscores:

- We can only place underscore between numbers.
- We can't place it at the beginning or at the end of a number.
- We can't place 2 underscores in a row.
- We can't convert strings to a number that contain underscores.

If you need to store a number in a string, for example in an API, or if you get a number as a string from an API, you should not use underscores in there, because JS will not be able to parse the number correctly out of that string. And the same is true with `parseInt` function - `parseInt('230_000') // 230` - instead of 230,000, it returned 230, only the parts in front of the underscore.

<br>
