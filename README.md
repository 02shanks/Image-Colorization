# Image-Colorization


## RGB and Lab

RGB and CIE Lab (or just "Lab") are two different color spaces, or ways of describing colors.RGB operates on three channels: red, green and blue. Lab is a conversion of the same information to a lightness component L*, and two color components - a* and b*.

RGB color space: <br />
R - indicating how much Red the pixel is <br />
G - indicating how much Green the pixel is <br />
B - indicating how much Blue the pixel is <br />

Lab color space: <br />
L - encodes Lightness of each pixel <br />
a - encode how much green-red each pixel is <br />
b - encode how much yellow-blue each pixel is <br />


## WorkFlow of our Conditional GAN:

### Generator:
Using Lab color space info, 
1. L channel(which is the grayscale image) is given to the generator model(U-net architecture)  
2. It predict the other two channels (*a, *b) and after its prediction, we concatenate all the channels and we get our colorful image.

<img width="400" alt="image" src="https://user-images.githubusercontent.com/76114538/176705408-a4d4fff3-c5f9-4d02-a493-6fdc0d776536.png">

### Discriminator:
1. The discriminator(convolutional “PatchGAN” classifier), takes these two produced channels and concatenates them with the input grayscale image and decides whether this new 3-channel image is fake or real.
2. Also discriminator(convolutional “PatchGAN” classifier) also takes real images (3-channel images again in Lab color space) that are not produced by the generator and decides whether this new 3-channel image is fake or real.

<img width="500" alt="image" src="https://user-images.githubusercontent.com/76114538/176712855-59f929fc-2638-4eaa-aa5e-1ffe202e8512.png">



