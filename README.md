# easy-peasy
Basics - Good, Simple and Interesting Tutorials and Blog Posts Arount The Web

## Multi-Task-Learning

* [An Overview of Multi-Task Learning in Deep Neural Networks](https://ruder.io/multi-task/index.html)

## GAN

* [Generative Adversarial Networks (GANs) in 50 lines of code (PyTorch)](https://medium.com/@devnag/generative-adversarial-networks-gans-in-50-lines-of-code-pytorch-e81b79659e3f), Very nice!
*  [GAN — What is wrong with the GAN cost function?](https://medium.com/@jonathan_hui/gan-what-is-wrong-with-the-gan-cost-function-6f594162ce01), 5 min read

* [A Gentle Introduction to Generative Adversarial Network Loss Functions](https://machinelearningmastery.com/generative-adversarial-network-loss-functions/), Very Nice for beginners!!
  
  1-1 Summary (mainly copy pasting for myself to not forget some parts.. _check the tutorial itself!_)
    
    * The GAN architecture is relatively straightforward, although one aspect that remains challenging for beginners is the topic of **GAN loss functions**.
    
    * The discriminator model is updated like any other deep learning neural network, although the generator uses the discriminator as the loss function, meaning that **the loss function for the generator is implicit and learned during training**.
    
      * The generator is not trained directly and instead is trained via the discriminator model. Specifically, the discriminator is learned to provide the loss function for the generator.

    * We typically seek convergence of a model on a training dataset observed as the minimization of the chosen loss function on the training dataset. In a GAN, convergence signals the end of the two player game. Instead, equilibrium between generator and discriminator loss is sought.
    
    * **Discriminator Loss:** Described mathematically, the discriminator seeks to maximize the average of the log probability for real images and the log of the inverted probabilities of fake images.
      
      * maximize log D(x) + log(1 – D(G(z)))
    
    * **Minimax GAN Loss:** In practice, [the loss function] may not provide sufficient gradient for G to learn well. Early in learning, when G is poor, D can reject samples with high confidence because they are clearly different from the training data.
    
    * **Non-Saturating GAN Loss:** In practice, this is also implemented as a binary classification problem, like the discriminator. Instead of maximizing the loss, we can flip the labels for real and fake images and minimize the cross-entropy.
    
    * **Wasserstein GAN Loss:**  The Earth-Mover’s distance calculates the distance between two probability distributions in terms of the cost of turning one distribution (pile of earth) into another.
    
    * The GAN using Wasserstein loss involves changing the notion of the discriminator into a critic that is updated more often (e.g. five times more often) than the generator model.
    
    * The critic scores images with a real value instead of predicting a probability. It also requires that model weights be kept small, e.g. clipped to a hypercube of [-0.01, 0.01].
    
    * The score is calculated such that the distance between scores for real and fake images are maximally separate.
    
    * The benefit of Wasserstein loss is that it provides a useful gradient almost everywhere, allowing for the continued training of the models. It also means that a lower Wasserstein loss correlates with better generator image quality, meaning that we are explicitly seeking a minimization of generator loss.
    
    * To our knowledge, this is the first time in GAN literature that such a property is shown, where the loss of the GAN shows properties of convergence.
    
    * **Effect of Different GAN Loss Functions:** Many loss functions have been developed and evaluated in an effort to improve the stability of training GAN models. The most common is the non-saturating loss, generally, and the Least Squares and Wasserstein loss in larger and more recent GAN models.
    
    * > Despite a very rich research activity leading to numerous interesting GAN algorithms, it is still very hard to assess which algorithm(s) perform better than others. We conduct a neutral, multi-faceted large-scale empirical study on state-of-the-art models and evaluation measures. _Are GANs Created Equal? A Large-Scale Study, 2018._
    
    * This includes the Minimax loss (MM GAN), Non-Saturating loss (NS GAN), Wasserstein loss (WGAN), and Least-Squares loss (LS GAN) described above. The study also includes an extension of Wasserstein loss to remove the weight clipping called Wasserstein Gradient Penalty loss (WGAN GP) and two others, DRAGAN and BEGAN.
    
    * The models were evaluated systematically using a range of GAN evaluation metrics, including the popular Frechet Inception Distance, or FID.

    * **Surprisingly, they discover that all evaluated loss functions performed approximately the same when all other elements were held constant.**
    
    * This does not mean that the choice of loss does not matter for specific problems and model configurations. Instead, the result suggests that the difference in the choice of loss function disappears when the other concerns of the model are held constant, such as computational budget and model configuration.
     
    
## Github

* [Markdown](https://guides.github.com/features/mastering-markdown/)

# Intermediate Materials

## GAN

* [From GAN to WGAN](https://arxiv.org/pdf/1904.08994.pdf), 2019

* [How to Identify and Diagnose GAN Failure Modes](https://machinelearningmastery.com/practical-guide-to-gan-failure-modes/), Very Nice!

1-1 Summary (mainly copy pasting for myself to not forget some parts.. _check the tutorial itself!_)

* GANs are difficult to train. The reason they are difficult to train is that both the generator model and the discriminator model are trained simultaneously in a zero sum game. This means that improvements to one model come at the expense of the other model.

  * The goal of training two models involves finding a point of equilibrium between the two competing concerns.

  * It also means that every time the parameters of one of the models are updated, the nature of the optimization problem that is being solved is changed. This has the effect of creating a dynamic system. In neural network terms, the technical challenge of training two competing neural networks at the same time is that they can fail to converge.
  
  * check this tutorial if you wanna know:
    1. How to identify **a stable GAN training** process from the generator and discriminator loss over time.
    2. How to identify **a mode collapse** by reviewing both learning curves and generated images.
    3. How to identify **a convergence failure** by reviewing learning curves of generator and discriminator loss over time.
    
*  checking discriminator loss for real and for generated fake images

* We can summarize these observations for stable GAN training as follows:

  1. Discriminator loss on real and fake images is expected to sit around 0.5.
  2. Generator loss on fake images is expected to sit between 0.5 and perhaps 2.0.
  3. Discriminator accuracy on real and fake images is expected to sit around 80%.
  4. Variance of generator and discriminator loss is expected to remain modest.
  5. The generator is expected to produce its highest quality images during a period of stability.
  6. Training stability may degenerate into periods of high-variance loss and corresponding lower quality generated images.
