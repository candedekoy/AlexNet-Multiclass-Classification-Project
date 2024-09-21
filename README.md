# AlexNet Multiclass Classification Project

## Description
This project focuses on a multiclass classification task using a modified AlexNet architecture, implemented in PyTorch, and trained on a custom dataset. The main steps involve resizing the input images, modifying the AlexNet architecture to fit the classification problem, addressing class imbalance, and evaluating the model using F1 score metrics.

## Methodology

### Dataset and Image Preprocessing:
*  The dataset consists of 256x256 RGB images. Since the pre-trained AlexNet model requires 227x227, images are resized.
*  Mean and standard deviation for each channel are calculated from the training set. These statistics were used to normalize the inputs during training, improving the model's performance.

### Model Architecture 
*  Pretrained AlexNet model is used and the last fully connected layer (out_feature) is modified to output 3 classes.

### Loss Function
*  Cross Entropy Loss is used for multiclass classification task.

### Optimizer 
*  A common variant of Stochastic Gradient Descent (SGD) "Adam" is used.
*  The learning rate was set to 0.01, a typical choice, and a learning rate scheduler was added, though it was not required in this case due to successful convergence within 5 epochs.

### Addressing Class Imbalance
*  To handle class imbalance in the training data undersampling is implemented. This ensured each class had the same number of training and validation images.
*  The test set was left unchanged to maintain real-world representativeness and avoid biasing the evaluation results.

### Evaluation
*  The table below presents F1 scores for the training set, validation set, and test set, comparing results with and without input normalization, as well as with and without addressing the class imbalance.

## Results

<table>
  <thead>
    <tr>
      <th rowspan="2">Condition</th>
      <th colspan="4">Training portion of the training set</th>
      <th colspan="4">Validation portion of the training set</th>
      <th colspan="4">Test set</th>
    </tr>
    <tr>
      <th>Class 1</th>
      <th>Class 2</th>
      <th>Class 3</th>
      <th>Overall</th>
      <th>Class 1</th>
      <th>Class 2</th>
      <th>Class 3</th>
      <th>Overall</th>
      <th>Class 1</th>
      <th>Class 2</th>
      <th>Class 3</th>
      <th>Overall</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>With input normalization and with addressing the class-imbalance problem</td>
      <td>1</td>
      <td>0.98</td>
      <td>0.98</td>
      <td>0.99</td>
      <td>0.86</td>
      <td>0.92</td>
      <td>0.91</td>
      <td>0.90</td>
      <td>0.98</td>
      <td>0.92</td>
      <td>0.90</td>
      <td>0.93</td>
    </tr>
    <tr>
      <td>With input normalization and without addressing the class-imbalance problem</td>
      <td>0.95</td>
      <td>0.88</td>
      <td>0.81</td>
      <td>0.88</td>
      <td>0.90</td>
      <td>0.90</td>
      <td>0.67</td>
      <td>0.82</td>
      <td>0.95</td>
      <td>0.89</td>
      <td>0.88</td>
      <td>0.91</td>
    </tr>
    <tr>
      <td>Without input normalization and with addressing the class-imbalance problem</td>
      <td>0.84</td>
      <td>0.81</td>
      <td>0.88</td>
      <td>0.84</td>
      <td>0.71</td>
      <td>0.62</td>
      <td>0.91</td>
      <td>0.75</td>
      <td>0.83</td>
      <td>0.79</td>
      <td>0.80</td>
      <td>0.81</td>
    </tr>
  </tbody>
</table>

