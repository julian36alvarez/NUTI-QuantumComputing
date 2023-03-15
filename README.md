# NUTI-QuantumComputing 

By: ECI.

Version: 0.1.0

The Quantum Convolution Neural Network (QCNN) is a project under the NUTI-QuantumComputing initiative that aims to explore the potential of quantum computing in the field of image recognition and computer vision.

## Prerequisites

- [Anaconda](https://www.anaconda.com/download/) >=4.x
- Optional [Mamba](https://mamba.readthedocs.io/en/latest/)

## Create environment

```bash
conda env create -f environment.yml
activate nuti_quantumcomputing
```

or 

```bash
mamba env create -f environment.yml
activate nuti_quantumcomputing
```


## Project organization

    nuti_quantumcomputing
        ├── data
        │   ├── processed      <- The final, canonical data sets for modeling.
        │   └── raw            <- The original, immutable data dump.
        │
        ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
        │                         the creator's initials, and a short `-` delimited description, e.g.
        │                         `1.0-jvelezmagic-initial-data-exploration`.
        │
        ├── .gitignore         <- Files to ignore by `git`.
        │
        ├── environment.yml    <- The requirements file for reproducing the analysis environment.
        │
        └── README.md          <- The top-level README for developers using this project.

# The Quantum Convolution Neural Network

## Introduction

Convolutional Neural Networks (CNNs) are a type of artificial neural network that excel at detecting features and patterns in input data, particularly in image recognition and audio processing tasks. They are a widely used subclass of neural networks due to their ability to automatically learn hierarchical representations of data through convolutional layers.

Quantum Convolutional Neural Networks (QCNNs) behave similarly to Classical Convolutional Neural Networks (CCNNs), with the input image first encoded into a quantum circuit using a feature map. Alternating convolutional and pooling layers are then applied to the circuit to reduce its dimensionality, with the final classification of the image determined by measuring the output of a single qubit. The Quantum Convolutional Layer consists of two-qubit unitary operators that recognize relationships between the qubits, while the Quantum Pooling Layer reduces the number of qubits by disregarding certain qubits in specific layers. Each layer in the QCNN contains parametrized circuits, which are adjusted during training to minimize the loss function of the network.

## Components of a QCNN

$U = (A_1 \otimes A_2) \cdot N(\alpha, \beta, \gamma) \cdot (A_3 \otimes A_4)$

where $A_j \in \text{SU}(2)$, $\otimes$ is the tensor product, and $N(\alpha, \beta, \gamma) = exp(i[\alpha \sigma_x\sigma_x + \beta \sigma_y\sigma_y + \gamma \sigma_z\sigma_z ])$, where $\alpha, \beta, \gamma$ are the parameters that we can adjust. 

![image](https://user-images.githubusercontent.com/31891276/225196086-30920a25-ee24-446a-9be6-a1ff7116db14.png)

## Convolutional Layer

![image](https://user-images.githubusercontent.com/31891276/225421529-af6ac8b9-0285-4ad5-9ada-feb3ae9d7dac.png)

![image](https://user-images.githubusercontent.com/31891276/225421557-eaf386fc-9c5f-4d59-9742-f806eaa78758.png)

## Pooling Layer

The aim of a pooling layer is to decrease the dimensions of our Quantum Circuit, which means reducing the number of qubits in the circuit while preserving as much information as possible from previously learned data. This reduction in the number of qubits also results in a decrease in the computational cost of the overall circuit, since the number of parameters that the QCNN must learn is reduced.

![image](https://user-images.githubusercontent.com/31891276/225422622-720f6d16-e96c-4fe0-94f5-5615d80c3fe4.png)

## Data Generation

A common application of classical convolutional neural networks (CCNN) is image classification, where they use feature maps to detect specific features and patterns, such as straight lines or curves, in pixelated images. By learning the relationships between these features, CCNNs can classify and label handwritten digits with ease. Leveraging the CCNN's ability to recognize features and patterns, researchers aim to train a quantum convolutional neural network (QCNN) to distinguish between two patterns in 2 x 4 pixelated images: a horizontal or vertical line with a noisy background. To create the dataset, pixels are assigned values of 1 to represent a line and every other pixel is assigned a random value between 0 and 1 to create a noisy background. The dataset is then split into training and testing sets and labeled with -1 for horizontal lines and +1 for vertical lines to enable the QCNN to differentiate between the patterns.

![image](https://user-images.githubusercontent.com/31891276/225422989-6e2ceb89-7163-41c2-b1ed-76e94a4747bb.png)

## Modeling QCNN


With the convolutional layers now defined, the next step is to construct the quantum convolutional neural network (QCNN) by implementing alternating pooling and convolutional layers. Since the dataset images contain eight pixels, the QCNN will use eight qubits. The dataset is encoded into the QCNN using a feature map, which can be generated using one of Qiskit's built-in feature maps such as ZFeatureMap or ZZFeatureMap. After analyzing multiple feature maps, it was discovered that the Z feature map produces the highest accuracy for this dataset. Consequently, the tutorial will continue to use the Z feature map going forward.

![image](https://user-images.githubusercontent.com/31891276/225423676-e336564f-0472-471f-bf8f-de04815d4053.png)

![image](https://user-images.githubusercontent.com/31891276/225424341-511b5807-8487-4bf8-a16c-7bc91f9488ef.png)

## Training  QCNN

The subsequent phase involves constructing the model with the training data. The classification is determined by performing a measurement from the output circuit, which yields a value that signifies whether the input data contains a vertical or horizontal line. The tutorial selects the expectation value of the Pauli Z qubit for the final qubit, denoted as $<Z>$, as the measurement to classify the data. Measuring this expectation value results in a value of either +1 or -1, which correspond to a vertical or horizontal line, respectively.
    
 ![image](https://user-images.githubusercontent.com/31891276/225425042-df07df0d-77e0-4a66-aaff-7326c374330b.png)
    
 ![image](https://user-images.githubusercontent.com/31891276/225425374-32914fb4-a1c7-422e-9e2e-ac26534fc5de.png)

## Test QCNN
    
 ![image](https://user-images.githubusercontent.com/31891276/225425579-6d488cf6-976d-4080-b75e-cb26dd98b009.png)


---
Project created for NUTI's Quantum Computing initiative course.




