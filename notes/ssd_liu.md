# SSD: Single Shot MultiBox Detector
**Wei Liu, Dragomir Anguelov, Dumitru Erhan, Christian Szegedy, Scott Reed, Cheng-Yang Fu, Alexander C. BergPaper name**

## Summary

This paper introduces a new end-to-end deep learning architecture to perform
object detection. This isn't the first paper to do such a thing, but has higher
accuracy and speed (FPS) than previous approaches. This also removes the need
for region proposals. Borrows quite a few ideas from YOLO, Faster-RCNN and MultiBox.

Architecture:
VGG base net-> multiple conv layers to generate feature maps at diff scales-> conv. prediction layer

## Things I learned

- You can use convolutional filters for prediction

## Questions

- What are default boxes?
- How are default boxes different from sliding windows? 
- How is prediction done at each default box. 
- What are offsets?
- How do they use conv filters for prediction?
- How to combine predictions for *multiple objects* at different scales? Non max
suppression doesn't care about labels, just bounding box positions and scores. Is it a per category NMS?

## Answers

- The default boxes are essentially boxes(of differing aspect ratios) around
anchor points. Each anchor point corresponds to a cell in the feature map. 
- Since the default boxes are extracted using convolution (part of the
network), the correct output (ground truth) needs to be provided to the
specific set of outputs of the net (while the others outputs are told that they
are wrong. This is done in the loss function).  In a sliding window approach,
the NN is trained on the positive and negative windows.


