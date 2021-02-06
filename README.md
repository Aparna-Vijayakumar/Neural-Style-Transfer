# Neural-Style-Transfer
Style Transfer using Cycle Consistent Adversarial Networks (CycleGANs)

### Overview
Neural Style Transfer is a set of algorithms by which digital images or videos can be manipulated to adopt the style of another image. It is an optimization
technique used to take two images—a content image and a style reference image (such as an artwork by a famous)—and blend them together so the output image
looks like the content image, but “painted” in the style of the style reference image. In this project, we incorporate a famous artist’s painting style, namely, Pablo Picasso’s cubist style of work onto
scenes and objects that we may find in our day-to-day life such as a bridge, or a playground.

### Dataset
We require two sets of data. One consisting of paintings by a famous artist (called style images), and one consisting of general images or scenes to transfer the artist’s
style onto (called content images). For the style images, we use the Best Artworks of All Time dataset containing the artwork of 50 renowned artists, which is publicly
available on Kaggle here https://www.kaggle.com/ikarus777/best-artworks-of-all-time . We use one artist’s paintings for style transfer, namely Pablo Picasso who is most famous for his cubist work. 
The dataset contains 439 paintings of Pablo Picasso. For the content images, we use a random sample of scene images from the BOLD5000 Stimuli dataset, also
publicly available at https://bold5000.github.io/download.html . This dataset contains images from the SUN Database, Microsoft COCO and ImageNet data which provides a good variety of content.

### Model
A Cycle-GAN is a special type of GAN which allows for style transfer between unpaired images. This
means that for a given set of content images, the model does not require a specific stylized image for each content
image in order to learn style transfer. Cycle-GANs are extremely useful in image-to-image translation tasks as it
is very hard to find paired images for training. We want to be able to transfer the artist’s general style to any content
image. Our model consists of 2 generators G<sub>content</sub> and G<sub>style</sub> and their corresponding discriminators D<sub>content</sub> and
D<sub>style</sub>. G<sub>content</sub> takes as input the style images (Picasso’s artwork) and tries to generate scene images identical to
that of our BOLD5000 Scene Stimuli dataset. G<sub>style</sub> takes as input the content images (Scene Stimuli Images from
BOLD5000) and tries to generate images that resemble Picasso’s paintings as closely as possible. Their associated
discriminators Dcontent and Dstyle learn to differentiate between the generated content and style images, and the
actual content and style images by predicting if an image was generated or if it is present in the original dataset.
