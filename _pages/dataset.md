---
layout: default
title: ProBio | Dataset
permalink: /dataset.html
mathjax_autonumber: true
---


# ProBio Dataset

## Overview
We present **ProBio**, the first protocol-guided multimodal dataset in BioLab to tackle the above challenges. **ProBio** provides 
- (i) a meticulously curated set of detailed and standardized protocols with corresponding video recordings for each experiment
- (ii) a natural and systematic evaluation framework for fine-grained multimodal activity understanding.
We construct **ProBio** by selecting a set of 13 frequently conducted experiments and augmenting existing protocols by incorporating three-level hierarchical annotations. This configuration yields 3,724 practical-experiment instructions and 37,537 Human-Object Interaction (HOI) annotations with an overall length of 180.6 hours. 

In light of the significant disparities observed between human and model performance in action recognition, we devise diagnostic splits that stratify experimental instruction into three categories based on difficulties (*i.e.*, easy, medium, hard). We hope **ProBio** and associated benchmarks will foster new insights to mitigate the reproducibility crisis in BioLab and promote fine-grained multimodal video understanding in computer vision.


## Protocol Format


```python
{
    "images":[{
        "date": int, 
        "camera_id": int,
        "video_id": str,                                 # camera id_challenge id_task_id
        "file_name": str,                                # 00000000.jpg
        "image_id": int,                      
        "frame_id": int,                                 # the frame number of the given video
        }, 
        …,                                               # all frames
    ],
    "objects":[{
        "image_id": int, 
        "object_category": list of int                   # index of object_list,
        "object_polygon": [[[x1, y1], [x2, y2],…], …]， 
        "object_id": list of int,                        # the corresponding id in 'object_polygon'
        "solution_category": [[id, category], ...],      # liquid 'category' in the 'id'th object
        },
        …,                                               # all frames
    ],
    "protocols": str
}
```

## Ambiguity

We define ambiguity between two actions with the bidirectional Levenshtein distance ratio, as shown in Equation \eqref{a}. In Equation \eqref{a}, $$P(A)$$ and $$P(B)$$ represent the power set of the given $$A$$ or $$B$$ set of hoi, while ratio denotes the Levenshtein distance ratio. The ambiguity (i.e. $$amb$$) between two practical experiments can exceed 1, which represents a high similarity between the two prc\_exp. Afterward, in order to measure the average ambiguity of each action, we define it by taking the average value (i.e. $$\frac{1}{N} {\sum \limits_{amb\in N} amb_i}$$).


$$amb=\frac{1}{P(A)}*\sum \limits_{x\in P(A)}{\underset{y\in P(B)}{\max}(ratio(x, y))} + \frac{1}{P(B)}*\sum \limits_{y\in P(B)}{\underset{x\in P(A)}{\max}(ratio(y, x))} \label{a}$$




{% include mathjax.html %}



