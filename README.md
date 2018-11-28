### lazy.js
---
https://github.com/dtao/lazy.js

```js
var people = getBigArrayOfPeople();

var results = _.chain(people)
  .plunk('lastName')
  .filter(function(name) { return name.startsWith('Smith'); })
  .take(5)
  .value();
  
var results = [];
for(var i = 0; i < people.length; ++i){
  if(people[i].lastName.startsWith('Smith')){
    results.push(people[i].lastName);
    if(results.length === 5){
      break;
    }
  }
}

var result = Lazy(people)
  .plunk('lastName')
  .filter(function(name) { return name.startsWith('Smith'); })
  .take(5);
  
Lazy.generate(Math.random)
  .map(function(e) { return Math.floor(e * 1000) + 1; })
  .uniq()
  .take(300)
  .each(function(e) { console.log(e); });

var fibonacci = Lazy.generate(function(){
  var x = 1;
      y = 1;
  return function(){
    var prev = x;
    x = y;
    y += prev;
    return prev;
  };
}());
fibonacci.take(10).toArray();

Lazy.generate(Lazy.identity)
  .async(1000)
  .map(function(x){ return String.formCharCode(x + 65); })
  .take(26)
  .each(function(char) { console.log(char); });

var mouseEvents = Lazy(sourceElement).on("mousemove");
var coordinates = mouseEvents.map(function(e){
  var elementRect = sourceElement.getElement.getBoundingRect();
  return [
    Math.floor(e.clientX - elementRect.left),
    Math.floor(e.clientY - elementRect.top)
  ];
});
coordinates
  .filter(function(pos) { return pos[0] < sourceElement.clientWidth / 2; })
  .each(function(pos) { displayCoordinates(leftElement, pos); });
coordinates
  .filter(function(pos) { return pos[0] > sourceElement.clientWidth / 2; })
  .each(function(pos) { displayCoordinates(rightElement, pos); });
  
var firstFiveLines = text.split("\n").slice(0, 5);
var firstFiveLines = Lazy(text).split("\n").take(5);

var firstFiveWords = Lazy(text).match(/[a-z0-9]+/i).take(5);

Lazy(stream)
  .take(5)
  .each(processData);
  
Lazy.readFile("path/to/file")
  .lines()
  .take(5)
  .each(doSomething);
Lazy.makeHttpRequest("http://example.com")
  .lines()
  .drop(5)
  .take(5)
  .each(doSomething);
```

```
npm install lazy.js
```

```
<script type="text/javascript" src="lazy.js"></script>
<script type="text/javascript" src="lazy.browser.js"></script>
```


