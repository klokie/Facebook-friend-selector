Welcome to the Facebook Friend Selector
=========================================

This is an interface component for websites and Facebook applications which allows your users to make a selection of one or more of their friends. The friends are returned as an array of Facebook IDs. It is similar to the `fb:multi-friend-selector` component by Facebook, except it can be used to select friends for anything, not just application requests.
## Credit to original authors

This is a forked project from [These Days Labs](http://playground.thesedays.com/FBFriendSelector/) friend selector. I (Mrman) have added a few features, reduced the complexity of placing the selector in a page (one div now).

## Viewing the example

You can view the example at [FBFriendSelector](http://fbfs.craig-saunders.co.uk/), just sign in to Facebook and approve the app (the app is empty so no security issues there).

If you clone the repository or download the tag then just replace the Facebook appID in index.html and everything should work.

The image below has been blurred for the sake of my friends privacy

![This is what it looks like.](http://fbfs.craig-saunders.co.uk/images/example.png)

## Using the plugin

### Include required HTML

- Place your div holder `<div id="FBFriendSelector"></div>`

### Include required CSS

- Include the `fbfriendselector.css` stylesheet (from css folder) in your document.
- Make sure the images included by `fbfriendselector.css` can be located (currently look to images/ folder) 

### Include required JavaScript

- Include jQuery in your document. 
- Include the Facebook [JavaScript SDK](http://developers.facebook.com/docs/reference/javascript/). (Technically, this step is optional. We have provided a `setFriends` function if you have loaded the friends on the serverside and want to avoid the JavaScript SDK.)
- Include `fbfriendselector.js` (located in js folder).
- Optional: We are using an HTML5 placeholder attribute on the search field. If you want the placeholder to work in older browsers, include a [placeholder polyfill](https://github.com/mathiasbynens/Placeholder-jQuery-Plugin).

### The fun stuff (using the plugin)

1 - Make sure your user has authenticated your Facebook app.

2 - Initialise the plugin. Here you can set options like toggling debug messages, your preferred classnames, etc.

	FBFriendSelector.init({debug: true});

3 - Create an instance of the plugin. We allow multiple instances per page because sometimes you will need users to select friends for more than one thing. You can pass in options here which will only effect this instance, for example a callback to deal with the friends that are selected.

	selector1 = FBFriendSelector.newInstance({
		callbackSubmit: function(selectedFriendIds) {
			console.log("The following friends were selected: " + selectedFriendIds.join(", "));
		}
	});

4 - Display the plugin instance when you need it. The plugin will automatically load the Facebook friends of the logged in user (and they will be cached and reused across all instances on the page).

	$("#btnSelect1").click(function (e) {
		e.preventDefault();
		selector1.showFriendSelector();
	});

