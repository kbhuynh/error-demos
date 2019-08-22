
# Error Page Animations

This document lists the required dependencies and steps taken to create the animations featured on the error pages (e.g., 404, 500, 503).

## Required Dependencies 

 - Adobe After Effects
 - [Bodymovin/Lottie](https://github.com/airbnb/lottie-web)
 - [Vanilla-tilt.js](https://micku7zu.github.io/vanilla-tilt.js/)

## Step 1: Animating in After Effects & Exporting JSON

After installing a version of Adobe After Effects and the Bodymovin plugin, create an animation using the software. Once finished, pull up the plugin's page by going to Window > Extensions > Bodymovin. Select the composition to be rendered and exported; then choose any of the options by clicking the gear icon. Finally, select the destination folder to save the rendered animation and  JSON code. Beware that some After Effects features are not yet supported by Bodymovin/Lottie (a list of which can be found [here](https://airbnb.io/lottie/#/supported-features)).

## Step 2: Embed in HTML Page
The destination folder you chose should now contain the necessary files for embedding into the web. Include the lottie.js (available via a CDN [here](https://cdnjs.com/libraries/bodymovin)) script, and create a div for the animation such as: `<div id="lottie"></div>`. Then, make a JS call, which can be as simple as this:

	var animation = bodymovin.loadAnimation({ 
		container: document.getElementById('lottie'),  // Required 
		path:  'data.json',  // Required 
		renderer:  'svg/canvas/html',  // Required 
		loop:  true,  // Optional 
		autoplay:  true,  // Optional 
		name:  "Hello World",  // Name for future reference. Optional.  
	})

For the error pages, only the SVG renderer is used. 

## Step 3: Style with CSS 
Now, the animation should appear on the HTML page, so you can style the div you created with CSS to your liking.

## Step 4: Parallax Effect
To apply the parallax tilting effect, make sure to include the vanilla-tilt.js script right before the closing `</body>` tag. Add the `data-tilt` attribute to your div for the animation. For example, `<div id="lottie" data-tilt></div>`. That is all you need to get the animation to start tilting. To see other options, see the [Vanilla Tilt documentation](https://micku7zu.github.io/vanilla-tilt.js/).  
