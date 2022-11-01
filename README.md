# Self-Attention Attribution: Interpreting Information Interactions Inside Transformer

## Overview:
**Reminder:** What is multi-head self-attention? Mechanism within the transformer architecture that learns token dependencies and encodes contextual information from the input.

**Problem:** Transformer architecture is like a "black box" when it comes to how multi-head self attention is actually working within the model. The authors want to solve the claim that prior work on self-attention fails to describe how the model inputs are interacting with attention to derive an output prediction.

**Author's solution:** A self-attention attribution method (ATTATTR) that explains the information interactions inside of a transformer. The method can be utilized for 3 primary uses:
1. Head Pruning
2. Attribution Tree Analysis
3. Construct Adverserial Triggers

## Attention Versus Attribution Scores

**Attention score** refers to the strength of a token's relationship to all other tokens, including itself. Attention scores are calculated for each token in each attention head.

**Attribution score (Author's Method)** is taking attention score relations between two tokens but attributing the relationships to the model output. The attribution score assign higher scores if the interaction contributes more to the final prediction.

<p float="left">
  <img src="https://user-images.githubusercontent.com/89158606/198739910-bb8cece6-1c44-4c0b-931c-8b6985a08524.png" width="300" />
  <img src="https://user-images.githubusercontent.com/89158606/198739937-83af4b54-b7be-4bba-bdb3-5a769ec4bafe.png" width="300" /> 
</p>

### Question 1: Just by looking at the attention versus attribution score diagrams, what do you think are some positive and negatives to both score approaches?

## Head Pruning:

If we know the attribution scores (from ATTATTR method) for each head in the multi-head attention mechanism, some heads can then be pruned if they are not important to the model output. This will allow for better model computation with limited change to the model accuracy.

<img width="632" alt="Screen Shot 2022-10-28 at 2 45 32 PM" src="https://user-images.githubusercontent.com/89158606/198719755-2c394309-02d2-41dc-8db6-d1e6a8a3e460.png">

## Attribution Tree Analysis:

<img width="615" alt="image" src="https://user-images.githubusercontent.com/89158606/199342616-41946eed-faee-4dc9-bb31-8f04b36d7485.png">

### Question 2: Based on this tree, what conclusion do you think the model output is for sentiment analysis: positive, negative or neutral? What do you think would change in the attribution tree analysis for a different model (not BERT)? 

## Adverserial Triggers

If we understand what token relationships are critical to the model prediction, we can see that the model might be over-emphasizing and relying on certain relationships. To make the model more robust, we can test these connections by inputting triggers into other inputs and seeing if the model only focuses on the over-emphasized patterns. This can dramatically decrease the model accuracy. 

<img width="432" alt="Screen Shot 2022-10-31 at 4 42 07 PM" src="https://user-images.githubusercontent.com/89158606/199115947-0b17e885-b136-42eb-8224-41856e79cf11.png">

## Critical Analysis

What could have been developed further? 
What was overlooked by the authors?

I thought this paper was very helpful to delve into the self-attention mechanism. I thought that the pseudocode for the attribution analysis was very interesting and could have been developed futher by the authors. In fact, the authors indicate that the attribution analysis is developed further in the appendix of the paper, but I could not find an appendix anywhere online or in the PDF. This seems like an oversight where the appendix was either not developed or not included in the final paper.

I also thought that the authors could have built out the section on adverserial attacks to explain why it is helpful to perform adverserial triggers. For someone who is unfamiliar with that concept, I was not clear why we would want to attack the model in the first place. Outside research (including the video that I included in the resource links) led me to realize that it precludes others from manipulating the transformer and makes the transformer generally more robust when it is not overemphasizing certain tokens. 

## Additional Resource Links
Transformer and Self-Attention Review: 

http://jalammar.github.io/illustrated-transformer/

https://arxiv.org/abs/1706.03762

Video on Adverserial Attacks:

https://www.youtube.com/watch?v=pGSl3eHdgeo

Related Paper on Taylor Expansion Method (prior work on this topic):

https://arxiv.org/pdf/1905.10650.pdf

Related Code (Complicated Implementation):

https://github.com/YRdddream/attattr

Sourcing Note: All pictures and diagrams on the repo are sourced from the original article (https://arxiv.org/pdf/2004.11207.pdf)

## Video Recording Link: 
