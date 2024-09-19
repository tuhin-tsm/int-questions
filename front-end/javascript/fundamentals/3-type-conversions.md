### String conversion

```javascript
let value = true;
console.log(typeof value); // boolean

value = String(value); // now value is a string "true"
console.log(typeof value); // string
```

### Numeric conversion

```javascript
let value = "123";

value = Number(value);
console.log(typeof value); // string
```

| Value       | Becomes...                                                                                                                                                       |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `undefined` | `NaN`                                                                                                                                                            |
| `null`      | 0                                                                                                                                                                |
| `true`      | 1                                                                                                                                                                |
| `false`     | 0                                                                                                                                                                |
| `string`    | The string is read “as is”, whitespaces (includes spaces, tabs \t, newlines \n etc.) from both sides are ignored. An empty string becomes 0. An error gives NaN. |
| " 123"      | 123                                                                                                                                                              |
| " 1 23"     | `NaN`                                                                                                                                                            |

### Boolean conversion

```javascript
Boolean(1); // true
Boolean(0); // false

Boolean("hello"); // true
Boolean(""); // false

//
Boolean("0"); // true
```
