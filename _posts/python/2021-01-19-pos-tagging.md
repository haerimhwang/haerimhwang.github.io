---
title: Tag English Words for Part-of-Speech
layout: post
categories: python
post-image: "https://haerimhwang.github.io/assets/images/python.png"
description: Codes for Tagging English Words for Part-of-Speech
tags:
- part-of-speech 
- syntactic category
- natural language processing
- google colab
- python
---

* This script marks up each word in a text as corresponding to a particular part of speech.
<br>
<br>

* Codes
    
    * Step 1: Import modules
        
          import nltk
          nltk.download('punkt')
          nltk.download('averaged_perceptron_tagger') 
          
    <br>
    
    * Step 2: Tag each word for its part-of-speech
        
          sentence = "You are right that I need to send it to him soon."
          tokens = nltk.word_tokenize(sentence)
          tagged = nltk.pos_tag(tokens)    
          
    <br>
    
    * Step 3: Check output

          tagged
          
<br>
<br>
