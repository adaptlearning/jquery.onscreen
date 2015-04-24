# jquery.onscreen
Inview replacement with extra functionality


##Usage

####Inview

The event will only fire when the element changes in its view state. It won’t keep firing if the user scrolls and the element remains in view.

**Handler parameters / view states**  
isInView: Indicates the visible state.  
visiblePartX: Detects which horizontal part of the element is visible to the user (possible values: left, right, both, none)  
visiblePartY: Detects which vertical part of the element is visible to the user (possible values: top, bottom, both, none)  

```
$('div').on('inview', function(event, isInView, visiblePartX, visiblePartY) {
  if (isInView) {
    // element is now visible in the viewport
    if (visiblePartY == 'top') {
      // top part of element is visible
    } else if (visiblePartY == 'bottom') {
      // bottom part of element is visible
    } else {
      // whole part of element is visible
    }
  } else {
    // element has gone out of viewport
  }
});

$('div').off('inview');
```


####Onscreen

The event will only fire when the element changes in its view state. It will keep firing if the user scrolls and the element remains on screen or not.  

**Handler parameters / view states**  
top: Offset of top from top of window  
left: Offset of left from left side of window  
bottom: Offset of bottom from bottom side of window   
right: Offset right from right side of window  
percentFromTop: Percentage offset of top from window top by window height  
percentFromLeft: Percentage offset of left from window left by window width  
percentFromBottom: Percentage offset of bottom from window bottom by window height  
percentFromRight: Percentage offset of right from window right by window width  
percentInview: Percentage area inview compared to the total possible inview area  
percentInviewHorizonal: Percentage horizonally inview compared to the total possible inview horizonally    
percentInviewVertical: Percentage vertically inview compared to the total possible inview vertically    
uniqueMeasurementId: Unique measurement Id  

```
$('div').on('onscreen', function(event, measurement ) {
  if (measurement.percentInview > 0) {
    // element is now visible in the viewport
    if (measurement.percentInviewVertical < 50) {
      // element is less than half onscreen vertically
    } else {
      // element is half or more than half onscreen vertically
    }
  } else {
    // element has gone out of viewport
  }
});

$('div').off('onscreen');
```
