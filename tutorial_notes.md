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





