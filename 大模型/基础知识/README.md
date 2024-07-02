# 基础知识

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
