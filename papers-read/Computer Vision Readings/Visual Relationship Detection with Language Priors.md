# Visual Relationship Detection with Language Priors

Stanford. Cewu Lu, Ranjay Krishna, Michael Bernstei, Li Fei-Fei

**Task:** visual relationship detection

*Problem*: skew of rare relationships because relationships are combinatorial. Need to learn with relatively few examples, then. Contrast with [6], which required enough training examples for every possible triplet.
*Proposal*: (1) learn appearance of objects and predicates separately, then fuse them together. (2) learn language model that makes use of word semantic embeddings.

     *NB stopped taking notes halfway through the paper*

## Contributions

- *New dataset*: **Visual Relationship Dataset (VRD)**
- can learn for scalable number of relationship types
- can learn for zero shot

## Bullets

- use triplets $(obj_1,pred, obj_2)$ to denote relationships
- fully supervised
- *test time*: given an image, predict multiple relationships and localize the objects

## Language Module

Project triplets into a semantic space by concatenating word2vec for the two objects and then performing a linear transform $(W,b)$. These params are learnt by minimizing variance on pairs of relationships to make distances between two relationships $f(R,W)$ proportional to the word2vec distances (between objects and predicates.
Then learn a rank loss, which the projection function $f$ generalizes to unseen triplets.

## Loss

A rank loss combines the language module and the appearance module, comparing the target triplet and the highest-ranked non-target triplet.

## TMI

- uses RCNN for object proposals at test time

## Related Work

- leveraging statistics of object co-occurence; we instead study context or relationships in which objects co-occur
- learn spatial relationships btwn objects to improve segmentation; we study spatial relationships (above, below, etc) as well as non-spatial relationships (pull, taller than, etc)
- human-object interation and action recognition work has learned discriminative parts; we are not constrained to a human being the subject
- lots of visual relationship works; we formalize VRD as a task unto itself
- Visual Phrases [6] learns a separate detector for every triplet; we separate learning appearance of individual objects and predicate
- visual phrase work (learning appearance models for visual phrases) has improved object detection; it doesn't scale to many relationships; ours also detects unseen (zero shot) relationships
  - Visual Phrases dataset has 17 common relationships types, which is few
  - Scene Graph dataset has 23,190 relationship types but only 2.3 predicates per object category; thus detecting relationships boils down to detecting objects
  - (ours) Visual Relationship dataset has 100 object categories, 70 predicates, 5000 images; 37,993 relationships with 6,672 relationship types
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQxMTY3NTI3OF19
-->