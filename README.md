# emo-classification-bilstm

## Introduction
In neural network the information flows in one direction from input to output. However in RNN information is fed back into the system after each step. Which means RNNs allow the network to “remember” past information by feeding the output from one step into next step. This helps the network understand the context of what has already happened and make better predictions based on that. <br/>

**RNN RESİM**

However, RNNs suffer from a common issue called _vanishing gradients_. The vanishing gradient problem is a challenge that emerges during backpropagation when the derivatives or slopes of the activation functions become progressively smaller as we move backward through the layers of a neural network. The weight updates becomes extremely tiny, or even exponentially small, it can significantly prolong the training time, and in the worst-case scenario, it can halt the training process altogether. <br/>

There are a number of ways to overcome this issue:
- Batch Normalization
- ReLU as Activation Function
- Skip Connections and Residual Networks (ResNets)
- Long Short-Term Memory Networks (LSTMs)
- Gated Recurrent Units (GRUs)




