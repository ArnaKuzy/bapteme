# Feedback 3

## Parcours S06

## Quelques corrections

- Une partie des routes ne sont pas bonnes, vous devez respecter les URLs indiquées dans le sujet.
- La racine d'un site `/` doit impérativement être géré, car quand on va sur un site, c'est l'url par défaut. Hors ici, je dois aller sur `/home` pour voir la page d'accueil.
- Certains urls redirigent vers des pages en .html au lieu des routes du sujet.
- Il manque la barre de navigation (menu) sur les pages `Etudiants` et d'une page à l'autre les boutons n'ont pas le même comportement, il impératif d'avoir le même menu sur toutes les pages, sinon cela rend la navigation difficile.
- Attention aux injections SQL, il faut a tout prix éviter d'utiliser directement des variables dans la fonction `query` de PDO, il faut utiliser des [requêtes préparées (doc PHP)](https://www.php.net/manual/fr/pdo.prepare.php)
- Il ne faut pas commit le fichier "config.ini" et ne surtout pas le push, si des mots de passe sont présents dans ce fichier, car cela peut créer une fuite de données.
Vous pouvez créer un fichier config.ini.dist qui sert de modèle avec de fausses données.


## Quelques améliorations

- Pour avoir le même menu sur toutes les pages, il faut créer une vue dédiée pour le menu dans un fichier `views/menu.tpl.php` par exemple et inclure ce menu dans toutes les pages, ainsi lorsque l'ont à besoin de modifier le menu, on le modifie qu'une fois pour tous le site
- Attention à l'indentation du code, un code bien indenté permet de mieux visualiser la porter des fonctions/conditions/boucles, ainsi qu'une meilleure lecture
- N'hésitez pas à commenter votre code, que fait une fonction, une condition etc.
- Pour plus de clarté, il est préférable de mettre les routes dans un fichier dédié, par exemple dans `app/routes.php`
- Pour éviter de dupliquer le code source du site, une bonne pratique est de segmenter l'affichage en plusieurs parties.

Exemple
On va créer un fichier avec le début du html et un avec la fin et insérer notre page au milieu.

`fonction show()`

```php
function show()
{
    // extract etc

    require_once __DIR__ . '/../views/layout/header.tpl.php';
    require_once __DIR__ . '/../views/' . $viewName . '.tpl.php';
    require_once __DIR__ . '/../views/layout/footer.tpl.php';
}
```

`views/layout/header.tpl.php`

```html
<html>
<head>
    <!-- Le header -->
</head>

<body>
    <header>
        <!-- Ici on inclu le menu -->
    </header>

    <main>
```

`views/layout/footer.tpl.php`

```html
    </main>
</body>

</html>

```


