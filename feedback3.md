Le projet build, c'est une bonne première étape.

Il est important de mettre les informations secretes dans un fichier qui n'est pas publique. Ici le secret servant au hash de la session est directement mis dans le code, et sera donc visible. Il serait plus prudent de le mettre dans le .env qui ne sera pas envoyé sur le git.

L'import des controllers dans express n'a pas d'utilité. Les controlleurs sont utilisé pour gérer les fonctions appelées au routing pour faire le lien entre les datas et la view.
Il faut effectivement les affecter à une constante pour les utiliser sur le fichier du routing, comme tu as pu le faire. Cependant il faut également le faire lors de l'utilisation des fonctions de dataMapper.js, ce qui a été oublié dans le searchController.js et le nom de la fonction cardElement n'est pas le bon searchController.js:12. 
Je pense cependant que cela relève d'un oublie étant donné que cela à été fait partout ailleurs. Attention donc aux erreures d'innatentions. Et test tes fonctions avant de les livrer, cela permet de l'identifier très rapidement.
 
La vue d'une carte ne render pas, cela est lié au fait que tu as laissé la boucle de la page cardList qui était là dans le but de lister toutes les cartes de la liste. Hors là nous n'avons qu'une carte, la boucle n'est donc pas nécessaire, et pire, elle bloque la page. De plus, tu passes à la page un objet avec une clé 'oneCard' mais tu utilises 'card' dans la page. Il faut utiliser la clé de l'objet que tu passes du controller à la view.

Tu as créé une view 'element', qui a pour objectif d'afficher une liste de carte correspondant au résultat de la recherche sur l'élément. Hors réutiliser un maximum les vues qui ont des points communs facilite la maintenance d'un site ou d'une application. Ici la vue du résultat de recherche a la même fonction que la liste des cartes, à savoir : lister des cartes.

La Session, le deck et les fonctions liées au deck n'ont pas été développés, as-tu manqué de temps, de moyens ?
Étant donné la quantité d'information, je suis disponible pour qu'on fasse une revue ensemble de ton code pour aborder chaque point et qu'on puisse trouver comment avancer.