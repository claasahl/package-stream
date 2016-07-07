# package-stream

An endless stream of [clean package data](http://npm.im/nice-package) from the npm registry.

See also [all-the-packages](https://github.com/zeke/all-the-packages), a similar
package designed for offline use.

## Installation

```sh
npm install package-stream --save
```

## Usage

The stream is an event emitter that emits two events: `pkg` and `up-to-date`.
The `up-to-date` event is emitted when the stream reaches the end of all
existing packages, but unlike typical read streams, this stream has no `end`
event. It remains open indefinitely, emitting `package` events as new package
versions are published to the npm registry in real time.

```js
var registry = require('package-stream')()

registry
  .on('package', function (pkg) {
    // nice clean package object
  })
  .on('up-to-date', function (pkg) {
    // consumed all changes (for now)
    // The stream will remain open and continue receiving package
    // updates from the registry as they occur in real time.
  })
```

Each package instance has convenience methods like `pkg.dependsOn(pkgName)`
and `pkg.mentions(query)`. To see the full list, check out the
[nice-package documentation](https://github.com/zeke/nice-package/blob/master/README.md#convenience-methods).

## Tests

```sh
npm install
npm test
```

## Dependencies

- [changes-stream](https://github.com/jcrugzz/changes-stream): Simple module that handles getting changes from couchdb
- [got](https://github.com/sindresorhus/got): Simplified HTTP requests
- [nice-package](https://github.com/zeke/nice-package): Clean up messy package metadata from the npm registry

## Dev Dependencies

- [tap-spec](https://github.com/scottcorgan/tap-spec): Formatted TAP output like Mocha's spec reporter
- [tape](https://github.com/substack/tape): tap-producing test harness for node and browsers
## License

MIT

_Generated by [package-json-to-readme](https://github.com/zeke/package-json-to-readme)_
