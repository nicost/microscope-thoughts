#How to serve locally so that it matches what is seen on github

On github, the site is served form https://nicost.github.io/microscope-thoughts, so all paths to images are prepended with microscope-thoughts.  There are likely fancy ways to deal with this, but we can mimic this locally by starting a local server as folloed:

`buncle exec jekyll serve --baseurl /microsocpe-thoughts`
