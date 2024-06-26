---
title: Concepts
---

# Concepts

## Handle Complex Content

The data model and hierarchy developed in OHMG is very flexible, allowing for robust handling of single-page maps, multi-page atlases, or even multi-volume altases. This is carried-out by "demoting" (as it were) individual pages or documents and instead focusing one level up on the "Map" level, where a Map can hold one or more documents, each to be georeferenced individually. To illustrate...

### Single Map

In the most basic example, the Map has just one descendant document, and that document can be georeferenced to create a layer.

![simple map diagram](../../static/diagrams/content-hierarchy-simple.png)

### Multi-page Atlas

In a more complex (but very common) example, a multi-page atlas will have multiple documents, and each one will be georeferenced individually. These documents are still being accessed through the context of the atlas, providing an easy way to measure and track the completeness of the atlas's georeferencing process.

![simple map diagram](../../static/diagrams/content-hierarchy-multipage-atlas.png)

In this example, you'll notice one of the documents has been split to create two separate layers. More on this [below](#splitting-insets).

### Multi-volume Atlas

:::caution
This level of aggregation is still in development!
:::

Finally, a light-weight grouping mechanism will allow for multiple volumes from the same atlas to be handled together.

![simple map diagram](../../static/diagrams/content-hierarchy-multivolume.png)

### Splitting Insets

Because it is common for historical maps to have insets, or just multiple maps on a single page, the first step in the georeferencing workflow is to define these regions. Then, each region will be georeferenced individually, creating a layer from each piece.

![examples of splitting](../../static/img/split-example-3page-anno.jpg)

The image above illustrates how three pages of an atlas would be prepared. The first page split into four regions, the second split into two, and the third would be left as a single, full sheet. After each piece has been georefrenced, there will be seven individual layers.

## Seamless Mosaics

Mosaics offer the possibility of creating a single, seamless output layer from multiple sheets of an atlas. It may be helpful to think of mosaics as **layer sets**. While every map will have a layer set called "main content", in complex atlases there may be other categories of layers, for example an index or key map. Layer sets allow multiple types of layers to be combined and trimmed into seamless mosaics.

### Multimask

At heart of the mosaic is the idea of a **multimask**, which is simply a collection of masks across all the layers in a layer set. Its existence facilitates the trimming and mosaicking processes needed to create a single, seamless, output layer.

![Multimask, Sanborn Map of New Orleans 1885, Vol. 2](../../static/img/multimask.jpg)

### Simple Map &ndash; one "mosaic"

In the simplest example, a single scanned map is treated as the "main content" mosaic. This allows it to be trimmed if desired, and places it within the same category as other mosaicked output from more complex atlases.

![single page mosaic](../../static/diagrams/content-hierarchy-simple-mosaic.png)

### Complex Atlas &ndash; multiple mosaics

Some multipage atlases may contain multiple categories of layers, for example an index map on the front page, and the rest of the pages showing "main content". Using layer sets accomodates this allowing each georeferenced layer to be sorted into the proper category. After this, a multimask is applied to each set.

![multiple mosaics](../../static/diagrams/content-hierarchy-multiple-mosaics.png)

## Collaborative Model

An iterative, componentized workflow provides direct access for any user to contribute at any stage in the overall process.

## Transformations & Projections

Because GDAL is used in OHMG behind the scenes, any standard transformation algorithms can be used for GCPs (polynomial, thin plate spline, etc.), and any projection can be targeted.

## Web Services

Layers are immediately published as web services and can easily be integrated into third-party platforms, like OpenHistoricalMap and Felt. 

## Data API

A simple API can provide researchers with programmatic access to GCPs, cutlines, and GeoTIFF download links.
