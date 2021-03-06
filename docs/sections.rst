Sections
========

A gallery is composed of a succession of sections as you can see on this `wonderfully
totally uninteresting example
gallery <http://psycojoker.github.io/prosopopee/first_gallery/>`_ the gallery is
composed of 5 sections:

* a full screen picture with text written on it
* a picture with borders around it
* a group of 5 pictures
* and a fullscreen picture without text on it this time

In your settings.yaml, a section will **always** have a ``type`` key
that will describe its kind and additional data. Underneath, the
``type`` key is actually the name of an HTML template and the other
data will be passed to this template.

You can find all the sections templates here: 

https://github.com/Psycojoker/prosopopee/tree/master/prosopopee/themes/exposure/templates/sections

You often have an ``image`` key. You need to give it a path to the
actual file. By convention, those files are put inside your gallery folder but
this is not mandatory.

Full Screen picture
___________________

This displays a full screen picture as shown in the `example
gallery <http://psycojoker.github.io/prosopopee/first_gallery/>`_ in the first
and last sections. How you should use it :

With text::

  - type: full-picture
    image: big_picture.jpg
    text:
      title: Big picture title
      sub_title: Some text
      date: 2016-01-15
      date_end: 2016-01-24 (Optional)

Without text::

  - type: full-picture
    image: big_picture.jpg

Bordered picture
________________

This displays a centered picture that is surrounded by white (the background) as
shown in the second position of the `example
gallery <http://psycojoker.github.io/prosopopee/first_gallery/>`_.

How to use it::

  - type: bordered-picture
    image: another_picture.jpg

Group of pictures
_________________

This displays a group of zoomable pictures on one or multiple lines as shown on
the fourth position (after the text) of the `example
gallery <http://psycojoker.github.io/prosopopee/first_gallery/>`_::

  - type: pictures-group
    images:
      -
        - image1.jpg
        - image2.jpg
        - image3.jpg
      -
        - image4.jpg
        - image5.jpg

The first level `-` represent a line of pictures.
The second level `-` represent the list of images in this line.

**Know bug**: the images are left aligned, so if you don't put enough images on
a line, you'll have white space on the right.

Text
____

This displays some centered text as shown on the third position of the `example
gallery <http://psycojoker.github.io/prosopopee/first_gallery/>`_. HTML is
allowed inside the text.

How to use it::

  - type: text
    text: Some text, HTML <b>is allowed</b>.

Paragraph
_________

This displays a h2 title followed by text. HTML is allowed inside of the text.
If no title is declared, a separator is added.

How to use it::

  - type: paragraph
    title: the title
    text: Some text, HTML <b>is allowed</b>.

HTML
____

This section is for raw html that will be centered (for example: inlining an OSM iframe).

How to use it::

  - type: html
    html: <tag>some html stuff</html>

Panorama
________


This displays a very large picture with a drag-and-drop possibility on it.

How to use it::

  - type: panorama
    image: 7.jpg

Author
______

This section is for describe the author of the story::

  - type: author
    name: Adrien Beudin
    text: Some text
    image: IMG_20150725_200941.jpg
    twitter: beudbeud (Optional)
    facebook: beudbeud (Optional)
    website: plop.fr (Optional)

Advanced options
________________

Images caption
~~~~~~~~~~~~~~

Prosopopée has a support of caption in images, you can use it on bordered-picture and pictures-group.

Exemple on bordered-picture::

  - type: bordered-picture
    image: another_picture.jpg
    text: This is a caption

And on pictures-group::

  - type: pictures-group
    images:
      -
        - name: image1.jpg
          text: This is a caption
        - image2.jpg
        - image3.jpg
      -
        - image4.jpg
        - image5.jpg

Background settings
~~~~~~~~~~~~~~~~~~~

For all section you can define the background.

Exemple for background color::

  - type: bordered-picture
    background: "#555"
    image: another_picture.jpg

or you can use picture::

  - type: text
    background: "url(background_picture.jpg)"
    text: Some text

Text color settings
~~~~~~~~~~~~~~~~~~~

For text, html and paragraph  section you can define the text color.

Exemple::

  - type: bordered-picture
    color: "#333"

Video support
~~~~~~~~~~~~~

For bordered-picture, full-picture and pictures-group it's possible to use
video instead of pictures. You have to specify with the "type" key that it's a
video.

The video will be converted using either ffmpeg or avconv (depending on the one
specified in the settings, ffmpeg being the default one).

Exemple for pictures-group::

  - type: pictures-group
    images:
      -
        - name: video.mp4
          type: video
        - image1.jpeg
        - image2.jpeg
      -
        - image3.jpeg
        - image4.jpeg

Exemple for bordered-picture::

  - type: bordered-picture
    image:
      name: video.mp4
      type: video

And for full-picture::

  - type: full-picture
    image:
      name: video.mp4
      type: video
    text:
      title: Title Text
      sub_title: Sub title text
      date: 2016-03-11
      date_end: 2016-03-25

You can also use a video for a gallery cover::

  title: pouet
  sub_title: plop
  cover:
    name: video.mp4
    type: video
