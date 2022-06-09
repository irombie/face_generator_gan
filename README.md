# Face Generation Using Generative Adversarial Networks

For this project, we are generating fake faces using the [CelebA dataset](http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html) and GANs! 
Due to computational resources, we scaled these images to 32x32. That is why the generated images are not of very high quality but they are still pretty convincing! 

![Alt text](faces.jpeg?raw=true "Title")

## Discriminator
    
The discrimnator uses 4 convolutioanl layers, latter 3 of which are followed by batch normalization layer, and one fully connected layer at the end. The hidden convoluational layers use leaky ReLU activation function. 

![Alt](discriminator.png?raw=true "Title")

## Generator

The generator is made up of 4 transpose convolutional layers, former 3 of which are followed by a batch normalization layer. 


![Alt](generator.png?raw=true "Title")

## GAN training

We can think of the training process of GANs as a game, where the generator is the adversary trying to trick the discriminator, which is the honest party. Since for this task, our aim is to __generate__ high quality images, we want generator loss to be low. But we also would like to avoid a situation where the generator loss is really small and the discriminator loss is large. This means that the generator suffers from overfitting. Thus, it is tricky to find the optimal point to stop the training. By trial and error, we find that training for 20 epochs gives good results with the following loss values: ```Epoch [   20/   20] | d_loss: 0.6345 | g_loss: 2.4629```. Therefore, we stop there. 

The loss graph for the discriminator and generator looks like the following: 

![Alt](loss.png?raw=true "Title")

It is quite different from the loss curves we observe in regular neural network training processes. When I first encountered a loss graph where the loss oscillates this much, I was wondering if there was an error in the code or not. Then, I learned that for adversarial networks, it is normal for the loss to oscillate and wanted to put this info out there in case anybody was wondering the same thing!

## More Faces!
 
![Alt](more_faces.png?raw=true "Title")

## Possible Improvements 

The generated faces are mostly white. In order to improve the model performance, the dataset needs to be more representative of the general population. Hence, more varied data should be collected.

Model is deep with more 4 conv and 4 transpose conv layers. However, the depth of the network could be increased for better generalization capability.

Using an adaptive learning rate might be a good idea.