---
title: Tag English Words for Part-of-Speech
layout: pythonpost
pythonpost-image: "https://haerimhwang.github.io/assets/images/python.png"
description: Codes for Part-of-Speech Tagging
  
tags:
- Natural Language Processing
- English
- Part-of-Speech tagging

---

* This script marks up each word in a text as corresponding to a particular part of speech.

<br> 
<br>
<br>

* Codes

  - Step 1: Import modules

    ```
    import nltk
    nltk.download('punkt')
    nltk.download('averaged_perceptron_tagger')
    ```
    <br>
    <br>
  
  - Step 2: Tag each word for its part-of-speech
  
    ```  
    sentence = "You are right that I need to send it to him soon."
    tokens = nltk.word_tokenize(sentence)
    tagged = nltk.pos_tag(tokens)
    ```    
    <br>
    <br>   

  - Step 3: Check output

    ```
    tagged
    ```

<br>
<br>

---
