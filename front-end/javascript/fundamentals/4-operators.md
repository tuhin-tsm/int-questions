### Nullish Coalescing Operator(??)

"Defined" -> Neither `null` nor `undefined`.

The result of `a ?? b` is:

- if `a` is defined, then a
- if `a` is not defined, then b

```javascript
let height = 0;
alert(height ?? 100); // 0
alert(height || 100); // 100
```

- The operator `??` has a very low precedence, only a bit higher than `?` and `=`, so consider adding parentheses when using it in an expression.
