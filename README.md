# TP-Admin-ClientServeur-
TP Admin Client-Serveur 
● Installation et configuration d’un hyperviseur 
● Création des microservices 
● Mise en place d’une solution de réplication

Dand notre projet docker est installé sur serveur linux (ubuntu)
Conteneur ?
la virtualisation par conteneurs se base sur la virtualisation Linux(LXC)

il sagit d'une methode de poisennement au niveau de L'OS 
=> le principe est de faire ourner des environnements linux isolé dans des containers partageons le meme noyaux vx dire conrairement au VM 
--------------------------
| Conteneur 1| conteneur 2|
 --------------------------
 --------------------------
|     LXC (controleur)    | 
---------------------------
|        Linux kernel     |
---------------------------
|         Hradware        |
---------------------------

VM: s'appuient sur les foncionnalité de l'OS de la machine hote
CONTAINER : accedent au os indépendamment = isolé

 --------------------------
|   APP 1     |     APP 2  |
| ---------   | ---------- |
| Dépendances |Dépendances |
 --------------------------
 --------------------------
|     LXC (controleur)    | =>gere un ensembles de function pour conteneurs
---------------------------
|        Linux kernel     |
---------------------------
|         Hradware        |
---------------------------

Le container virtualise lenvirennement de virtualisation comme processeur, memoire, susteme de fichier, et ne virtualise pas la miche


LXC se base sur 2 fonctionnalité du noyaux linux:
1- Control groups : limiter et isoler l'utilisation des ressources. donner des % pour chaque container
2- Name space : empcher un groupe de voir les ressources dun autre groupe

**La virt par containers caracterisé par la couche intermedaire du controleur
foncionalité pour le conteneur gérer par le controleur : 
-------------------
1. les interaction de conteneur avec l'OS
2. la securité par la gestion de privileges et de ressource, la scalibilité= la duplication et la suppression des conteneurs, laccesibilité des conteneur a travers la gestion des API


**le cont plus vacile a gerer, a dupliquer, sauvgarder, restorer
**La virt avec des conteneur permet au serveur dheberger bcp plus de container par rapport au vm
les app vont etre executer au sein de l'os hote mais de maniere virtuellement isolé

**docker engine: 
 --------------------------
|   APP 1     |     APP 2  |
| ---------   | ---------- |
| Dépendances |Dépendances |
 --------------------------
 --------------------------
|     docker engine       |=>fait tourner les conteneurs, joue le role de controleur
---------------------------
|        OS hote          |
---------------------------
|         Hradware        |
---------------------------

Docker fonctionne sur une architecture (client/server)
le client docker =====> communique avec docker deamon qui fait tourer le docker engine

** Image :  on doit empiler plusieur images docker

-------------  --------------
|Img debian |  | Img ubuntu |
-------------  --------------
|Img debian |  | Img ubuntu |
---------------------------
|      kernel linux        |
---------------------------

Avantage docker: 
permet dexploiter et de faciliter le deploiment



* Exposition des port : ( reseau)
    Les microservices s'exécutent généralement à l'intérieur de conteneurs Docker, qui sont des instances isolées et légères d'applications. Chaque conteneur peut exposer un ou plusieurs ports pour permettre aux autres services ou utilisateurs d'accéder aux fonctionnalités fournies par ce microservice spécifique.

* Pour exposer un port d'un conteneur Docker, vous devez spécifier la configuration appropriée lors du démarrage du conteneur. Lorsque vous exécutez la commande docker run, vous pouvez utiliser l'option -p (ou --publish) pour lier un port du conteneur à un port de l'hôte (le système sur lequel Docker s'exécute).
