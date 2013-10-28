# beats [![experimental](http://hughsk.github.io/stability-badges/dist/experimental.svg)](http://github.com/hughsk/stability-badges) #

A naive but generic beat-detection module.

## Usage ##

[![beats](https://nodei.co/npm/beats.png?mini=true)](https://nodei.co/npm/beats)

### `detect = require('beats')(bins[, minSeparation])` ###

Takes an array of `bins`, and an optional `minSeparation` value which
determines the minimum amount of time between beats for each bin (defaults to
0).

Each bin takes the following options:

``` javascript
{
  // the minimum index to sample in
  // the frequencies array.
    lo: 0
  // The maximum index to sample in
  // the frequencies array.
  , hi: 512
  // The minimum volume at which to
  // trigger a beat for this bin.
  , threshold: 0
  // the amount by which to decay
  // the threshold for this bin for
  // each sampled frame.
  , decay: 0.005
}
```

### `result = detect(frequencies[, dt])` ###

Returns a `Float32Array` containing the beats for the current frame: one
element per bin. If an element's value is 0, then there is no beat this frame.
Otherwise, the value will match the average volume of the bin's frequencies.

`frequencies` is an array of audio frequencies for the current frame. `dt` is
the amount of time between this frame and the last one - it defaults to 1.

## License ##

MIT. See [LICENSE.md](http://github.com/hughsk/beats/blob/master/LICENSE.md) for details.
