---
aliases:
  - Bayer filter
resources: |-
  https://en.wikipedia.org/w/index.php?title=Bayer_filter&useskin=vector

  https://bokehrentals.com/bayer-sensor-technology/
---
A Beyer filter mosaic is a colour filter array (CFA) for arranging RGB colour filters on a square  grid of photosensors. This is the arrangement that is used most commonly in single-chip digital image sensors.

The filter pattern is half green, one quarter red and one quarter blue, hence is also called BGGR, RGBG, GRBG or RGGB. This combination is used because they are "opposite colours", similar opposite colours like cyan-magenta-yellow are also used. CMY combinations were impractical as the dyes did not exist, however some cameras today use them. The CMY combination has a higher [[quantum efficiency]].

Each photo-site is sensitive to only one colour, and in the majority of camera systems, each photo-site corresponds to one pixel in the final image.

![[Bayer pattern-img-2311081837.png]]

The original patent calls the green sensors _luminance-sensitive_ and calls the red and blue ones _chrominance-sensitive_ elements. The use of the twice as many green elements, compared to red and blue, mimic the physiology of the [[human eye]]. The luminesce perception of the [[human eye]] uses M and L [[cone cells]]-- which are most sensitive to green light.  

The raw output from a Bayer pattern has each pixel recording only a single colour. To create a full-colour image a demosaicing algorithm is used to interpolate a set of RGB values for each pixel, the algorithm interpolates depending on the surrounding pixels.

**Demosaicing** #re-edit

Simple methods interpolate the colour value of the pixels of the same colour in the neighbourhood. For example, once the chip has been exposed to an image, each pixel can be read. A pixel with a green filter provides an exact measurement of the green component. The red and blue components for this pixel are obtained from the neighbours. For a green pixel, two red neighbours can be interpolated to yield the red value, also two blue pixels can be interpolated to yield the blue value.

This simple approach works well in areas with constant colour or smooth gradients, but it can cause artefacts such as colour bleeding in areas where there are abrupt changes in colour or brightness especially noticeable along sharp edges in the image. Because of this, other demosaicing methods attempt to identify high-contrast edges and only interpolate along these edges, but not across them.

Other algorithms are based on the assumption that the colour of an area in the image is relatively constant even under changing light conditions, so that the colour channels are highly correlated with each other. Therefore, the green channel is interpolated at first then the red and afterwards the blue channel, so that the colour ratio red-green respective blue-green are constant. There are other methods that make different assumptions about the image content and starting from this attempt to calculate the missing colour values.

![[Bayer pattern-img-2311081837 1.png]]

1. Original scene
2. Output of a 120×80-pixel sensor with a Bayer filter
3. Output color-coded with Bayer filter colors
4. Reconstructed image after interpolating missing color information
5. Full RGB version at 120×80-pixels for comparison

**Why do we need this?**

The colour sensor does not measure the wavelength of the light directly, only the intensity.

[[Film stock|Film stocks]] also face this issue, they overcome it by using a layer of dyes. 

Early digital cameras used prisms to separate wavelengths of light.

