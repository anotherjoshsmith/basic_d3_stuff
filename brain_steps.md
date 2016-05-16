#some notes on examples relevant to connectome project...

each individual fa graph should look something like the following example:
http://bl.ocks.org/Matthew-Weber/5645518

important differences
- do away with dragging and zooming. could add these back in, but only allow drag in relevant area
- "select series:" menu can be used to select fa or fa residual. alternatively, make it a toggle button (probably better)
- no need for legend
- add axes


selecting table data... select from lines by color whatever we select with mouse
d3.selectAll("line").style("color", "WHITE")
