# <a id=arc.json.puthref=#arc.json.put>`arc.json.put`</a>

```javascript
var arc = require('@smallwins/arc-prototype')

function handler(req, res) {
  res({
    json: {noteID: 1, body: 'hi'}
  })
}

exports.handler = arc.json.put(handler)
```

Things to understand:

- `arc.json.put` accepts one or more functions that follow Express-style middleware signature: `(req, res, next)=>`
- `req` is a plain object with `path`, `method`, `query`, `params`, and `body` keys
- `res` is a function that must be invoked with named params: 
  - `json` a plain `Object` value
  - or `location` with a URL value (a string starting w `/`)
  - `session` (optional) a plain `Object`
  - `status` (optional) HTTP error status code responses: `500`, `403`, or `404`
- `res` can also be invoked with an `Error`
  - optionally the `Error` instance property of `code`, `status` or `statusCode` can be one of `403`, `404` or `500` to change the HTTP status code
- `next` is an optional function to continue middleware execution
