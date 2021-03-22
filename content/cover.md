---
title: Cover
weight: 1
menu: false
type: cover
slug: .
toc: false
image: figures/00094701-sm.jpg
---

**Issues / Questions:**

- When getting started in a new project, it felt a little excessive to have to create a `iiif` directory within `img` and then a `images` directory within that. Should we have these set up but empty in the default starter? And/or could we possibly eliminate the `images` directory and just have users put images for processing directly in `iiif`?

- For workflow (ours internally and users) would best practice be to add the high-res image, process it, and then remove it from the project? So, not to commit to a GitHub repository? And process related, I’m going to need to test moving the processed image tiles into a figures sub-module that we can keep private, in the case of third-party licensed images. And I’m a little concerned about overall repository file sizes. The compressed `site` directory for this sample project with five IIIIF image tile sets is 270MB, versus 35MB without the IIIF tiles.

- When running `quire imageslice`, the command line prints `ℹ Finding images to process...` and then can go quiet for a **very** long time. It took me about 20 minutes to slice a 130MB file for *Irises*. Let’s consider adding to this output so users don’t feel it’s hung up. Maybe something like `ℹ Processing images, this may take a while depending on the image file sizes ...`

- The command also checks to make sure the images are of a proceessable file format type and outputs a message if not. This is useful in normal circumstances, like if a user tries to process a TIF, but it‘s also messaging about files that most users can’t see, like: `✖ Cannot slice file .DS_Store. File type must be: .jp2, .jpg, .jpeg, .png, .svg.`. Can we think about how to handle this differently?

- Should we consider changing the command to `quire iiif`?

- The catalogue entry viewer won't display IIIF images unless there's another non-IIIF image included in the carousel. See Adolphe Braun’s [[Flowers]](/catalogue/3/) for an example. [DEV-7105](https://jira.getty.edu/browse/DEV-7105)

- (As an aside, let’s look at turning off mouseover/touch zoom behavior in the catalogue entry viewer. It’s problematic for users when I think the +/- controls suffice.)

- In [`themes/default/source/js/deepzoom.js`](https://github.com/thegetty/quire/blob/main/themes/default/source/js/deepzoom.js) the max zoom level (lines 68 and 83) is set at 4 which was really limiting. I changed it to 10 as a test and I could zoom fully in on all the images, but actually too far in. [See the *Irises* catalouge entry as a good example.](/catalogue/1/) Is the `imageslice` command slicing to a consistent number of levels? Or is it based on the size of the image being sliced? Can we somehow read how many layers are available and set the zoom level to that? And whatever the solution, how will it work with IIIF images being called from external pre-existing sources?

- What about the static JPGs? Should Quire users continue including them to use for things like the [contents image grids](/catalogue/), the PDF and e-book outputs, and for images with `download: true`? Or, is it possible to employ IIIF for these things too?