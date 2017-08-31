# ImageNet Classification with Deep Convolutional Neural Networks
**Alex Krizhevsky, Ilya Sutskever, Geoffrey E. Hinton**

## Summary

The paper that started it all, it was the first deep learning paper that showed
state of the art performance in a real computer vision task. It was the first
deep learning based approach in the ImageNet competition, and it trounced other
methods at the time. The main contribution of this paper was to incorporate
previously known neural net techniques in a novel, simple, deep architecture:
- ReLU activation- faster convergence
- Model parallelism- bigger network->more parameters, slightly faster
- Local Response Normalization
- Overlapping Pooling- reduces overfitting
- Dropout- reduces overfitting
- Data Augmentation- reduces overfitting

The architecture uses 5 CNN layers and 3 fully connected layers.

## Things I learned

- One of the key differences in the Alexnet architecture was that it used ReLU
  activation functions which were relatively uncommon at the time (2012),
  compared to tanh layers.
- Performance on ImageNet is commonly reported using the below two metrics:
    - top 1% test set error rate- The fraction of test images for which the
      correct label is not the same as the highest model predicted label.
      Scored 37.5% 
    - top 5%- The fraction of test images for which the correct label is not
      among the five labels considered most probable by the model. Scored 17.0%
- The authors use model parallelism (as opposed to data parallelism) at the
  kernel level
- Here as in other NLP competitions(SQuAD), the best performance is obtained by
  averaging by averaging the prediction of multiple networks with different weight
  initializations
- Dropout-
    - Rationale behind dropout is a kind of ensembling during training, where for
    each input, a different architecture is sampled (but with shared
    weights)."This technique reduces complex co-adaptations of neurons, since a
    neuron cannot rely on the presence of particular other neurons. It is,
    therefore, forced to learn more robust features that are useful in
    conjunction with many different random subsets of the other neurons."
    - Dropout causes learning to take longer (approximately 1.5x)
    - During test time, activations of neurons are multiplied by 0.5 which is
      equivalent to taking the geometric mean of the network's predictions.
- In the data augmentation step

## Questions

- How *exactly* does model parallelism work for CNNs?
- Generally speaking, do convolutional layers have fewer parameters than fully
  connected ones?
- Why is the data usually normalized? And how/why does local response
  normalization work?
- What is the intuition behind overlapping pooling?
- Is there a principled approach to increasing depth in modern CNN models? More
  complex models like GoogleNet have ridiculous number of layers with millions
  of parameters. What's to say that each new tweak or improvement isn't
  specific to the dataset (overfit), and that these gains wouldn't be seen
  elsewhere (poor generalization)?

## Answers

