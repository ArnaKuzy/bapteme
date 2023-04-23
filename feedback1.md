# Feedback 1

## Parcours S06

Globalement, le parcours est très bon, vous avez fait quelques bonus en plus.

## Quelques corrections

- Une partie des ACL sont incorrects, il est possible de créer, modifier ou supprimer un étudiant avec le rôle `user`, alors que seul les admins  en ont les droits.
- Certain urls des routes ne sont pas corrects, revoyez la doc !
- Attention aux injections SQL, il faut a tout prix éviter d'utiliser directement des variables dans la fonction `query` de PDO, il faut utiliser des [requêtes préparées (doc PHP)](https://www.php.net/manual/fr/pdo.prepare.php)
- Dans les formulaires de modification des teachers et student, le select utilisera toujours la valeur 1 par défaut, même si j'avais mis 2 à la création, il faut définir la valeur par défaut du select en fonction de la valeur en base de données. Sinon je risque de redéfinir la valeur à 1 à chaque modification.
- De plus les urls des formulaires ne sont pas bon, si j'essaye de modifier un teacher/student, je suis redirigé vers une page 404 !
- Le site essaye de charger un fichier "style.css" qui n'existe pas, vérifier que vous ne chargez pas des ressources inutilement.
- Il ne faut pas commit le fichier "config.ini" et ne surtout pas le push, si des mots de passe sont présents dans ce fichier, car cela peut créer une fuite de données.
Vous pouvez créer un fichier config.ini.dist qui sert de modèle avec de fausses données.

## Quelques améliorations

- Pour plus de clarté, il est préférable de mettre les routes dans un fichier dédié, par exemple dans `app/routes.php`, idem pour les ACL, ainsi quand j'ai besoin de modifier une route ou un ACL, il est plus simple de s'y retrouver.
- Vous pouvez aussi trier vos routes par "pages" ou "model".
- Vous pouvez masquer l'affichage des boutons en fonction du rôle, par exemple un user ne peux pas ajouter, ni consulter les profs et utilisateurs, les afficher n'est donc pas nescéssaire.
- Avant de commit, vérifier que vous n'avez pas de code inutilisé, ou que vous avez bien commenté votre code.