l'api fetch permet de gérer la view et la data de manière asynchrone, et ainsi détacher la view et l'API pour rendre l'affichage plus dynamique, et charger dynamiquement les données.
Cela permet aussi de réduire la charge des informations délivrée par l'API en retournant des JSON.

Une route accessible en fetch pour lister les cartes ressemblerait à cela : router.get('/api/cards', cardController.cards);
Le cardController.js côté api pourrait alors s'occuper de query les data et simplement retourner et JSON, et plus la vue.
cards: async (req, res) => {
    try {
      const cards = await dataMapper.getAllCards();
      res.json(cards);
    } catch (error) {
      console.error(error);
      res.status(500).send(`An error occured with the database :\n${error.message}`);
    }
  },

Dans un front connecté à une API, il serait alors possible de servire la page directement via le routeur, et alors de gérer les données en asynchrone et raffaichir uniquement les données de la page.
la fetch api permet donc beaucoup plus de flexibilité, scalabilité et sécurité dans les projets qu'une vue qui intérroge directement la base de donné en query tel que cela à été fait dans ce projet.