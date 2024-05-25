# Map

- The Map object holds key-value pairs and remembers the original insertion order of the keys.
- Any value (both objects and primitive values) may be used as either a key or a value.
- A **key** in the Map **may only occur once**; it is unique in the Map's collection.

Exmple:

```javascript
const map1 = new Map();

map1.set("a", 1);
map1.set("b", 2);
map1.set("c", 3);

console.log(map1.get("a"));
console.log(map1.size);
```

### Maps vs. Objects

<table class="standard-table">
  <thead>
    <tr>
      <th scope="row"></th>
      <th scope="col">Map</th>
      <th scope="col">Object</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Accidental Keys</th>
      <td>
        A <code>Map</code> does not contain any keys by default. It only
        contains what is explicitly put into it.
      </td>
      <td>
        <p>
          An <code>Object</code> has a prototype, so it contains default keys
          that could collide with your own keys if you're not careful.
        </p>
        <div class="notecard note">
          <p>
            <strong>Note:</strong> This can be bypassed by using
            <code>Object.create(null)</code>,
            but this is seldom done.
          </p>
        </div>
      </td>
    </tr>
    <tr>
      <th scope="row">Security</th>
      <td>
        A <code>Map</code> is safe to use with user-provided keys and values.
      </td>
      <td>
        <p>
          Setting user-provided key-value pairs on an <code>Object</code> may allow
          an attacker to override the object's prototype, which can lead to
          <a href="https://github.com/eslint-community/eslint-plugin-security/blob/main/docs/the-dangers-of-square-bracket-notation.md">
            object injection attacks
          </a>. Like the accidental keys issue, this can also be mitigated by using
          a <code>null</code>-prototype object.
        </p>
      </td>
    </tr>
    <tr>
      <th scope="row">Key Types</th>
      <td>
        A <code>Map</code>'s keys can be any value (including functions,
        objects, or any primitive).
      </td>
      <td>
        The keys of an <code>Object</code> must be either a
        <code>String</code> or a <code>Symbol</code>.
      </td>
    </tr>
    <tr>
      <th scope="row">Key Order</th>
      <td>
        <p>
          The keys in <code>Map</code> are ordered in a simple, straightforward
          way: A <code>Map</code> object iterates entries, keys, and values in
          the order of entry insertion.
        </p>
      </td>
      <td>
        <p>
          Although the keys of an ordinary <code>Object</code> are ordered now.
        </p>
      </td>
    </tr>
    <tr>
      <th scope="row"><p>Size</p></th>
      <td>
        The number of items in a <code>Map</code> is easily retrieved from its
        <code>Map.prototype.size</code> property.
      </td>
      <td>
        Determining the number of items in an <code>Object</code> is more roundabout and less efficient. A common way to do it is through <code>Object.keys(obj).length<c/ode>
      </td>
    </tr>
    <tr>
      <th scope="row">Iteration</th>
      <td>
        A <code>Map</code> is an iterable,  so it can be directly iterated.
      </td>
      <td>
        <p>
          <code>Object</code> does not implement an iteration protocol, and so objects are not directly iterable using the JavaScript <code>for...of</code> statement (by default).
        </p>
      </td>
    </tr>
    <tr>
      <th scope="row">Performance</th>
      <td>
        <p>
          Performs better in scenarios involving frequent additions and removals
          of key-value pairs.
        </p>
      </td>
      <td>
        <p>
          Not optimized for frequent additions and removals of key-value pairs.
        </p>
      </td>
    </tr>
    <tr>
      <th scope="row">Serialization and parsing</th>
      <td>
        <p>No native support for serialization or parsing.</p>
      </td>
      <td>
        <p>
          Native support for serialization from <code>Object</code> to
          JSON, using <code>JSON.stringify()</code>.
        </p>
        <p>
          Native support for parsing from JSON to <code>Object</code>,
          using <code>JSON.parse()</code>.
        </p>
      </td>
    </tr>
  </tbody>
</table>
