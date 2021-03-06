# svgAnimation.js is a [Snap.svg](http://snapsvg.io) plugin used to create complex animations from simple SVGs
svgAnimation takes the complexity out of creating Snap.svg animations. Instead of animating in transform strings, callbacks, and milliseconds, svgAnimation allows us to use a simple JSON file to specify keyframes. With it, you can animate translate, rotate, and scaling transformations independently for any given element within an SVG. 

![example.gif](https://rawgit.com/hellomichael/svgAnimation/master/example.gif)

[View this example live in Codepen](http://codepen.io/hellomichael/pen/QNgZdx)

### Installation

In your HTML file, import Snap, svgAnimation, and any easing libaries. Both the minified and uncompressed (for development) versions are provided.

```js
<!-- Libraries -->
<script src="js/libs/snap.svg.min.js"></script>
<script src="js/libs/snap.svg.easing.min.js"></script>

<!-- Scripts -->
<script src="js/src/svgAnimation.min.js"></script>
```

## Use
To instantiate a new svgAnimation, use the following snippet.

```js
<script>
  (function() {
    var backpack = new svgAnimation({
      canvas:         new Snap('#canvas'),
      svg:            'svg/backpack.svg',
      data:           'json/backpack.json',
      duration:       2000,
      steps:          10
    });
  })();
</script>
```

## Options
* **canvas**:   Defines the Snap canvas that we'll drawing to, specified by a DOM id
* **svg**:      Defines the path of the SVG file
* **data**:     Defines the path of the JSON file
* **duration**: Defines the entire duration of an animation
* **steps**:    Defines the number of steps of an animation

### JSON File
The JSON file will hold the keyframes of our animation. A breakdown of the zipper animation is provided as an example. 

```json
{
  "animations": [
    {
      "id": "#zipper",
      "keyframes": {
        "translateKeyframes": [
          {
            "step": 6,
            "x": 90,
            "y": 0
          },

          {
            "step": 9,
            "x": 0,
            "y": 0,
            "easing": "easeOutQuint"
          }
        ],

        "rotateKeyframes": [
          {
            "step": 4,
            "angle": 45,
            "cy": "top"
          },

          {
            "step": 6,
            "angle": -45,
            "easing": "easeOutBack"
          },

          {
            "step": 8,
            "angle": 30,
            "easing": "easeOutQuint"
          },

          {
            "step": 10,
            "angle": 0,
            "easing": "easeOutBack"
          }
        ],

        "scaleKeyframes": [
          {
            "step": 4,
            "x": 0,
            "y": 0,
            "cy": "top"
          },

          {
            "step": 6,
            "x": 1,
            "y": 1,
            "easing": "easeOutBack"
          }
        ]
      }
    }
  ]
}
``` 

### To Do(s)
* Make event driven
* Add other SVG animatable properties (path animation, opacity, etc.)
* Add playback functionality (back, forwards, loop, etc.)

### Thanks
Thanks to Rey Bango, Chris Halaska, Matt Harwood, and Rhiana Chan for making this possible.