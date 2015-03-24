To run code:

Open index.html in Google Chrome. All resources can be loaded locally.

To analyze through Google's online Pagespeed Insights, user must host site remotely. Author used ngrok (https://github.com/inconshreveable/ngrok) and python's SimpleHTTPServer.


List of optimizations:
Index.html: 
	Optimized all images by resizing and compressing, and saving locally.
	Set Width and Height Attributes on all images to avoid repainting
	Inlined style.css and Screen.css
	Set print.css as a media-only query
	Inlined Google Web Fonts
	Set other scripts (analytics, perfmatters) with async tag to unblock rendering

Pizza.hmtl:
	Optimized pizzeria.jpg by shrinking size

main.js (pizzeria)
	Reduced number of background "slider" pizzas from 200 to 40 (line 536)
	Replaced all instances of document.querySelectAll() with document.getElementsByClassName() for efficiency

	In function updatePositions():
		Cache the document.body.scrollTop so it doesn't requery for every iteration.

	In function changePizzaSizes(size):
		cache the number of "randomPizzaContainer" object to avoid requerying every iteration.
		Move dx, newwidth outside of loop, as all objects have the same width anyway, and we only have to calculate the width/newwidth once.


