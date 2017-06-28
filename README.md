# WHIP 0.0.9 Pre-Pre-Alpha

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
				WHIP.setClearColor("black"); // Set clear color to black
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

One thing to be aware of is that WHIP consumes keyboard input events so as to not affect the HTML page (all input events go straight to the input handler). If you're trying to refresh the screen with CTRL-R, this is why it won't work. I might add a flag to set/unset this functionality, but I prefer it right now.

###### HTML Body

The body of your HTML page *needs* to have the **onload** and the **onresize** attributes set to **"WHIP.start()"** and **"WHIP.resize()"** respectively.

###### WHIPPostInit()

After WHIP.start() finishes its initialization process, it will look for a function, obviously, named WHIPPostInit and try to run it. If it doesn't find this method, it will error out. Technically, this could be blank -- the WebGL context will still be initiated but nothing will be done with it.

### Examples

Definitely (more) on their way as I figured out more things...

[Rotating Plane](https://zrezi.github.io/whip-examples/rotating%20plane/rotating_plane.html)

[Rotating Sphere](https://zrezi.github.io/whip-examples/rotating%20sphere/rotating_sphere.html)

### Documentation

The code is commented in [JSDoc](http://usejsdoc.org/) style, but I haven't generated the documentation for it yet. Everything should be fairly easy to read and understand from there.

### Ideas for the Future (maybe)

* GLSL Shader generation
* Utility functions moved into WHIP
* Mesh class representing a world object
* And easier way to draw objects, possibly via an array

### Past "versions" via commit history

* [0.0.1](https://github.com/Zrezi/whip/commit/98fcecba4dc5d1ac0398b6a5b5b65266a0fa69a0) - Initial Commit to Github
* [0.0.2](https://github.com/Zrezi/whip/commit/063ad7b7a573d4b861cdf3d1b9d07ba20bf81421) - Template and Init rework
* [0.0.3](https://github.com/Zrezi/whip/commit/75431e4777503e5b57fabda906564cd6c5c99313) - First example
* [0.0.4](https://github.com/Zrezi/whip/commit/9fe5fcab96346b00634319c87fa5a6e11e3bcab0) - Wireframe toggles
* [0.0.5](https://github.com/Zrezi/whip/commit/a60944086f7c27660608e97bc10919aee69fa8b9) - Rectangle and Sphere buffer generation
* [0.0.6](https://github.com/Zrezi/whip/commit/238182ea884b1fc1dc8bab61f853ff0497245703) - Rendering capabilities
* [0.0.7](https://github.com/Zrezi/whip/commit/634c5a13d2b4c8bb070625ed0f13c70d52100dd1) - Input and Color via strings
* [0.0.8](https://github.com/Zrezi/whip/commit/bea95bb20e2ebed9c0239f378dc2d3bb60583886) - Angle utility functions
* 0.0.9 - **(Current)** Mesh Utility