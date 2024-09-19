### Script Tag

The benefit of a separate file is that browser will download it and store it in its cache. Other pages that reference the same script will take it from the cache instead of downloading it, so the file is actually downloaded only once.

If `src` is set, the script content is ignored

### Automatic semicolon doesn't happen always

```
alert("Hello")
[(1, 2)].forEach(alert);
```

### "use strict" directive

JavaScript's strict mode is a way to opt in to a restricted variant of JavaScript, thereby implicitly opting-out of "sloppy mode".

```javascript
"use strict";

num = 5; // error: num is not defined
```
