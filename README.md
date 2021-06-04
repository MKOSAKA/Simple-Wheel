
# Simple Wheel Picker

## DEMO
- [samples/index.html](https://mkosaka.github.io/Simple-Wheel-Picker/samples/index.html)
- [pppark.com](https://pppark.com/) (using for selection the datetime to park. **ONLY JAPANESE**)


## INSTALL
```html
<!-- simple wheel needs jQuery -->
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>

<link rel="stylesheet" href="./css/simple-wheel-picker.min.css">
<script src="./js/simple-wheel-picker.min.js"></script>
```

## USAGE
Simpl-Wheel-Picker needs to have `class="simple_wheel"`.
```javascript
<!-- single wheel -->
<div class="simple_wheel">
    <ul>
        <li>select-1</li>
        <li>select-2</li>
        <li>select-3</li>
        <li>select-4</li>
    </ul>
</div>
```

```javascript
<!-- multiple wheels -->
<div class="YOUR_WRAPPER">
    <div id="hour" class="simple_wheel">
        <ul>
        <li>AM 01</li>
        <li>AM 02</li>
        <li>AM 03</li>
        <li>AM 04</li>
        </ul>
    </div>
    <div class="simple_wheel_separator">
        :
    </div>
    <div id="min" class="simple_wheel">
        <ul>
        <li>00</li>
        <li>15</li>
        <li>30</li>
        <li>45</li>
        </ul>
    </div>
</div>
```


## Fucntions

All functions need a prefix `__SW__`.




##### Programatic Selection of List Item
```javascript
__SW__.selectListItemForIndex({
    index:3,
    wheel: 'hour', // wheel's id or jQuery object or DOM
    animate_dur: 0, // millisecound. (default 50)
    checkIndexChanged: true, //if true, new index value is compared with current one. if it has not changed, the event 'select' will not occur. (default true)
    fireEventSelect: true, // if true, the event 'select' will occur. (default true)
    callback: false
});
```


##### Get index and values of selected list items.
```javascript
const selectedItem = __SW__.getIndexAndValOfSelectedListItem('hour');
console.log(selectedItem.index);    // ex:3
console.log(selectedItem.value);    // ex:'AM04'
```

## Event

Simple Wheel occurs event `"select"`.
```javascript
const wheel = document.getElementById('hour');
wheel.addEventListener("select", function(e){
    console.log(e.detail.selected_index); // index of selected list item.
});
```


## Design
You can cahange Style like bellow.

```html
<style>
    .my-wheel{
        width: 300px;
        height: 200px;

        font-size: 1.2rem;
        background-color: #f3f3f3;
        border-color: blue;
    }
</style>

<div class="simple-wheel my-wheel">
    ...
</div>
```
simple-wheel-separator is convenient for displaying strings and images as separators.
```html
<style>
    .wheel_grp{
        height: 200px;
    }
    .wheel_grp .separator{
        width: 10px;
    }
    .wheel_grp .hour,
    .wheel_grp .min{
        width: 200px;
    }
</style>
<div class="wheel_grp_01">
    <div class="simple-wheel hour"></div>
    <div class="simple-wheel-separator separator">:</div>
    <div class="simple-wheel min"></div>
</div>
```
    


## Requirement

* jQuery 3.6.0

