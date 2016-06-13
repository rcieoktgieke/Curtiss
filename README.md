# Curtiss Gallery Management

Curtiss is a platform to generate static galleries by reading and scaling image files. This allows for optimal load times, because the thumbnails created by the image processing script are no larger than the dimensions they will be loaded with. By keeping the gallery static, images can be scaled and aligned nicely while maintaining a gallery as responsive as possible, because no computaion and re-rendering is passed on to the client. It also reduces server load; because each request is fulfilled with the same response, only minimal work is required on backend. A more detailed examination of the benefits of a static site can be found here: weber.lol.

##What Curtiss does:

Curtiss reads images from a configurable directory, scales such that all images which share a row are the same height (but not all rows are the same height), and saves the scaled images to a configurable output directory. The front end then renders the images into a fully-contained gallery that can be placed anywhere on any webpage, with a width (and image margins) specified in configuration. A more detailed description of how it does all of this will likely appear here at some later time, but until then, documentation can be found throughout most of the code.

##Installation:

Hopefully coming soon... good luck? 


Notes to be incorporated later:

Relative links are turned on for Middleman to allow Curtiss galleries to be deployed on pages in a location other than the root of the site's filesystem.
Variables that can be defined in the config.rb file:
The path to the folder where all images to be processed and used by Curtiss will be stored.
The path to the folder where thumbnails will be saved.
The width (in pixel) which Curtiss will make each row fit within.
The number of images Curtiss will attempt to place on each row.
The number of pixels Curtiss will leave for margins BETWEEN images.
The number of pixels left blank on each row by default. Try adjusting this if images are wrapping before the end of their rows.
The height of the list of thumbnails used in the overlay.
The config.rb script calls a function which wraps the entirety of the curtiss\_image\_process.rb script.
A number of variables are passed from the config.rb script to the front end source code using the config[] variable.
The index.html.erb assigns an index to each image in the gallery according to the order in which they appear in the gallery matrix. This index is used by the JavaScript to swap out each thumbnail for its higher-res counterpart.
In the JavaScript, calling addToOverlayThumbs() from loadGalleryImages() creates placeholders (in a way) for the thumbnail images in the overlay, but leaves the loading of these thumbnails visible (in some cases) to the user. Calling addToOverlayThumbs() from replaceImageWhenLoaded() results in dynamic insertions to the overlay thumbnail list, but only renders thumbnails when they are fully loaded.
The gallery-container-div div wraps all gallery content (not the overlay), and thus can be safely moved to any location on the pgae, and galley content can be expected to follow it.
