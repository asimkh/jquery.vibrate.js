> Does my Device Support the API?

The vibration API is implemented in `navigator.vibrate`. So calling the function makes your phone vibrate. You can test if your browser is recent enough to have the `vibrate` function in `navigator`.

Mozilla had their own implementation `mozVibrate` so some browsers may support that instead.

```javascript
var canVibrate = "vibrate" in navigator || "mozVibrate" in navigator;

if (canVibrate && !("vibrate" in navigator))
    navigator.vibrate = navigator.mozVibrate;
```

However, this doesn't mean that your device can vibrate. Just that it's recent enough. There are a few requirements you need to meet.

1. You need the hardware for it. 
2. The page needs to be visible.
3. Browser-specific implementation prevents the vibration.

*** 

Usage
-----

### jquery.vibrate.js

> Download and embed the code then initialize in one of the following ways.

```javascript
// Vibration for 50ms on all .button on click
$(".button").vibrate();

// Vibrate for 20ms on click
$(".button").vibrate("short");

// Vibrate for 50ms on click
$(".button").vibrate("medium");
$(".button").vibrate("default");
$(".button").vibrate(50);

// Vibrate for 100ms on click
$(".button").vibrate("long");

// Vibrate for 40ms on touchstart
$(".button").vibrate({
    duration: 40,
    trigger: "touchstart"
});
```