# Deep Residual Learning for Image Recognition
**Kaiming He, Xiangyu Zhang, Shaoqing Ren, Jian Sun**

## Summary

This paper discusses the problems with training very deep networks and
introduces "residual connections" to alleviate the problem. The authors assert
that a deep net with layers copied from a shallow network, and the remaining
layers all assigned identity function should be no worse than the shallow
network. In practice however, optimizers are unable to find even this solution
(let alone a better one), and actually degrade in performance.

The intermediate layers are made to learn "residual functions" ie. H(x)-x,
where x is the input to the layers and H(x) is the layer we actually want to
learn. The reasoning is that the outputs are equivalent but the residual
connections are easier to learn.

The authors also test their Resnets for object detection by bolting it on to
the Faster-RCNN framework and show SOTA results.

## Things I learned

- Degradation problem
    - Increasing depth beyond a certain point degrades *both* training and test
      error, thus highlighting that overfitting is not the problem (one would
      expect at least training error to be less than that of the shallow
      network)
- The authors assert that identity mappings are hard to learn for a stack of
  nonlinear layers
- They also found through experiments that this is **not** due to the vanishing
  gradient problem (They use BN and verify that forward/backward signals don't
  vanish). 
- More analysis in [Identity Mappings in Deep Residual Networks](https://arxiv.org/pdf/1603.05027.pdf)


## Questions

- How are the shortcut connections actually implemented in a software package?
    - x-> intermediate layer-> F(x)+x. How is the intermediate layer forced to
      produce just F(x)? For instance, is it frozen
- In practice, why are Resnets better than Highway Networks (Srivastava et al.)
  when the identity mapping is a subset of the solution space of the Highway
  networks?

## Answers



