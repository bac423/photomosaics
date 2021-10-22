# Autoencoders for solving Photomosaic.
Transform an image of your choice into a beautiful photomosaic consisting of artificially generated tiles.

<photos of woman, man, sunset, bender, and me>

Vary the density of tiles for images of different sizes.

<sunset 100x100, my photo 28x28>

This approach makes use of a specially pretrained autoencoder to encode tiles into a dense latent space and decode them as images close to the autoencoder’s original training set.

# How is this different from photomosaics that use pre-prepared tiles?
There are many great search-based algorithms to create photomosaics. These algorithms come with an advantage in the form of the perfect quality of tiles. You can find a large number of such artworks on the web. For example, if you are a fan of British football, here is a Bobby Robson portrait made up of 2,000 pictures of Newcastle by Welsh artist Nathan Wyburn.

https://i2-prod.chroniclelive.co.uk/incoming/article16568705.ece/ALTERNATES/s615b/0_A-portrait-of-Sir-Bobby-Robson-has-been-created-after-the-people-of-Newcastle-voted-for-the-Geordie.jpg

However, search-based models lack flexibility, and their effectiveness and speed depend heavily on the diversity and size of datasets. The autoencoder approach has three main advantages over search-based models. 
1)	Tiles fit better in their neighborhoods because they are generated for each location individually. 
2)	Fewer tiles are required to process images in a meaningful way. 
3)	The speed does not suffer from the size of the dataset used for autoencoder training. This promises to be useful with large and complex datasets.

Overall, the search-based approach is still better for creating meaningful artworks, while the autoencoder approach can act as an online operating filter.

# How efficient is this approach? 
Generation of realistic images from “something a bit better than random noise” while keeping some visual information presents many challenges. 

It is necessary to keep the balance between the quality of tiles and the overall accuracy of photomosaics. By this token, it is vitally important to keep the set of possible encodings in the latent space as uniform as possible to ensure that each tile satisfies the desired quality.

For MNIST, I successfully used a two-dimensional latent space. To support uniformity, I included a sigmoid activation function to limit the latent space to $(0, 1)^2$ and added Gaussian noise to the model during training.

<distribution of digits>

Finally, I must mention that a more advanced autoencoder or a separate GAN for generation might solve this problem. Preparing these models takes time, but it is certainly promising. 
