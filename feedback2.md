# Feedback 2

## Parcours S06

Le projet est vide, il manque beaucoup de fonctionnalités, l'affichage des données est maitrisé, mais quand est-il des création/modification/suppression ?

## Quelques corrections

- Le bouton de modification d'un prof redirige vers la page pour "ajouter" un prof
- Attention aux injections SQL, il faut a tout prix éviter d'utiliser directement des variables dans la fonction `query` de PDO, il faut utiliser des [requêtes préparées (doc PHP)](https://www.php.net/manual/fr/pdo.prepare.php)
- Il manque les vues en cas d'erreur.
- Attention, l'affichage des listes déborde de l'écran lorsque l'on clique sur le bouton pour supprimer.
- Il ne faut pas commit le fichier "config.ini" et ne surtout pas le push, si des mots de passe sont présents dans ce fichier, car cela peut créer une fuite de données.
Vous pouvez créer un fichier config.ini.dist qui sert de modèle avec de fausses données.

## Quelques améliorations

- Attention à l'indentation du code, un code bien indenté permet de mieux visualiser la porter des fonctions/conditions/boucles, ainsi qu'une meilleure lecture
- N'hésitez pas à commenter votre code, que fait une fonction, une condition etc
- Pour plus de clarté, il est préférable de mettre les routes dans un fichier dédié, par exemple dans `app/routes.php`