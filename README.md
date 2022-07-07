# Abstract:

Ce projet traite du problème des attaques adverses sur des systèmes de reconnaissance faciale. Il s'agit d'un domaine pour lequel les activités de recherches sont très actives dans la mesure où les systèmes de reconnaissance faciale sont de plus en plus utilisés comme méthodes d'authentification.

La première partie de cette étude consistera à développer un classifieur $C$. Ce classifieur $C$ doit retrouver l'identité d'une personne figurant sur une image (*face identification*). La configuration *closed-set* sera utilisée : toutes les identités dans l'ensemble de test sont présentes dans l'ensemble d'entraînement.

La deuxième partie portera sur la conception d'un modèle adverse $A$ qui attaque les images fournies au classifieur $C$.  $A$ doit générer un bruit $B_{pert}$, qui fausse la classification de $C$, tel que la différence entre l'image perturbée $I_{pert} = I_{origin} + B_{pert}$ et l'image d'origine $I_{origin}$ ne soit pas perceptible à l'oeil nu.

Pour ce projet, j'ai choisi d'utiliser framework PyTorch ainsi que le jeu de données LFW (*Labeled Faces in the Wild*) qui contient 13233 images de visages de 5749 personnes.

---------------------------------

Les parties **Chargement des données**, **Analyse de la distribution du jeu de données** de ce notebook peuvent être lancées directement. 

La partie **Entrainement** contient les blocs de codes pour l'entrainement des classifieurs ad hoc et pré entrainés. Les paramètres des modèles entrainés ont été stockés dans des fichiers au format .pt :


*   classifier_adhoc.pt : paramètres du classifier ad hoc entraîné
*   classifier_adhoc_with_noise.pt : paramètres du classifier ad hoc entraîné avec un bruit gaussien additif
*   pretrained_classifier_vgg16 : paramètres du classifier pré-entraîné VGG16
*   robust_classifier_adhoc.pt : paramètres du classifier entraîné avec des attaques adverses (adversarial training)


La partie **Attaques** commence par le chargement des paramètres des modèles entrainés à partir des fichiers .pt. Elle traite ensuite de l'évaluation des modèles ainsi que des attaques.
