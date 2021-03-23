---
title: Introduction
weight: 3
# image: figures/lange-house.jpg
---

To better see where IIIF is being employed by Quire versus where the static JPG is being used, IIIF image tiles are in color, the static JPG source images are in black and white.

| Pixel Length of Longest Side of Original Image | Levels of Zoom Created |
| ---------------------- | -------------- |
| > 16384                | 7              |
| > 8192                 | 6              |
| > 4096                 | 5              |
| > 2048                 | 4              |
| > 1024                 | 3              |
| > 512                  | 2              |
| > 256                  | 1              |

Using a IIIF image in the **q-figure-zoom** shortcode:

{{< q-figure-zoom id="irises" >}}

Using IIIF image from an **external info.json** file and internal static fallback JPG in the **q-figure-zoom** shortcode:

{{< q-figure-zoom id="iris-sibirica" >}}

Using IIIF images in the **q-figure-group** shortcode:

{{< q-figure-group grid="2" id="vase-of-flowers, flowers, flowers-and-beetles, still-life" >}}


