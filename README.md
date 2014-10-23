Swipe
=====

移动端专用轮播组件，支持滑动切换
改编自https://github.com/thebird/Swipe
，添加了点击页签可以切换至对应tab页功能

Usage
=====

Swipe only needs to follow a simple pattern. Here is an example:

```Html
<div id='slider' class='swipe'>
  <div class="swipe-wrap">
    <div><!-- anything --></div>
    <div><!-- anything --></div>
    <div><!-- anything --></div>
  </div>
  <div class="swipe-pagination">
    <div><!-- anything --></div>
    <div><!-- anything --></div>
    <div><!-- anything --></div>
  </div>
</div>
```

Above is the initial required structure– a series of elements wrapped in two containers. Place any content you want within the items. The containing div will need to be passed to the Swipe function like so:

```Javascript
window.mySwipe = Swipe(document.getElementById('slider'));
```

I always place this at the bottom of the page, externally, to verify the page is ready.

Also Swipe needs just a few styles added to your stylesheet:

```Css
.swipe {
  overflow: hidden;
  visibility: hidden;
  position: relative;
}
.swipe-wrap {
  overflow: hidden;
  position: relative;
}
.swipe-wrap > div {
  float:left;
  width:100%;
  position: relative;
}
.swipe-pagination {
  /* anything */
}
```

Config Options
=====

Swipe can take an optional second parameter– an object of key/value settings:

* startSlide Integer (default:0) - index position Swipe should start at

* speed Integer (default:300) - speed of prev and next transitions in milliseconds.

* auto Integer - begin with auto slideshow (time in milliseconds between slides)

* continuous Boolean (default:true) - create an infinite feel with no endpoints

* disableScroll Boolean (default:false) - stop any touches on this container from scrolling the page

* stopPropagation Boolean (default:false) - stop event propagation

* callback Function - runs at slide change.

* transitionEnd Function - runs at the end slide transition.

* pagination Boolean (default: true) - touch paginations can switch to the matching tab 

###Example

```Javascript
window.mySwipe = new Swipe(document.getElementById('slider'), {
  startSlide: 2,
  speed: 400,
  auto: 3000,
  continuous: true,
  disableScroll: false,
  stopPropagation: false,
  callback: function(index, elem) {},
  transitionEnd: function(index, elem) {}
});
```

Swipe API
=====

Swipe exposes a few functions that can be useful for script control of your slider.

`prev()` slide to prev

`next()` slide to next

`getPos()` returns current slide index position

`getNumSlides()` returns the total amount of slides

`slide(index, duration)` slide to set index position (duration: speed of transition in milliseconds)
