# pull-delayed-sink

return a pull-stream sink, that won't start reading until you say.

## Example

``` js
var delayed = require('pull-delayed-sink')
var feed = [], d

//create a pull stream, and direct to nowhere yet!
pull(pull.values(feed), d = delayed())


//... later, start the sink.
setTimeout(function () {
  feed.push(1, 2, 3)

  d.start(pull.collect(function (err, ary) {
    if(err) throw err
    t.deepEqual(ary, [1, 2, 3])
    t.end()
  }))
})

```

`pull.defer` is a similar function, but it's a source instead of a sink.


## API

### d = delayed(); d.start(sink)

create a fake sink stream, and then start it when you have the sink you want.

### d = delayed(sink); d.start()

make a sink delay, and then allow it to start.

## License

MIT
