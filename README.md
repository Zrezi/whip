# WHIP 0.0.2 Pre-Pre-Alpha

WHIP is a WebGL Library written to try to abstract some of the lower level WebGL calls into easier-to-understand functions. This project works extremely well with [glMatrix](http://glmatrix.net/) and I would go as far as to say that it's required to get any useful functionality out of the library.

### A Quick Word on Setup

The basis of WHIP is that you should be able to start drawing with WebGL within a few minutes. Below is a template HTML file that shows everything you need to get a minimal WebGL environment set up. Take a look:

```
<!DOCTYPE html>
<html>

	<head>
		<meta charset="utf-8">
		<title>WHIP Template</title>
		
		<script type="text/javascript" src="whip.js"></script>
		
		<!-- Implement post-init method here or in an external JS file -->
		<script type="text/javascript">
		
			function WHIPPostInit() {
				WHIP.setClearColor(WHIP.BLACK); // Set clear color to black
				WHIP.clear(); // Clear the screen
			}
			
		</script>
		
	</head>
	
	<body oncontextmenu="return false;" onload="WHIP.start()" onresize="WHIP.resize()">
		<canvas id="webgl-canvas" height="500" width="500"></canvas>
	</body>
	
</html>
```
This page will draw a 500x500 black square on the screen, with WebGL! There's a few things to take note of though.

###### Input Capturing

One thing to be aware of is that WHIP consumes input events so as to not affect the HTML page (all input events go straight to the input handler). If you're trying to refresh the screen with CTRL-R, this is why it won't work. I might add a flag to set/unset this functionality, but I prefer it right now.

###### HTML Body

The body of your HTML page *needs* to have the **onload** and the **onresize** attributes set to **"WHIP.start()"** and **"WHIP.resize()"** respectively.

###### WHIPPostInit()

After WHIP.start() finishes its initialization process, it will look for a function, obviously, named WHIPPostInit and try to run it. If it doesn't find this method, it will error out. Technically, this could be blank -- the WebGL context will still be initiated but nothing will be done with it.

### Examples

Definitely on their way...

### Documentation

The code is commented in [JSDoc](http://usejsdoc.org/) style, but I haven't generated the documentation for it yet. Everything should be fairly easy to read and understand from there.