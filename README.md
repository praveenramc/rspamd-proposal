## Corpus testing and Automatic Symbol Score Generation

**Name:** Pragadeesh C  
**Email:** cpragadeesh@gmail.com  
**Github:** [cpragadeesh](http://www.github.com/cpragadeesh)  
**University:** Amrita University  
**Course:** B.Tech (Honors) in Computer Science  
**Course Year:** 3rd Year  
**Country:** India  
**Timezone:** GMT +5.30 (IST)  

---

## Proposal
This project aims to build a module for nightly automatic re-scoring of Symbol Scores by training the Neural Network on a corpus of spam and ham.

### Abstract

Symbol scores are the determining factor for the action recommendation for an email. Currently, symbol scores are either set to default or set manually. These scores are generally set based on human judgement. This leaves a space for improvement. This project aims to use Artificial Neural Networks to re-score the weights automatically to reduce the False Positives and False Negatives in the classification of spam and ham.

### Deliverables

At the end of this project, a module capable of automatically learning from the spam and ham corpus and re-score the weights, nightly will be made available for Rspamd.

## Implementation

### Overview
The project can be divided into three major tasks: Corpus Testing, Neural Networks, Automation, Testing & Documentation.  
* #### Corpus Testing
    Shell scripts will be developed for feeding a corpus of spam and ham messages into rspamd, the results generated will be used to prepare a dataset(used to train our Neural Networks) and also generate statistics for evaluation purpose.

* #### Neural Networks
     This task involves using the dataset produced from the previous task to train and compute the ideal scores for each symbol which will reduce the False positives and False Negatives.

* #### Automation, Testing & Documentation
    This task will provide a way to configure the automation of previous two tasks, test the module in various environments, document the module.  

### Discussion
##### Corpus Testing
Corpus testing is pretty straight forward. It will be accomplished using  shell scripts. The First shell script will be a logging script that logs all the Symbols and scores associated with each message by running the corpus through rspamd using `rspamc` command. The logs generated by this script would then be processed by a pre-processing script to create a dataset that would be fed into the Neural Network. Also, the logs generated will be used to generate statistics of Hit-Rate, False positives and False negatives. By analyzing the statistics generated, the symbols which do not hit enough messages and symbols which hit the wrong type of messages will be suggested for removal from the rules and excluded from the dataset.

##### Neural Networks
A Perceptron will be used as our neural network. A Perceptron will take in inputs through various nodes, perform a linear combination of these inputs and feed the value into an activation function and then output a Binary value.

In our case, each input node will represent a Symbol. For a particular message, The input vector will consist of a series of 0s and 1s (0 if the symbol was not associated with the message, 1 if the symbol was associated with the message). The weight of each input node will represent the score of each Symbol. A bias value is added to the linear combination of the input and the weights. So, in effect the Perceptron's input will be:

> h(message) = sum(Xi * Wi) + Bias  
  Xi = ith value of Input vector (0 or 1)  
  Wi = Score of ith Symbol  

Clearly, if the bias is set to 0, this formula is same as the one that is used to calculate the message score. The message score will be the sum of the scores of each symbol that is associated with a message.

The input of Perceptron would then be passed onto an activation function. Our choice of activation function would be the Sigmoid function. So the final result would be:

> g(h(m)) = Sigmoid(h(m))

For learning phase, the error will be computed using Mean-Square error. Stochastic Gradient Descent algorithm would then be used to update the weights so as to minimize the error. Stochastic Gradient Descent is used to converge fast and is computationally less expensive compared to regular Gradient Descent. The weights will be updated as follows:

> error(m) = g(m) * (1-g(m)) * (g_expected - g(m))  
  Wi = Wi + error(m) * Xi * learning_rate

After training the neural network on the training set, the final scores will be calculated as follows:

> score(w) = -scale * w / bias


##### Automation, Testing and Documentation
The user will be provided various options such as an upper bound for the score, the frequency of re-scoring, etc. The module will be tested on various UNIX flavors. An overview of the module and configuration options will be documented.

## Timeline Breakdown

##### Community Bonding Period: May 5 - May 27  
* Communicate with the mentor to get feedback on the workflow.
* Get familiar with the existing codebase to understand common design patterns and techniques.
* Read various literature on Neural Network optimization.
* Finalize the workflow.

##### Week 1: May 28 - June 3
* Write scripts to scan corpus and generate results using rspamc.
* Write scripts to preprocess results and filter out the required data.

##### Week 2: June 4 - June 10
* Write statistics generation script.
* Write scripts to convert log files into dataset for C module.

##### Week 3: June 11 - June 17
* Implement scratch Neural Network.
* Write visualization scripts.
* Experiment with different Neural Network configs.

##### Week 4: June 18 - June 24
* Finalize the best possible Neural Network config.
* Begin implementing production Neural Network.

##### Week 5: June 25 - July 1
* Finish implementing production Neural Network.
* Write re-scoring scripts, post re-scoring statistics scripts.

##### Week 6: July 2 - July 8
* Write scripts to automate nightly re-scoring.

##### Week 7: July 9 - July 15
* Test the module.
* Document the module.

##### Week 8: July 16 - July 22
* Test Neural Network on different environments.
* Fix bugs.

##### Week 9: July 23 - July 29
* Continue testing Neural Network on different environments and Fix bugs.

##### Week 10: July 30 - August 5
* Get code review and prepare for PR
* Polish the code as required

##### Week 11: August 6 - August 12
* Buffer week

##### Week 12: August 13 - August 19
* Buffer week
* Prepare for final evaluation.

#### Other commitments

My University's Finals are scheduled from May 13 - May 27. During these 2 weeks, I might not be able to spend 40 hours/week. However, during other weeks, I can work up to 50 hours/week. Apart from this, I might take a break for 3-4 days, in which case, I will inform the mentor a week prior.

## About me

I am Pragadeesh C, from India. I am pursuing my Undergraduate in Computer Science from Amrita University. I am very passionate about AI/Machine learning. I derive my inspiration from Andrew Ng. Humans spend a lot of time doing mundane tasks like driving, being stuck in traffic, and performing other routine activities(reading spam?). I believe that we could spend a lot of time on other important tasks if we could use AI to automate these mundane activities. This is what drives me.

I am thrilled about contributing to Open Source in general. I am especially very excited about the impact that I could create by contributing to Rspamd. Furthermore, Being the pragmatist I am, I have been waiting to put my skills to use in real world. I believe that this would be a very good opportunity for me.

#### Experience

I have completed an online course in Machine Learning by Andrew Ng in Coursera. I have worked through the course materials which covered various programming tasks that involved Neural Networks, Spam classification, etc. Apart from the coursework, I have built a Recommendation system using Netflix dataset. [Source](https://github.com/cpragadeesh/Recommendation-System). Used unsupervised learning to detect Twitter troll farms. [Source](https://github.com/cpragadeesh/troll-farm-detection).

Apart from these, I have built several projects. I built a Web platform for debugging contests using Django. [Source](https://github.com/cpragadeesh/coldcoffee), Built a command line interface for automating testing for online algorithmic contests conducted in codeforces.com using Python. [Source](https://github.com/cpragadeesh/codeforces-cli).

I learnt C in my highschool. For introductory course project, I developed a project that imitated an interpreter. It was capable of performing basic commands. [Source](https://github.com/cpragadeesh/nice). 

I learnt Lua for modifying a MOD for a game called [MTA SA](https://www.mtasa.com) in my highschool. Although I have been a little out of touch, I could pick up Lua very easily since I have used other scripting languages like JS, Python, etc.

I believe that I have sufficient knowledge of C to complete this project. I am confident that I could pick up whatever skills this project requires and complete it.

#### Contributions

*Plugin improvement*
* DMARC: Report if a message was sampled_out  

  _([Link](https://github.com/vstakhov/rspamd/pull/1570))_

*Test improvement*  
* lua_html content extraction  

  _(Working on it, Will send a PR soon)_
