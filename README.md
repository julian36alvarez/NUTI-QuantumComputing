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


---
Project created for NUTI's Quantum Computing initiative course.




