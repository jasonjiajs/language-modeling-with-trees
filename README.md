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
![image](https://github.com/jasonjiajs/15.095_ml_under_a_modern_optimization_lens/assets/90637415/48300e54-7f19-4f5d-8119-b126e9e31f3c)

• Tree-BasedMethods
Tokenization: individual characters
'h','e','l','l','o',' ','w','o','r','l' 'd'
• CART, Random Forest, XGBoost
• NeuralNetworkMethods(Benchmark)
Context length for all models is the previous 10 characters
One-hot encoded vectors:
0 14 32] 14 [0,...,1,...0]
Target
• Feedforward Neural Networks
• Evaluation
• Training and Test Accuracy
• Training Time
• Interpretability


## Key Findings
Tree-based methods can sometimes **outperform** neural networks in next character prediction for the dataset sizes we trained on.

![image](https://github.com/jasonjiajs/15.095_ml_under_a_modern_optimization_lens/assets/90637415/2b14ad9d-28c8-4271-bcd1-a2db21cf88fb)

