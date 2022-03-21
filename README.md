# Federated Learning : vers du Machine Learning plus respectueux de la vie privée ?

## Table des matières
1. [Introduction à l'apprentissage fédéré et premiers concepts](#Introduction à l'apprentissage fédéré et premiers concepts)
2. [Cas d'usages connus de l'apprentissage fédéré](#Cas d'usages connus de l'apprentissage fédéré)
3. [Apprentissage fédéré et respect de la vie privée](#Apprentissage fédéré et respect de la vie privée)
4. [Variantes et améliorations proposées](#Variantes et améliorations proposées)

## Introduction à l'apprentissage fédéré et premiers concepts
L'apprentissage fédéré est une technique d'apprentissage automatique proposée par Google en 2016 dans l'article [Communication-Efficient Learning of Deep Networks
from Decentralized Data](http://proceedings.mlr.press/v54/mcmahan17a/mcmahan17a.pdf), permettant l'apprentissage automatique à partir de données décentralisées, sans transférer les données. L'un des principaux arguments pour cette technique est que l'apprentissage fédéré serait plus respectueux de la vie privée. Dans cette veille, nous allons introduire le sujet, et présenter des ressources permettant de se faire une meilleure idée du sujet, et de répondre à cette question.

Pour une introduction très légère, Google a créé une [bande dessinée en ligne](https://federated.withgoogle.com/), permettant de découvrir le sujet de manière ludique. Pour en savoir un petit peu plus sans toutefois rentrer dans le détail de l'implémentation, Google AI a publié un billet de blog [
Federated Learning: Collaborative Machine Learning without Centralized Training Data ](https://ai.googleblog.com/2017/04/federated-learning-collaborative.html) permettant une bonne introduction au sujet.

Dans un [article de journal en coopération avec le Wall Street Journal](https://deloitte.wsj.com/articles/keeping-ai-private-homomorphic-encryption-federated-learning-01644518384), l'entreprise présente son point de vue sur pourquoi cette technologie (couplée à une technique que nous présenterons plus bas) sera très importante dans le futur, notamment pour répondre aux contraintes liées aux lois type RGPD.


## Cas d'usages connus de l'apprentissage fédéré
Dans cette section, nous allons voir des ressources permettant de mieux comprendre les cas d'usage de l'apprentissage fédéré. De nombreuses entreprises revendiquent utiliser l'apprentissage fédéré, mais ne communiquent pas dessus. D'autres secteurs pourraient en profiter (banques, assurances, mutuelles, justice, autorités financières, constructeurs de smartphones, ), mais pas de réelle application est connue à ce jour.

### Cas d'usages sur mobiles
Les GAFAM sont les principaux utilisateurs actuels de l'apprentissage fédéré. Les données décentralisées apparaissent naturellement sur les smartphones, c'est pourquoi Google et Apple en sont particulièrement friands.

#### Google

- [Clavier intelligent GBoard : Prédiction du prochain mot](https://research.google/pubs/pub47586/)
- [Clavier intelligent GBoard : Autocorrection par N-grammes](https://research.google/pubs/pub48709/)
- [Clavier intelligent GBoard : Suggestions automatiques](https://research.google/pubs/pub47655/)
- [Clavier intelligent GBoard : Prédiction du prochain émoji](https://research.google/pubs/pub48270/)
- [Clavier intelligent GBoard : Découverte de nouveaux mots dans le clavier GBoard](https://research.google/pubs/pub49223/)
- [Fonction "Ok Google"](https://research.google/pubs/pub49696/)
- [Remplacement du cookie tiers : Federated Learning of Cohorts (FLoCs)](https://github.com/google/ads-privacy/tree/master/proposals/FLoC)

#### Apple
- [Fonction "Dis Siri" : Reconnaissance automatique de la voix du détenteur du Smartphone](https://machinelearning.apple.com/research/improving-on-device-speaker)
- [Autres applications : recommandation automatique de news, prédiction d'émojis, détection de ressources consommatrices d'énergie dans Safari...](https://machinelearning.apple.com/research/federated-personalization)

[Cet article](https://www.technologyreview.com/2019/12/11/131629/apple-ai-personalizes-siri-federated-learning/) parle de l'utilisation de l'apprentissage fédéré par Apple.

#### Amazon
[Modèle de reconnaissance automatique de parole](https://www.amazon.science/publications/cross-silo-federated-training-in-the-cloud-with-diversity-scaling-and-semi-supervised-learning)

#### Nvidia
Nvidia utilise l'apprentissage fédéré pour des applications médicales grâce à son framework Clara FL, tout en préservant la confidentialité des données. Le détail de l'architecture employé est accessible dans leur [article de blog](https://blogs.nvidia.com/blog/2019/12/01/clara-federated-learning/).

#### Owkin
Owkin est une start-up française qui implémente des modèles d'apprentissage fédéré pour exploiter les données décentralisées des hôpitaux. Dans [un billet de blog](https://owkin.com/publications-and-news/blogs/federated-learning-in-healthcare-the-future-of-collaborative-clinical-and-biomedical-research), la start-up présente sa vision de l'apprentissage fédéré dans le domaine médical. Dans un [autre billet de blog très intéressant](https://owkin.com/publications-and-news/blogs/story-of-the-1st-federated-learning-model-at-owkin), elle présente également comment ils ont implémenté leur premier modèle d'apprentissage fédéré pour la santé.

## Apprentissage fédéré et respect de la vie privée
En l'état, l'apprentissage fédéré n'est pas totalement respectueux de la vie privée, [cet article](https://www.kdnuggets.com/2020/08/breaking-privacy-federated-learning.html) permet de mieux comprendre pourquoi. Plusieurs techniques permettent de pallier ces défaillances : la méthode d'aggrégation des gradients des clients peut être rendue plus robuste, selon la méthode développée dans [cet article](https://research.google/pubs/pub45808/). On peut ajouter des techniques dites de differential privacy, comme on peut l'étudier dans le [cours d'Aurélien Bellet](http://researchers.lille.inria.fr/abellet/teaching/private_machine_learning_course.html) à l'université de Lille. Apple a également publié [un article](https://machinelearning.apple.com/research/learning-with-privacy-at-scale) pour illustrer comment la differential privacy est utilisée dans leurs services. Une couche d'encryption homéomorphique est fréquemment ajoutée, [cet article de Nvidia](https://developer.nvidia.com/blog/federated-learning-with-homomorphic-encryption/) permet d'en apprendre plus à ce sujet.

Un champ de recherche actif de l'apprentissage fédéré est l'étude de sa robustesse aux attaques. Cela peut être une attaque d'un client prenant part à l'apprentissage, comme une attaque du serveur. Cela peut être des attaques franches, ou simplement voir la quantité d'information à laquelle un agent non-malicieux mais curieux peut accéder. Ce [thread twitter](https://twitter.com/jonasgeiping/status/1495803744054910981), ainsi que le [repo GitHub associé](https://github.com/JonasGeiping/breaching) sont très instructifs à ce sujet. Le site KDNuggets propose également [un article](https://www.kdnuggets.com/2020/08/breaking-privacy-federated-learning.html) permettant de mieux comprendre cette thématique sans se plonger dans le code ou les articles de recherche.



## Variantes et améliorations proposées

### Federated Learning at scale et personnalisation
Google a publié [un article de recherche](https://research.google/pubs/pub47976/) sur la gestion d'un modèle d'apprentissage fédéré à une échelle de production avec des millions d'appareils. On peut notamment y lire l'architecture employée, la gestion des connexions/déconnexions, la manière d'évaluer le modèle, quand et comment faire les mises à jour du modèle. Un tel papier est unique car peu d'entreprises ont les moyens de mettre en place des modèles de cette ampleur.

Apple a également révélé dans [un article](https://machinelearning.apple.com/research/federated-personalization) sa manière d'implémenter certains modèles d'apprentissage fédéré, plutôt sur l'axe de l'évaluation des performances, et de la personnalisation des modèles pour l'utilisateur final. Cet article est volontairement un complément à celui de Google, et les deux articles donnent de précieux éclaircissements sur comment implémenter de tels modèles à l'échelle.

### Apprentissage fédéré en peer-to-peer ou avec blockchain
Une variante de l'apprentissage fédéré classique est le cas ou il n'y a pas de serveur central pour agréger les mises à jour de modèles locaux. Les mises à jour sont faites en peer-to-peer. De nombreux développements ont été effectués sur cette configuration, notamment [cet article](https://arxiv.org/abs/1901.11173). Les [slides de Aurélien Bellet](http://researchers.lille.inria.fr/abellet/talks/privacy_preserving_decentralized_machine_learning.pdf) sont également une source de grande qualité à ce sujet.

D'autres développements couplent l'apprentissage fédéré à des techniques de Blockchain, dans le but de valider les mises à jour locales, et grantir plus de traçabilité à l'apprentissage du modèle. On peut par exemple citer [cet article](https://ieeexplore.ieee.org/abstract/document/8843900?casa_token=GddC705-1lcAAAAA:3i-kxCkDRr0dj1ivHwpJ82aY-v2c24AIdVy1j5b7b16GANQbCGoBLA_lvyEeV4CjlyuiZ3kF1xrIfQ), qui couple l'apprentissage fédéré à la blockchain pour des applications IOT.
