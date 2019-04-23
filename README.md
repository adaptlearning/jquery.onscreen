# jquery.onscreen
Inview replacement with extra functionality


## Usage

### Inview

The event will only fire when the element changes in its view state. It won’t keep firing if the user scrolls and the element remains in view.

`event`: jQuery event object.    
`isInView`: Indicates the visible state.  
`visiblePartX`: Detects which horizontal part of the element is visible to the user (possible values: left, right, both, none)  
`visiblePartY`: Detects which vertical part of the element is visible to the user (possible values: top, bottom, both, none)  

```js
$('div').on('inview', function(event, isInView, visiblePartX, visiblePartY) {
  if (!isInView) {
    // element has gone out of viewport
    return;
  }
  // element is now visible in the viewport
  if (visiblePartY == 'top') {
    // top part of element is visible
    return;
  } else if (visiblePartY == 'bottom') {
    // bottom part of element is visible
    return;
  }
  // whole part of element is visible
});

$('div').inview(function(event, isInView, visiblePartX, visiblePartY) { //alternate syntax
   //...
});

$('div').off('inview');
$('div').off('inview', callback);

$.inview(); //trigger a check
```


### OnScreen

The event will only fire when the element changes in its view state. It will keep firing if the user scrolls and the element remains on screen or not.  

`event`: jQuery event object.    
`top`: Offset of top from top of window  
`left`: Offset of left from left side of window  
`bottom`: Offset of bottom from bottom side of window   
`right`: Offset right from right side of window  
`percentFromTop`: Percentage offset of top from window top by window height  
`percentFromLeft`: Percentage offset of left from window left by window width  
`percentFromBottom`: Percentage offset of bottom from window bottom by window height  
`percentFromRight`: Percentage offset of right from window right by window width  
`percentInview`: Percentage area inview compared to the total possible inview area  
`percentInviewHorizontal`: Percentage horizonally inview compared to the total possible inview horizonally    
`percentInviewVertical`: Percentage vertically inview compared to the total possible inview vertically    
`onscreen`: true/false  
`uniqueMeasurementId`: Unique measurement Id  

```js
$('div').on('onscreen', function(event, measurement) {
  if (measurement.percentInview <= 0) {
    // element has gone out of viewport
    return;
  }
  // element is now visible in the viewport
  if (measurement.percentInviewVertical < 50) {
    // element is less than half onscreen vertically
    return;
  }
  // element is half or more than half onscreen vertically
});

$('div').onscreen(function(event, measurement) { // alternate syntax
  //...
});

$('div').off('onscreen');
$('div').off('onscreen', callback);

$('div').onscreen() = { 
  top: x,  
  left: x,  
  bottom: x,  
  right: x,  
  percentFromTop: x,  
  percentFromLeft: x,  
  percentFromBottom: x,   
  percentFromRight: x, 
  percentInview: x,  
  onscreen: x,
  uniqueMeasurementId: x   
};  

$.onscreen(); //trigger a check
```

### Locking

```js
$.inview.lock("name");
$.inview.unlock("name");
$.inview.isLocked("name");
$.inview.isLocked();
```

This will stop inview/onscreen from processing.

### Config

Stop scroll over inview behaviour
```js
$.inview.config({
  allowScrollOver: false
});
```
