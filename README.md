# Language Modeling using Tree-Based Methods
Final Project, MIT 15.095 - Machine Learning Under a Modern Optimization Lens

## Summary


## Problem and Motivation
Neural networks are highly popular as models of choice for autoregressive language modeling (predicting the next token/character/word). However, they are computationally expensive to train.

On the other hand, tree-based models such as XGBoost, RF, CART and OCT can be easier to train and might be able to generate similar predictions. In fact, CART and OCT can even be interpretable. This is also in light of the proof in class that neural networks are equivalent to trees under certain assumptions.

We would thus like to experiment with tree-based methods and compare their performance with established neural network-based methods for autoregressive language modeling.

## Data

We used the cleaned Alpaca Dataset, a slightly modified version of the dataset used to fine-tune the Alpaca large language model. The data consists of instructions for the model, inputs for those instructions, and outputs that the model should try to recreate.

<img width="850" alt="image" src="https://github.com/jasonjiajs/15.095_ml_under_a_modern_optimization_lens/assets/90637415/db697744-3213-4c21-81af-767d3a5a0de4">

## Methods

### Preprocessing
Our preprocessing involved the following key steps:
- Tokens: We split sequences of concatenated instruction, input, and output by character, then take pairs of (10 consecutive characters, 11th character) as pairs of (X,Y).
![image](https://github.com/jasonjiajs/15.095_ml_under_a_modern_optimization_lens/assets/90637415/48300e54-7f19-4f5d-8119-b126e9e31f3c)
- We add an ‘[EOS]’ (End Of Sequence) token to the end of the sequence, which is the concatenation of the instruction, inputs and outputs. We include this so that at generation time, if a model generates an [EOS] token, this lets us know that the model is done generating an output.
- One-hot encoding of characters: Each character is mapped to an index, and each character is converted to a vector using one-hot encoding. Each of these one-hot encoded vectors is concatenated to make a binary input vector of size (vocabulary size) * (context length)
- Train/test split: We use an 80/20 train-test split.

### Tree-Based Methods
We tested several tree-based methods for autoregressive language modeling, including:
- CART
- XGBoost
- Random Forest

### Neural Network Methods(Benchmark)
We use feedforward neural networks (FFNs) as our benchmark. We choose a straightforward model architecture comprising an input layer, a hidden layer and an output layer. Here, embedding size is the number of rows of the weight matrix representing the hidden layer. The input to this model is the one-hot encoded context vector, which is the same input as the tree-based methods receive and makes results more comparable between methods.

### Evaluation
- Training and Test Accuracy
- Training Time
- Interpretability

## Key Findings
Tree-based methods can sometimes **outperform** neural networks in next character prediction for the dataset sizes we trained on.

![image](https://github.com/jasonjiajs/15.095_ml_under_a_modern_optimization_lens/assets/90637415/2b14ad9d-28c8-4271-bcd1-a2db21cf88fb)

