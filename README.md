
# Overview

Analysis of the Paper "Negative Data Augmentation" (ICLR 2021)

- Arxiv: [here](https://arxiv.org/abs/2102.05113)



# TLDR

## Key points 

![img1](images/NegativeDataAugmentation1.png)



## Summary

Very interesting paper about generative models

A common failure mode for generative models, especially GAN, is they produce a significant amount of "false positives": samples that are not realistic.

Why?

Using an analogy with physics, standard GANs are trained by enforcing a sort of attractive potential between the generator distribution and the true distribution samples, using the discriminator.
Theoretical guarantees: generative distribution converges to the true distribution in the infinite data limit.

What happens in practice?

See Fig.3, in the finite data limit, if the green dots distribution is not representing the green oval properly then the blue oval won't be able to overlap well.

Simple solution: more and better green dots
But this is not always possible.

The idea proposed in this paper is simple yet powerful: adding to the attractive potential related to the positive samples, also a repulsive potential related to negative samples.

The repulsive potential has the same theoretical guarantees and makes the more system more samples efficient since generating negative samples from positive samples is simple and cheap: see Fig.2

-------

Also available on LinkedIn [here](https://www.linkedin.com/feed/update/urn:li:activity:6765609955648147456/)

------

# Details 

More details about the paper 

## Positive Data Augmentation

### Math

- [Idea: Positive Data Augmentation](details/positive_data_augmentation.ipynb)

### Summary 

- Invariances can be used to manipulate in-distribution samples and produce more in-distribution samples



## Negative Data Augmentation

### Math

- [Idea: Negative Data Augmentation](details/negative_data_augmentation.ipynb)

### Intuition

![nda_gan1](images/nda_gan1.png)

- The goal of the generator is to learn the underlying data distribution 

- The transformation T transforms a data point which certainly belongs to the underlying data distribution into another data point which certainly does not belong to the underlying data distribution 

So while invariances manipulate existing in-distribution samples to produce other in-distribution samples, the negative augmentation functions transform in-distribution samples into out of distribution samples (with some degree of similarity to the original samples), so they do the opposite job



## Examples of Negative Augmentation Functions 

Some examples of such negative augmentation functions 

![nda_gan2](images/nda_gan2.png)





### Questions from my side 

1. What negative functions are more effective in training the generator? 

- Effectiveness can be measured with samples efficiency, so the less samples or the less negative samples the better 

- Probably this is also dependent on the specific generator used 



