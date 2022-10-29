---
title: Linear Mixed-Effects Regression Analysis
layout: post
categories: r
post-image: "https://haerimhwang.github.io/assets/images/r.png"
description: Codes (and explanations) for Linear Mixed-Effects Regression Analysis
tags:
- linear mixed-effects regression
- anova
- statistics
- data science 
- r
---

* This post explains basics of linear mixed-effects regression vs. ANOVA.  
         
* What makes linear mixed-effects analyses different from ANOVA?
    
    * NOVA assumes that observations are independent within and between participants and items. However, multiple responses from the same participant and those to the same item cannot be regarded as independent from each other. The way linear mixed-effects models to deal with this situation is to add random effects for participant and item. This allows us to resolve the non‑independence by assuming a different baseline value of dependent measure for each participant and item. We can model differences between participants/items by assuming different random intercepts and slopes for each participant/item.  
            
* How does a formula work?  
    
      contrast.model <- lmer(DependentMeasure ~ Factor1 * Factor2 + (1 + Factor1 * Factor2 | Participant) + (1 + Factor1 * Factor2 | item), data)
        
    * You can think of this formula as telling your model that it should expect that there are going to be multiple responses per participant and item, and these responses will depend on each participant’s baseline level and also on each item’s baseline level.  
  
* How do we interpret the results?
    
    * Take an example from my pilot study to understand how the results of mixed-effects analyses are interpreted. My pilot study investigated how Korean L2ers of English (n = 22) judged acceptability of English sentences on a 4-point scale with an additional “I don’t know” option. The critical sentences (k = 24) were distributed in a 2 × 2 Latin square design with the factors “construction” (VP-ellipsis; Gapping) and “clause” (Conjunct; Adjunct), as shown in (1)-(4).  
      
        (1) VP-ellipsis in a Conjunct Clause (VPE‑C): Sara made pizza, and Kelly did too.  
        (2) VP-ellipsis in an Adjunct Clause (VPE‑A): Sara made pizza because Kelly did.  
        (3) Gapping in a Conjunct Clause (Gapping‑C): Sara made pizza, and Kelly pasta.  
        (4) Gapping in an Adjunct Clause (Gapping‑A): \* Sara made pizza because Kelly pasta.  
          
    * In this study, “construction” and “clause” are the two independent variables. The dependent variable is z-scores that I converted from the raw acceptability judgment scores.
        
    * In the following mixed-effects model (run with a contrast coding), the two independent variables “construction” and “clause” are added as fixed effects.
        
          Haerim.model <- lmer(z-score ~ construction * clause + (1 + construction * clause | participant) + (1 + construction * clause | item), data)
        
    * Because the effects of “construction” and “clause” and their interaction might be different for different participants and items, I also added “participant” and “item” as random effects. Here, roughly speaking, the notation “(1 + construction \* clause ⦙ participant)” means that you tell the model to expect differing responses to the factors in question, which are “construction” and “clause” and their interaction in this case.

    * By adding these random effects, now I have different intercept and slopes for “construction,” “clause,” and “construction:clause” (indicating interaction between “construction” and “clause”) per participant and item as below.
        
            $participant
                    (Intercept) 	construction	clause		construction:clause
            L2A_01  −0.13035717	−1.8822782	−0.21515671	−0.14715510
            L2A_02	0.06596786	−1.7498164	−0.22280625	−0.22145612
            L2A_03	0.28485458	−1.3562880	−0.63579403	−1.24079459
            … …
            
            $item
             	(Intercept) 	construction	clause		construction:clause
            1	0.11852205	−1.292183	−0.6962850	−0.8422584
            2	0.19970942	−1.387608	−0.5917419	−0.8100677
            3	0.24531526	−1.374109	−0.5889505	−0.9270524
            … …
        
    * Simply speaking, the intercept means a grand mean of z-scores given by each participant and item. (This is not true when you run a mixed-effects model with other coding options, such as a dummy coding. I will come back to this point.) The following slope value, termed as a coefficient, under the third column “construction” can be regarded as a difference between z‑scores for Gapping and those for VPE.

    * What is important for us is that the column with the coefficients for the effect of “construction,” “clause,” and their interaction is different for each participant and item. However, there is also some consistency in how “construction” affects the z‑scores despite the variation across participants and items. For example, the coefficients for “construction” across participants are always negative and many of the values are quite similar to each other. Specifically, for all participants, z-score tends to go down in the case of Gapping, but for some people it goes down slightly more so than for others (compare L2A\_01 vs. L2A\_03).

    * Before turning to the interpretation of the results, see Figure 1 for the overall results of this pilot study. This figure shows acceptability z‑scores by condition.

    * When we run the model with a contrast coding, we get the results for random effects as below.
        
            Random effects:
            Groups			Name			Variance	Std.Dev.	Corr 
            participant	  	(Intercept)		0.040101	0.20025 
                         		construction		0.150601	0.38807		0.80 
                         		clause			0.160550	0.40069		−0.61	−0.87
                         		construction:clause	0.477556	0.69105		−0.85	−0.80
            item			(Intercept)		0.009452	0.09722 
                         		construction		0.007289	0.08537		−0.45
                          		clause			0.007876	0.08875		0.70	−0.95
                          		construction:clause	0.036609	0.19134		−0.60 	−0.45
            residual					0.168750	0.41079		0.16	0.76
        
    * This is a measure of how much variability in the dependent measure there is due to participants and items, which are our random effects. You can see that item has much less variability than participant. At the very bottom, you see “residual” which stands for the variability that is not due to either participant or item.

    * Now, let’s take a look at the results of the model that we built (again, with a contrast coding).
        
            Fixed effects:
            				Estimate	Std. Error  df		t value		Pr(>|t|)
            (Intercept)		        0.20417	    	0.05044	    27.42000	4.047		0.000381***
            construction			−1.32417	0.09212	    22.78900	−14.375	  	6.47e-13***
            clause				−0.64325	0.09471	    22.83400	−6.792		6.55e-07***
            construction:clause		−0.94653	0.16904	    23.47700	−5.599		9.94e-06***

    * Here, the intercept means a grand mean of the z-scores of my data. (cf. In the model built by a dummy coding, the intercept value indicates the mean of a certain condition/level that was automatically set as a reference level/condition. Such a model built in R takes whatever comes first in the alphabet to be the reference level/condition.)
        
    * The coefficient (often noted as Estimate or b) of “construction” is the slope for the categorical effect of “construction.” This means that to go from “VPE” to “Gapping”, you have to go down 1.32417. In other words, an acceptability judgment score is lower in Gapping than in VPE, by about 1.32.
        
    * The coefficient “construction:clause” indicates a difference within one factor minus a difference within the other factor. We can obtain -0.94653 by subtracting (VPE-A − VPE-C) from (Gapping-A − Gapping-C).

    * Then, there is a standard error associated with this slope. A t-value is simply the estimate divided by the standard error.
    
