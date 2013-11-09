SalesLink Email Templates: Designing and Coding Guidelines
============================================================

We’ve written this document to help you create SalesLink templates. It contains some hard rules as well as simple guidelines. You may successfully ignore some of what’s below but, be sure to test your templates rigorously.

Designing your Template
-----------------------

The only hard rule for designing templates is that the maximum width for the content area has to be 600px, and the minimum width 450px. Besides that, you’re only limited by your imagination.
**General design guidelines*** What works for print, doesn’t necessarily work on screen.* Design for end-use in mind. Clients will be viewing your templates in email applications not in Photoshop/InDesign/Illustrator. As such, it’s more important that your design works in the former and not the latter.* Don’t rely on complex layouts and visual effects generated in image editing software. Any part of the template that will be dynamically generated should be styled with CSS/HTML.* Design your email template to degrade gracefully. Not all email applications support the latest CSS so you should keep in mind how your design will look if a particular CSS attribute is not working.* Design to reduce the amount of images used when coding the email template.* Try different variations of content to see how your email template will behave (with and without a headshot, with a short and long headline, etc). Ensure that your design still works if a particular piece of content is not available.* Avoid making your design reliant on the end-user having to format their content to fit your vision (if your design only works with a square headshot, but breaks with a rectangular one, you should rethink your design).* Observe basic design principles like Hierarchy, Balance, Contrast, Movement, Rhythm/Pattern.

Coding your Template
--------------------

Keep in mind that HTML development for emails is quite different than development for websites. While it’s always important to observe code standards and best-practices, because of the lack of support for CSS in many popular email applications, it’s best to err on the side of caution. That usually means avoiding the latest CSS properties and using nested tables for spacing and positioning.**General coding guidelines*** A table-based structure is best.
** Many email applications have issues with `div` tags. If you must use `div` tags then avoid using the CSS `float` property.
** Avoid using the CSS `position` property, many email applications do not support this.** Avoid using CSS `padding` or `margins` properties for spacing, many email applications do not support them.* Ensure that text in table cells wraps properly, and doesn’t cause the table to exceed the max. 600px content width.
* Avoid background images, many email applications do not support them. If you do wish to use background images, make sure there is a suitable background colour if the images do not show up.* `alt` attributes should be added to all images.* `title` attributes should be added to all links that use an image instead of text in case the image does not load.
* Use only GIFs or JPGs as some emails client will not display PNG files.**Initial set-up**Start with a standard HTML document that has:* a W3C 4.01 Transitional Doctype Declaration;* a UTF-8 character-set `meta` tag in the `head` element; and
* a `title` tag in the `head` element.

    <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">    <html>
        <head>            <meta http-equiv="Content-Type" content="text/html; charset=utf-8">            <title>Title goes here</title>        </head>        <body></body>    </html>

For tracking purposes please add a special `img` tag just before the closing `body` tag:        <body>            <img id="raybec_open" src="http://templates.mysaleslink.com/static/images/transparent.gif" alt="tracking">        </body>Next: add a few styling attributes to the `body` tag. These will set the margin to 0 (recommended) and the background colour to white (you can change this to any other colour you wish):        <body bgcolor="ffffff" topmargin="0" leftmargin="0" marginheight="0" marginwidth="0">

Because support for styling attributes is so varied among the different email applications, it is recommend that you also add the above mentioned styles to the `head` element in the form of CSS `style` tag. This will also allow us to set a few other attributes that will help email rendering in iOS applications.        <head>            <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
            <title>Title goes here</title>            <style type="text/css">                body {
                    background:#ffffff;
                    margin: 0 !important;                    padding: 0 !important;                    width: 100% !important;                    -webkit-font-smoothing: antialiased;                    -webkit-text-size-adjust: none;
                }
            </style>
        </head>

Next: you’ll want to create a “wrapper” table in the body element that will hold the rest of the content. Assign an `id="wrapper"` to this table and duplicate the stylistic attributes with css rules in the head element.                #wrapper {                    width: 100%;                    background: #ffffff;                }

            <table id="wrapper" cellspacing="0" cellpadding="0" border="0" width="100%" bgcolor="ffffff"><tr><td align="center">                content goes here            </td></tr></table>

That’s it for the initial set up. The code above provides you with a good foundation on which to build your own template. 

Here’s the final html document you should now have:    <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">    <html>
        <head>            <meta http-equiv="Content-Type" content="text/html; charset=utf-8">            <title>Title goes here</title>
            <style type="text/css">                body {
                    background:#ffffff;
                    margin: 0 !important;                    padding: 0 !important;                    width: 100% !important;                    -webkit-font-smoothing: antialiased;                    -webkit-text-size-adjust: none;
                }
                #wrapper {                    width: 100%;                    background: #ffffff;                }
            </style>        </head>        <body>
            <table id="wrapper" cellspacing="0" cellpadding="0" border="0" width="100%" bgcolor="ffffff"><tr><td align="center">                content goes here            </td></tr></table>
            <img id="raybec_open" src="http://templates.mysaleslink.com/static/images/transparent.gif" alt="tracking">        </body>    </html>

Making your Template SalesLink compatible
-----------------------------------------
