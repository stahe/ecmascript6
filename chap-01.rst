Présentation du cours
=====================

Ce document fait partie d’une série de quatre articles :

1. [`Introduction au langage PHP7 par
   l’exemple <https://stahe-php7.readthedocs.io/fr/latest/>`__] ;

2. [`Introduction au langage ECMASCRIPT 6 par
   l’exemple <https://stahe-ecmascript6.readthedocs.io/fr/latest/>`__].
   **C’est le document présent** ;

3. [`Introduction au framework VUE.JS par
   l’exemple <https://stahe-vuejs.readthedocs.io/fr/latest/>`__] ;

4. [`Introduction au framework NUXT.JS par
   l’exemple <https://stahe-nuxtjs.readthedocs.io/fr/latest/>`__] ;


Ce sont tous des documents pour **débutants**. Les articles ont une
suite logique mais **sont faiblement couplés** :

-  le document [1] présente le langage PHP 7. Le lecteur seulement
   intéressé par le langage PHP et pas par le langage Javascript des
   articles suivants s’arrêtera là ;

-  les documents [2-4] visent à construire un client Javascript au
   serveur de calcul de l’impôt développé dans le document [1] ;

-  les frameworks Javascript [vue.js] et [nuxt.js] des articles 3 et 4
   nécessitent de connaître le Javascript des dernières versions
   d’ECMASCRIPT, celles de la version 6. Le document [2] est donc
   destiné à ceux qui ne connaissent pas cette version de Javascript. Il
   fait référence au serveur de calcul de l’impôt construit dans le
   document [1]. Le lecteur de [2] aura alors parfois besoin de se
   référer au document [1] ;

-  une fois ECMASCRIPT 6 maîtrisé, on peut aborder le framework VUE.JS
   qui permet de construire des clients Javascript s’exécutant dans un
   navigateur en mode SPA (Single Page Application). C’est le document
   [3]. Il fait référence à la fois au serveur de calcul de l’impôt
   construit dans le document [1] et au code du client Javascript
   autonome construit en [2]. Le lecteur de [3] aura alors parfois
   besoin de se référer aux documents [1] et [2] ;

-  une fois VUE.JS maîtrisé, on peut aborder le framework NUXT.JS qui
   permet de construire des clients Javascript s’exécutant dans un
   navigateur en mode SSR (Server Side Rendered). Il fait référence à la
   fois au serveur de calcul de l’impôt construit dans le document [1],
   au code du client Javascript autonome construit en [2] ainsi qu’à
   l’application [vue.js] développée dans le document [3]. Le lecteur de
   [4] aura alors parfois besoin de se référer aux documents [1] [2] et
   [3] ;

La dernière version du serveur de calcul de l’impôt développée dans le
document [1] peut être améliorée de diverses manières :

-  la version écrite est centrée sur le serveur. La tendance est
   désormais (juillet 2019) au client / serveur :

   -  le serveur fonctionne en service jSON ;

   -  une page statique ou non est le point d’entrée de l’application
      web. Cette page contient du HTML /CSS mais aussi du Javascript ;

   -  les autres pages de l’application web sont obtenues dynamiquement
      par le Javascript :

      -  la page HTML peut être obtenue par assemblage de fragments
         statiques, fournis par le même serveur qui a fourni la page
         d’accueil ou bien entièrement construite par le Javascript ;

      -  ces différentes pages affichent des données qui sont demandées
         au service jSON ;

Ainsi le travail est réparti sur le client et le serveur. Le serveur
ainsi déchargé peut servir davantage d’utilisateurs.

L’architecture correspondant à ce modèle est le suivant :

|image0|

**JS** : Javascript

Le code javascript est client :

-  d’un service de pages ou fragments statiques ou non ;

-  d’un service jSON ;

Le code Javascript est donc un client jSON et à ce titre peut être
organisé en couches **[UI, métier, dao]** (UI : User Interface) comme
l’ont été nos clients jSON écrits en PHP. Au final, le navigateur ne
charge qu’une unique page, la page d’accueil. Toutes les autres sont
obtenues et construites par le Javascript. On appelle ce type
d’application **SPA** : **S**\ ingle **P**\ age **A**\ pplication ou
encore **APU** : **A**\ pplication à **P**\ age **U**\ nique.

Ce type d’application fait également partie des applications dites
**AJAX** : **A**\ synchronous **J**\ avascript **A**\ nd **X**\ ML

-  **Asynchronous** : parce que les appels du client Javascript au
   serveur jSON sont asynchrones ;

-  **XML** : parce que XML était la technologie utilisée avant
   l’avènement du jSON. On a cependant gardé l’acronyme AJAX ;

Nous allons étudier une telle architecture dans les chapitres à venir.
Côté client, nous utiliserons le framework Javascript **[Vue.js]**
**[https://vuejs.org/]** pour écrire le client Javascript du serveur
jSON PHP que nous avons écrit dans le document [1].

**[Vue.js]** est un framework Javascript. Pour le comprendre, il faut
maîtriser ce langage. Nous présentons dans ce document la norme
ECMAScript 6 qui est la normalisation la plus récente (en 2019) de ce
langage. On trouvera l’historique et le rôle d’ECMAScript sur Wikipedia
**[https://fr.wikipedia.org/wiki/ECMAScript]**.

Ce document propose une liste de **scripts console** Javascript dans
différents domaines (structures du langage, accès aux bases de données,
au réseau internet, programmation en couches, programmation par
interfaces). Le document se termine avec deux applications :

**Une application console** qui sera un client du serveur de calcul de
l’impôt construit dans le document [1]. Ce client aura la même
architecture que celle du client console PHP construit dans le document
[1] :

|image1|

-  les couches [7-9] seront celles du client Javascript s’exécutant dans
   une console ;

-  les couches [1-4] sont celles du serveur PHP 7 construit dans le
   document [1] ;

-  contrairement au client PHP console construit dans le document [1],
   il n’y aura pas d’interactions avec le système de fichiers local
   [6] ;

On a là une application client / serveur où le client est une
application console. Une seconde application sera écrite où le code des
couches [7-9] **sera porté dans un navigateur**. Nous serons alors prêts
à aborder les frameworks Javascript des navigateurs dans les documents
[3] et [4].

Les scripts de ce document sont commentés et leur exécution console
reproduite. Des explications supplémentaires sont parfois fournies. Le
document nécessite une lecture active : pour comprendre un script, il
faut à la fois lire son code, ses commentaires et ses résultats
d'exécution.

Les exemples du document sont disponibles
\|\ `ici <http://sergetahe.com/cours-tutoriels-de-programmation/wp-content/uploads/documents/php7-ecmascript6-vuejs-nuxtjs/ecmascript6.rar>`__\ **\ \|**.

L’application serveur PHP 7 peut être testée
\|\ `ici <https://sergetahe.com/apps/impot/serveur-php7/>`__\ **\ \|**.

Serge Tahé, octobre 2019

.. |image0| image:: ./chap-01/media/image1.png
   :width: 5.83071in
   :height: 1.81496in
.. |image1| image:: ./chap-01/media/image2.png
   :width: 5.28346in
   :height: 2.03937in
