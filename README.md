# jquery.table-shrinker
A fast-render, lightweight plugin to turn tables responsive the right way.
<br/>
Turn your hugest table into a compact table with a great user experience.

![table-shrinker](https://user-images.githubusercontent.com/5666881/55237489-0b5bd480-5211-11e9-933b-552d340cbae3.png)

## Getting Started
Just do it.

### Prerequisites
[Jquery](https://jquery.com/)
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js" crossorigin="anonymous"></script>
```

### Installing
Insert the .css
```html
<link rel="stylesheet" href="jquery.table-shrinker.min.css">
```

Insert the .js
```html
<script src="jquery.table-shrinker.min.js"></script>
```

## How to use
First, add <b>shrink</b> class to the table you want to be shrinked

```html
  <table class="shrink">
```
Next, instantiate the plugin right after the DOM finished rendering
```javascript
    options = {
          useZebra: false     // i don't like zebras
          useObserver: false  // turned off observer because i really don't like zebras
        }
        
    $("table.shrink").tableShrinker(options)
```

And finally, add <b>shrink-XX</b> classes to the header to tell them when you want them to be shrinked
```html
<thead>
  <tr>
    <th> User-ID </th> <!-- never shrinks -->
    <th class="shrink-xxs" > First Name </th> <!-- shrinks @ 320px  -->
    <th class="shrink-xs" > Last Name </th> <!-- shrinks @ 480px  -->
    <th class="shrink-sm" > Driver Licence </th> <!-- shrinks @ 768px  -->
    <th class="shrink-md" > Phone number </th> <!-- shrinks @ 992px  -->
    <th class="shrink-lg" > e-mail</th> <!-- shrinks @ 1200px  -->
    <th class="shrink-xl" > Street address </th>  <!-- always shrinks -->
  </tr>
</thead>
```

Additionally, there's a <b>shrinkable</b> class which make texts containers responsive
This is usefull if you like to keep displaying a large info cell in a tiny devices, preventing its texts to breakline.
``` html
  <th class="shrinkable"> Full Name </th>
```

---
Basically that's it. your table should be shrinked by now.
<br/>
Below there's the options explanation and some hints of use.

---
### Options

#### useZebra
###### default: true
Table rows inside wrapper became striped.
#### useObserver
###### default: true
update Zebra whenever a new cell becomes visible in the wrapper.
<br/>
not supported for older browsers check compatibility [here](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API#Browser_compatibility).
#### useTransitions
###### default: true
Animate when collapsing the wrapper.
#### transitionSpeed
###### default: 300
name says it all.
#### ignoreWhenHit
###### default: 'button, a, .btn'
If you have a share button on each row you might want to ignore it.
<br>
so if any tap/click event hit one of these elements it's event propagation is stoped, this way buttons can keep their functionality inside the table.
#### showToggler
###### default: true
You can disable the toggler icon and still show/hide the shrinked content by hiting the anywhere in the row (except for the ignoreWhenHit elements)
#### customToggler
###### default: ['\<span\>+\<\/span\>','\<span\>-\<\/span\>]
A list of two html's that is toggled when wrapper collapses, you can add classes or change it's content and control the toggler's design at your own css




### Hints
#### Instant Load
You can instantly render the table at the first graphic engine loop of the browser by adding the same <b>shrink-XX</b> and <b>shrinkable</b> classes that you used on the table headers to every table cell
<br>
For example:
```html
<thead>
  <tr>
    <th> User-ID </th> <!-- never shrinks -->
    <th class="shrink-xs"> Age </th>
    <th class="shrink-xs shrinkable" > Full Name </th>
    <th class="shrink-md" > e-mail </th>
    <th class="shrink-lg" > Phone number </th>
  </tr>
</thead>
<tbody>
  <tr>
    <td> #0001 </td>
    <td class="shrink-xs"> 27 </td>
    <td class="shrink-xs shrinkable" > Hubert Blaine Wolfe­schlegel­stein­hausen­berger­dorff Sr. </td>
    <td class="shrink-md" > H_B@wolfe.com </td>
    <td class="shrink-lg" > +(66) 666.66666-6666 </td>
  </tr>
  <tr> 
  (...)
</tbody>
```
This way your table first loads directly in it's shrinked state!
<br/>
There's no impact in performance speed, the only downside of this is that if you have tables that renders 100+ rows in the same page your DOM tree can get very large.


#### Larger than desktops
If you want to show more data in the same table but even desktops width can't handle, just keep adding columns with <br>shrink-xl</br>

```html
    (...)
    <th class="shrink-xl" > Addtional Info </th> 
    <th class="shrink-xl" > Addtional Info </th> 
  </tr>
</thead>
```
<br>
