# ARMI Ecosystem Documentation

This repository exists to support a GitHub Pages for the documentation of all open-source TerraPower projects. For instance, at the time of this writing, this repo represents the GitHub repositories:

* armi
* armicontrib-dif3d
* dragon-plugin

The primary documentation pages will be for the bleeding-edge, latest-and-greatest version of each repository/package. But as important releases happen, we will also append the versioned, official releases of the documentation too. For instance:

* https://terrapower.github.io/releases/armi/v0.2.0/index.html

## Release Instructions

The default, top-level documentation in this repo (for instance, the top-level `/armi/` folder) is used for the most recent, up-to-date, bleeding-edge version of the software. But every time a major/minor release happens, we should make it part of our release process to immediately archive off the documentation for that version of the software.

The process to do this is easy.

Let's say the ARMI package has just released version `1.0.0`. Hurray! After waiting a few minutes, the documentation for that version will be automatically deployed by a GitHub Action job here, to the top-level `/armi/` folder. To archive the documentation for that release, simply copy/paste the _entire_ documenation folder to: `/releases/armi/v1.0.0/`. Done!

For extra points, please add a link to your new documentation in the top-level [index.html](https://github.com/terrapower/terrapower.github.io/blob/master/index.html) file.
