---
title: Build Probability and Surprisal Model for English Data
layout: python
post-image: "https://haerimhwang.github.io/assets/images/python.png"
description: Codes for Building Probability and Surprisal Model
tags:
- probability language model
- surprisal
- natural language processing
- python
---
* This script builds language models to compute probability and surprisal based on n-gram counts.  
<br>

* Codes
    
    * Step 1: Import modules
        
            import nltk
            from nltk.corpus import reuters
            from nltk import bigrams, trigrams
            from collections import Counter, defaultdict
            import math
            

    * Step 2: Read in corpus data that are freely available
        
            nltk.download('reuters')
                
            reuters.sents()[0:10]
   
        
    * Step 3: Create placeholders for probability and surprisal
        
            # Create a placeholder for probability model
            model_prob = defaultdict(lambda: defaultdict(lambda: 0))
            
            # Create a placeholder for surprisal model
            model_surprisal = defaultdict(lambda: defaultdict(lambda: 0))

        
    * Step 4: Count frequency of co-occurance
        
            for sentence in reuters.sents():
              for w1, w2, w3 in trigrams(sentence, pad_right=True, pad_left=True):
                model_prob[(w1, w2)][w3] += 1
                model_surprisal[(w1, w2)][w3] += 1
      
        
    * Step 5: Transform the counts to probabilities
        
            for w1_w2 in model_prob:
            total_count = float(sum(model_prob[w1_w2].values()))
              for w3 in model_prob[w1_w2]:
                model_prob[w1_w2][w3] /= total_count # probability
      
        
    * Step 6: Transform the counts to surprisal
        
             for w1_w2 in model_surprisal:
              total_count = float(sum(model_surprisal[w1_w2].values()))
                for w3 in model_surprisal[w1_w2]:
                  probability = model_surprisal[w1_w2][w3] / total_count  
                  model_surprisal[w1_w2][w3] = -math.log(probability) #-math.log(probability, 2) <-- Smith and Levy, 2013
      
    * Step 7: Test probability model
        
            model_prob['you', 'are']
       
        
    * Step 8: Test surprisal model
        
            model_surprisal['you', 'are']
            
<br>
<br>
* Reference:  
   `https://www.analyticsvidhya.com/blog/2019/08/comprehensive-guide-language-model-nlp-python-code/`  
   `https://nlpforhackers.io/language-models/`  


