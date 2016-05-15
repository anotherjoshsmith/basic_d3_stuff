# some stuff
**models.js** is a library built by Curran
tons of libraries based on d3... 
dc.js lets you link plots together interactively, could be important for our project.

covering examples similar to *let's make a barchart* tutorial

*d3 script* is sorta just a patchwork of html, javascript, and css. 

**jsbin.com** for prototyping. play w example code and see output quickly.

##Examples

need to set the size of an svg element itself...
starting in the top left for x=0, y=0 makes sense from the stand point of building a page up from scratch
coo... don't use rgb thooo

z at the end of path specification closes the path!

move stuff together by grouping with **g** tag, transfrom and translate
To resize... write some javascript to look for certain event to trigger resize.

use google fonts to manipulate text style

##JavaScript notes

+myString parses myString into a number. it's magic...

myArray[myArray.length - 1] gives you the last thing in your array. Similar to python, but you can't just do -1.

var myObject = {
  x: 5,
  y: 10,
}

myObject.x orrrrr myObject["y"]. again much more familiar given pandas experience.
You can also have an array of objects. [ {x: 5, y:10}, {x: 3, y: 7} }]

console.log?? similar to print...

myArray.forEach(someFunction (d){blah blah... elementwise application of function to array objects}

##and so, d3 begins

d3.csv loads file, second argument is function to act on csv elements

parsefloat in d3 d.x = parseFloat(d.x);
                 d.y = parseFloat(d.y)

w/o d.x = +d.x as in the normal js case

scale in d3:

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>D3 Example</title>
    <script src="//cdnjs.cloudflare.com/ajax/libs/d3/3.5.5/d3.min.js"></script>
  </head>
  <body>

    <script>

      var scale = d3.scale.linear()
        .domain([0, 1])  // Data space
        .range([0, 100]); // Pixel space

      console.log(scale(0));   // Prints 0
      console.log(scale(0.5)); // Prints 50
      console.log(scale(1));   // Prints 100

    </script>

  </body>
</html>

allows you to project from data space (.domain) to pixel space (.range)
*notice method chaining in scale variable. common in d3*

"method chaining w getter/setter funcitions is all over d3."

domain and range are like keys and values in the ordinal case. .rangePoints useful for binning? 
.rangeRoundPoints() better for crisp lines in svg

"d3 is a dom manipulation library." d3 databinding... selectAll("rect").data(data).enter()
// virtual selection executes only when there is no DOM element, but there are data elements.

d3.select("body".append("svg")
  .attr("width", 250)
  .attr("height", 250);

important to set up script for the case of data coming and leaving...
**.enter()** is only executed only for **new DOM elements**. it does NOT update data!
"you have different phases." // Bind data // Enter // Update // Exit
- if an attribute is constant, it should be a part of the enter phase
- rects.exit().remove(), only executes when there are less DOM elements than previously selected

cool way to scale your data automatically... 
xScale.domain(d3.extent(data, function (d){ return d.sepal_length; })); // or set xColumn = "sepal_length" at the top of your code
yScale.domain(d3.extent(data, function (d){ return d.petal_length; }));
- invert y range so that minimum is at the bottom and max is top
- use variables for "xColumn" rather than "sepal_length" so that your code is more reuseable!
- oh man, d3.scale.log() is bae
wow, crazy how a few lines makes your visualization so much more visually appealing (color/ring stuff)

d3.scale.category10 somewhat magically assigns color to ordinal data... yay!
define margins and take advantage of g element for transformation. d3 convention is to implement margins all in one element.

population map based on longitude and latitude is coool. again, two lines of css drastically change the effect.
ahhh look at selection code from live temp example. casts selection to new location, related to what i need to do.
d3.svg.line() to create my lines... luckily there isn't actually live updates. only case we update is for the transition from FA to FA residuals. could be relatively simple in this way... just need to update color(or alpha) on mouse hover and selection.
...and link to sortable demographic table. line graphs don't even have to update on sorting.


mmm data.map? might have to rewind and hear that part again.
Let's add some axes! append group objects for each axis? can be sorta tedious to set these up how you like.. 
...should probably start w a template for all the CSS stuff.

##FIN
