Web app offline
===============
Merci à [@verekia](http://twitter.com/#!/verekia) pour son article sur [html5-css3.fr](http://www.html5-css3.fr)

Ici l'article d'origine pour lui dire un petit merci: *[source](http://www.html5-css3.fr/html5/tutoriel-application-web-offline-html5-cache-manifest)*.

La page HTML
------------
Afin d’utiliser le cache d’application, il va falloir déclarer un fichier manifest.
Ce fichier se déclare dans la balise html comme ceci :

    <html manifest="site.manifest">
    
    </html>

Le manifest
-----------
Une fois déclaré, il faut bien sûr créer le fichier manifest en question. Appelons le nôtre “site.manifest”.
Dans ce fichier, qui commence obligatoirement par la ligne “CACHE MANIFEST”, nous allons déclarer les fichiers qui doivent être mis en cache.

Il est possible d’ajouter différentes sections à notre fichier manifest:

* CACHE, il s’agit de la section par défaut qui liste les fichiers à mettre en cache.
* NETWORK, qui liste les fichiers qui nécessitent obligatoirement une connexion internet.
* FALLBACK, qui liste les fichiers qui, au cas où ils ne soient pas accessibles en ligne, doivent renvoyer vers d’autres fichiers.

ex:

    CACHE MANIFEST
    # v0.1

    CACHE:
    index.html
    css/style.css
    img/logo.png

    FALLBACK:
    / /offline.html
 
    NETWORK:
    *

La configuration apache
-----------------------
Nous arrivons maintenant au passage (un peu) délicat. Il va falloir déclarer le MIME-type du fichier manifest. Ceci se fait par l’intermédiaire du fichier de configuration de serveur.
Créez donc un fichier .htaccess dans le répertoire de votre application et ajoutez-y simplement la ligne :

    AddType text/cache-manifest manifest

Dans cette ligne, on déclare que tous les fichiers se terminant par “manifest” ont pour MIME-type “text/cache-manifest”.

Tester sa webapp hors ligne
---------------------------
Afin de pouvoir tester localement notre application, nous allons devoir passer par Apache (et oui, faites chauffer vos WAMP / MAMP / LAMP !).
Plaçons notre application dans le dossier de votre serveur (www pour WAMP) et rendez-vous sur l’adresse http://localhost/
Si tout se passe bien, votre page s’affiche.
Maintenant stoppez les services de WAMP, puis rafraîchissez la page.
Alors qu’une page classique aurait naturellement fait afficher une belle erreur 404… Votre page est toujours là !
Ouvrez maintenant la console de votre navigateur si celui-ci en possède une (pour Chrome, elle se trouve dans Outils, Outils de développement, onglet Console).
On peut y voir ceci :

    Creating Application Cache with manifest  http://localhost/le-chemin-vers-votre-manifest
    Application Cache Checking event
    Application Cache Downloading event
    Application Cache Progress event (0 of 3)
    ... (1 of 3)
    ... (2 of 3)
    ... (3 of 3)
    Application Cache Cached event

L'application n'est correctement mise en cache que si la ligne suivante apparais:

    Application Cache Cached event
