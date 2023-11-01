
Il est important de mettre les informations secretes dans un fichier qui n'est pas publique. Ici le secret servant au hash de la session est directement mis dans le code, et sera donc visible. Il serait plus prudent de le mettre dans le .env qui ne sera pas envoyé sur le git.

deckController.js:10 peut être ajouté globallement sur express via un app.use, dans le deckController cela permet d'initialiser la session au démarrage, et pas uniquement quand une carte veux être ajoutée au deck.
C'est pour cela qu'ici la page de deck ne s'affiche pas, tu cherches dans ta session un deck qui n'existe pas dans deckController.js:29

La route pour voir le détail d'une carte n'est pas finalisé. Elle n'as pas de parametre dans l'URL permettant de savoir quelle carte on souhaite afficher, elle n'est pas appelée quand on click sur une carte dans la liste des cartes, dans le mainController.js:20 la méthode n'intègre pas les données de la carte, dans le mainController.js:18 il manque le parametre dans la fonction getCard(?) pour savoir quelle carte on souhaite get, la query dans dataMapper.js:13 n'intègre pas de valeurs dans la méthode, hors une référence $1 est ajoutée, qui fait référence au premier objet de l'array de values qui est passé à la méthode query de la database.
datamapper.js:18 La query pour la carte est assigné à la constante queryResult, hors apres, est vérifié la constante resultQuery qui n'existe pas. Attention aux fautes d'innatention

La vue d'une carte ne render pas, cela est lié au fait que tu as laissé la boucle de la page cardList qui était là dans le but de lister toutes les cartes de la liste. Hors là nous n'avons qu'une carte, la boucle n'est donc pas nécessaire, et pire, elle bloque la page. De plus, tu passes à la page un objet avec une clé 'oneCard' mais tu utilises 'card' dans la page. Il faut utiliser la clé de l'objet que tu passes du controller à la view.

La Session, le résultat de recherche sur élément, le deck et les fonctions liées au deck n'ont pas été développés, as-tu manqué de temps, de moyens ?
Étant donné la quantité d'information, je suis disponible pour qu'on fasse une revue ensemble de ton code pour aborder chaque point et qu'on puisse trouver comment avancer.
