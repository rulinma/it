# 基础知识


Scaler
Vector
Matrix
Tensor: multi-dimensional arrays

## 步骤流程

Stage
* Pretraining
  * Dataset: Raw internet, text trillions of words, low-quality, large quantity.
  * Algorithm: Language Modeling predict the next token(Tokenization)
  * Model: Base model
  * Notes: GPT, LLaMA, PaLM
* Supervised Finetuing
  * Dataset: Demonstrations, model “finetuning” on small supervised dataset
  * Algorithm: Language Modeling predict the next token(Tokenization)
  * Model: SFT model
  * NOtes: Vicuna-13B
* Reward Modeling
  * Dataset: Comparisions
  * Algorithm: Binary classification. Predict rewards consistent w preferences.
  * Model: RM model
  * Notes: None
* Reinforcement Learning
  * Dataset: Prompts
  * Algorithm: Reinforcement Learning
  * Model: RL model
  * Notes: Chat GPT, Claude

## 参考文献

1. [State of GPT](https://karpathy.ai/stateofgpt.pdf)
2. [GPT现状](https://mp.weixin.qq.com/s/zmEGzm1cdXupNoqZ65h7yg)
3. [Transformers 快速入门](https://transformers.run/c1/attention/)

## 名词解释

* BERT
  * Bidirectional Encoder Representations from Transformers：是Google开发的一种多功能语言模型，可用于多种NLP任务，如文本分类、问答系统和机器翻译等。它是一个双向Transformer模型，具有三层编码器和两个特殊的自我注意子层。
* GPT
  * Generative Pretrained Transformer
* LSTM
  * Long short-term memory (LSTM) is a type of recurrent neural network (RNN) aimed at dealing with the vanishing gradient problem present in traditional RNNs. 
* NNLM
  * Neural Network Language Model.
* RL
  * Reinforcement Learning（强化学习）是机器学习的一个重要子领域，它涉及到智能体（agent）通过与环境的互动来学习如何做出最佳决策或行为以达到某个目标。
* RLHF
  * RLHF（Reinforcement Learning from Human Feedback）是一种使用强化学习方法训练AI模型的过程，在该过程中，AI系统会从人类反馈中进行自我改进和优化。
* RNN
  * RNN stands for Recurrent Neural Network. It's a type of neural network that is designed to handle sequential data.
* SFT
  * 在大模型或人工智能领域的文献、文章或讨论中，"SFT" 通常指的是 "Sustainable Fine-Tuning"（可持续微调）。
* Transformer
  * The Transformer is a type of neural network that was introduced in 2017 by Vaswani et al. in the paper "Attention Is All You Need."