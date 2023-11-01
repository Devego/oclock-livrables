Dans l'ensemble, une belle organisation des fichiers, et une syntaxe clair et une indentation lisible. Les conventions de nommage sont respectées, camelCase et nommage des fichiers. 

Attention aux noms de fonctions, il faut que cela permette de rapidement savoir le but de la fonction, hors la fonction addDeck n'explique pas clairement ce qu'elle fait. Hors elle permet d'ajouter une carte au deck et non d'ajouter un deck.

Il est important de mettre les informations secretes dans un fichier qui n'est pas publique. Ici le secret servant au hash de la session est directement mis dans le code, et sera donc visible. Il serait plus prudent de le mettre dans le .env qui ne sera pas envoyé sur le git.

Une demande était faite concernant la suppression d'une carte du deck, hors elle n'a pas été dévelopée. Pour indice, il faut créer une fonction de filter sur les deck de la session, qui retire l'élément de la liste, et qui remet la nouvelle liste dans la session, puis rediriger vers le /deck pour re-render la page.

index.js:16
resave doit prendre une valeur de "true" dans le cas ou la session n'implémente pas la fonction "touch", ce qui est le cas ici. Voir doc de express-session

Réutiliser un maximum les vues qui ont des points communs facilite la maintenance d'un site ou d'une application. Ici la vue du résultat de recherche a la même fonction que la liste des cartes, à savoir : lister des cartes. Hors là, le résultat de la recherche montre une liste de nom de carte, mais sans le visuel et les informations supplémentaires.

dataMapper.js:10 - la recherche prend en compte le fait que l'élément ne doit pas être null, ce qui est bien, hors la cherche peut être executée sans élément, et dans ce cas elle ne retourne pas de résultat. Il faut imaginer une recherche si l'élément est nul et une autre si un élément est renseigné, ainsi tous les cas de figure sont couverts.

deckController.js:17 - Il est possible d'ajouter un nombre illimité de cartes au deck, hors la consigne était de le limiter à 5 cartes. Il faudrait ajouter une vérification avant d'ajouter la carte au deck.

Dans la vue du deck, il y a un affichage de prix qui a été ajouté. Hors les cartes n'ont pas de valeur, ce qui n'affiche donc aucun prix. Il faudrait soit ajouter des prix aux cartes, meme si ce n'était pas demandé, c'est une bonne initiative, soit retirer le prix des cartes sur la page de deck.

En production, il est important de ne pas laisser les consoles log, surtout sur une API. Il faut imaginer la charge que cela peut représenter pour un serveur utilisé par des milliers de personnes qui executent les fonctions contenant des consoles log.