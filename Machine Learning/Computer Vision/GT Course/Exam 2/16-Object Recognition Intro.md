# Object Recognition Intro
Category recognition
###### recognition via alignment
**Pro** effective when finding reliable features for clus
great results for matching specific instances
**Cons** Not suited for category recognitionnot diff view
* need to fit each object we are looking for
###### Classification now
Sematic segmentation: each pixel gets category
img classification: words that describe img
object detection: bounding boxes
instance segmentation: semantic + object
**Task**: training imgs -> class unknown
instance vs fine-grain recognition (living being)
category: mental image, similar percieved shape
**Challenges**: illumination, pose, clutter, occlusions, intra-class appearance, viewpoint, camera, robustness (objects covering), context (window)
**supervised classfication** labeled examples
measurements: mistakes, cost for mistake
risk of classifier: R(s) = Pr(4->9|using s)L(4->9)+Pr(9->4|using s)L(9->4)  /// L is cost
* want to minimize risk:
Pr(4->9|using s)L(4->9)=Pr(9->4|using s)L(9->4)
**ex**: P(class is 9|x)L(9->4) + P(class is 4|x)L(4->4) /// L(4->4) is 0
![[Pasted image 20230415215037.png|200]]![[Pasted image 20230415215046.png|200]]
when we assume x is not chaging
P(skin) = skin/total pixels //don't predict too often
p(skin|x) > $\theta$ classifies as skin 
###### Strategies
**Generative Model** training data to build representative probability model -> separately model class-conditional densities and priors
* i.e p(label) as p(skin) & p(x|label) as p(x|skin)
**Discriminative:** Directly construct a good decision boundary, model the posterior p(label|x) 
