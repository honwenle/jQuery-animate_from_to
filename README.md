Animate from to v1.0 - a jQuery plugin
======================================

This is a simple jQuery plugin with one simple purpose: to give the impression
of movement from one element to another. This is useful for instance for
a web shop when you want show that a product was added to the cart. The
idea is based on another plugin called add2cart, but all of the code is
rewritten and made more flexible.

Tested in Firefox 10, IE 7-9, Chrome 17, Opera 10, Safari 5, and probably many more. It's not that much code, so if you find some bug it's easy to fix.

Note: You need to be in standards mode for this to work. In IE, use: ```<meta http-equiv="X-UA-Compatible" content="IE=Edge" />```

Who did this?
============================

* Emil Stenström [https://friendlybit.com](https://friendlybit.com). You're welcome!
* Johan Brook [https://johanbrook.com](https://johanbrook.com) contributed with code restructuring and a different type of plugin call.
* Thorbjörn 'Puggan' Sundragon [https://puggan.se/](https://puggan.se/) contributed TypeScript definitions.
* You? I'd love more contributions.

Quickstart
==========

Usage
------

Arguments and construction:

	$(sourceElm).animate_from_to(targetElm [, options]);

Basic, bare bones example with real arguments:

	$("#area-1").animate_from_to("#area-2");

It's also possible to use this construct:

	$.animate_from_to(sourceElm, targetElm, [, options]);


Example
-------

    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.5.2/jquery.min.js"></script>
    <script src="jquery.animate_from_to-1.0.js"></script>
    <script>
        $(document).ready(function(){
            $("#button1").click(function(){
                $('#prod_123').animate_from_to('#cart');
            });
        });
    </script>

    <span id="cart">
        My shopping cart
    </span>


    <div id="prod_123" style="height: 100px; width:300px; margin-top: 100px; background: pink">
        <form onsubmit="return false;">
            <button type="submit" id="button1">Add to cart</button>
        </form>
    </div>


Customization
------------

Slow the speed of the animation:

    $('#prod_123').animate_from_to('#cart', {
        pixels_per_second: 1000
    });

Slow the speed and make the animated element blue:

    $('#prod_123').animate_from_to('#cart', {
        pixels_per_second: 1000,
        initial_css: {
            'background': 'blue'
        }
    });

Call the function of your choice when the animation finishes:

    $('#prod_123').animate_from_to('#cart', {
        callback: function(){
			alert('Animation done');
		}
    });

Options
=======

This is what the different arguments mean:

**`sourceElm`** (*required*)

Element to start the animation from. Can be either a selector or a DOM element.

**`targetElm`** (*required*)

Element where the animation ends

**options** (*optional*, default: {})

- **pixels_per_second** (optional, default: 3000).
Speed of the animation, in number of pixels per elapsed second. This makes the
animation move with constant same speed no matter where on the page the
element is.

- **initial_css** (optional, default: [See source]).
Object literal. A way to override the default CSS of the "shadow" element that is part of the
animation.

- **image** (optional, default: '').
URL to image that will be used instead of a blank div

- **square** (optional, default: '').
There are two options
height: Will keep the animated div square, and animate it to the targets height
width: Will keep the animated div square, and animate it to the targets width

- **callback** (optional, default: [Dummy function that does nothing]).
Function. A callback that will be called when the animation finishes.


A custom call would hence look like this:

    $("#prod_123").animate_from_to("#cart", {
        pixels_per_second: 1000,
        initial_css: {
            "color": "red",
            "background-color": blue
        },
        callback: function(){
            alert("Completed!");
        }
    });


License
=======

Copyright (c) 2011 Emil Stenstrom <https://friendlybit.com>

Dual licensed under the MIT and GPL licenses:

* https://www.opensource.org/licenses/mit-license.php
* https://www.gnu.org/licenses/gpl.html
