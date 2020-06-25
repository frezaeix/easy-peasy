# easy-peasy
Basics - Good, Simple and Interesting Tutorials and Blog Posts Arount The Web

## Multi-Task-Learning

* [An Overview of Multi-Task Learning in Deep Neural Networks](https://ruder.io/multi-task/index.html)

## GAN

* [Generative Adversarial Networks (GANs) in 50 lines of code (PyTorch)](https://medium.com/@devnag/generative-adversarial-networks-gans-in-50-lines-of-code-pytorch-e81b79659e3f), Very nice!
*  [GAN — What is wrong with the GAN cost function?](https://medium.com/@jonathan_hui/gan-what-is-wrong-with-the-gan-cost-function-6f594162ce01), 5 min read

* [A Gentle Introduction to Generative Adversarial Network Loss Functions](https://machinelearningmastery.com/generative-adversarial-network-loss-functions/)
  
  1-1 Summary (mainly copy pasting for myself to not forget some parts.. _check the tutorial itself!_)
    
    * The GAN architecture is relatively straightforward, although one aspect that remains challenging for beginners is the topic of **GAN loss functions**.
    
    * The discriminator model is updated like any other deep learning neural network, although the generator uses the discriminator as the loss function, meaning that **the loss function for the generator is implicit and learned during training**.
    
      * The generator is not trained directly and instead is trained via the discriminator model. Specifically, the discriminator is learned to provide the loss function for the generator.

    * We typically seek convergence of a model on a training dataset observed as the minimization of the chosen loss function on the training dataset. In a GAN, convergence signals the end of the two player game. Instead, equilibrium between generator and discriminator loss is sought.
    
    * Described mathematically, the discriminator seeks to maximize the average of the log probability for real images and the log of the inverted probabilities of fake images.
      
      * maximize log D(x) + log(1 – D(G(z)))
    
    * In practice, [the loss function] may not provide sufficient gradient for G to learn well. Early in learning, when G is poor, D can reject samples with high confidence because they are clearly different from the training data.
    
    
     
    
## Github

* [Markdown](https://guides.github.com/features/mastering-markdown/)

# Intermediate Materials

## GAN

* [From GAN to WGAN](https://arxiv.org/pdf/1904.08994.pdf)]

* [How to Identify and Diagnose GAN Failure Modes](https://machinelearningmastery.com/practical-guide-to-gan-failure-modes/)
