Dans l'ensemble, une belle organisation des fichiers, et une syntaxe clair et une indentation lisible.

Le build n'a pas pu se faire immédiatement car une variable d'environnement était manquante dans l'exemple .env. Il est important d'y lister toutes les variables nécessaires au fonctionnement de l'application.

index.js:16
resave doit prendre une valeur de "true" dans le cas ou la session n'implémente pas la fonction "touch", ce qui est le cas ici.

router.js:13
Express est un framework que l'on peut imaginer comme une suite de middleware. Il existe des middleware que l'on va appliquer sur le router, comme un middleware d'authentification qui va autoriser ou refuser l'accès à des routes. Hors ici il s'agit de gérer un objet en session, et cela doit se faire au niveau de l'application, et non du router.

Attention au nomage des fichiers, ici card-item.ejs ne respecte pas les conventions de nommage, ici cela devrait s'écrire en camelCase, donc cardItem.ejs

La vue deck.ejs pourrait se servir de cardList.ejs. Réutiliser un maximum les vues qui ont des points communs facilite la maintenance d'un site ou d'une application. Ici la vue du deck a la même fonction que la liste des cartes, à savoir : lister des cartes.

En production, il est important de ne pas laisser les consoles log, surtout sur une API. Il faut imaginer la charge que cela peut représenter pour un serveur utilisé par des milliers de personnes qui executent les fonctions contenant des consoles log.

C'est super d'avoir mis en oeuvre les efforts nécessaires pour faire la mission bonus. Et qui plus est, bien fait !

