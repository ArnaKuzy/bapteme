# Dessine moi un fetch

Bonjour,

## Explication

`fetch` est une fonction Javascript, qui permet d'effectuer des requêtes HTTP asynchrones vers un serveur, afin de récupérer ou envoyer des données, ou réaliser des actions.

Par exemple sur un navigateur, lorsque que l'on entre un url par exemple : `https://placekitten.com/200/300`, le navigateur va effectuer une requête vers le serveur placekitten.com qui permet de générer des images de chat, et renvoie au navigateur une image, qu'il va afficher.

Résultat :
![image](https://placekitten.com/200/300)

On peut aussi récupérer du texte, des données au format JSON, des fichiers de tout type, des pages HTML, etc...

Grâce à la fonction JavaScript fetch on va pouvoir exécuter une requête depuis un serveur javascript, ou depuis une page web après l'affichage de la page.
Le mot "asynchrone" ici veut dire, que pendant la requête le reste du code continuera de s'exécuter en parallèle.

## Exemple

Imaginons pour la page "Liste des profs", nous voulons raffraîchir la liste des profs sans pour autant recharger l'intégralité du HTML.

Grâce à la fonction fetch nous allons pouvoir récupérer uniquement les données de la liste des professeurs puis mettre à jour uniquement la portion de HTML qui affiche la liste.

Pour ce faire voici un exemple d'intégration dans une page

- On va envoyer le formulaire de création d'un student grâce à la fonction fetch

```html
<html>
<body>

<form id="mon-formulaire">
    <input name="firstname">
    <input name="lastname">
    ...

    <button onsubmit="sendForm(event)">Créer le prof</button>
</form>

<script>

function sendForm(event)
{
    // Pour empêcher la page de se recharger
    event.preventDefault();
    
    // Récupération des données du formulaire    
    const formData = new FormData(document.getElementById('mon-formulaire'));

    // Paramètres du fetch
    const params = {
        method: 'POST',
        body: formData,
    };

    // Envoie du formulaire
    fetch('https://monserveur.com/students/add', params)
        .then(function(response) {
            // Si la réponse est valide on peux rediriger vers la liste ou afficher un message
            window.location.href = "https://monserveur.com/students"
        })
        .catch(function(error) {
            En cas d'erreur on affiche un message d'erreur
        })
    }
</script>

</body>
</html>
```

On définie notre formulaire HTML et lors de l'envoie, on va appeler la fonction `sendForm` avec notre fetch dedans.
On récupère ensuite les données de notre formulaire dans un `FormData` pour pouvoir l'envoyer avec notre requête HTTP

La fonction `fetch` prend comme premier paramètre l'url sur lequel on veut faire une requête, par défaut la méthode utilisér est `GET`, mais nous allons utiliser du `POST`  en définissant des paramètres supplémentaires.
En 2e paramètre elle prend un objet avec des paramètres, ici nous allons définir la méthode sur `POST`, et placer le formulaire dans le `body` de la requête.

Une fois la requête envoyée, la fonction fetch va attendre la réponse du serveur
Le serveur va recevoir les données de la même manière que si nous avions fait un formulaire HTML classique il n'y a donc rien à changer sauf pour la réponse.

```php
function studentAddPost()
{
    // Récupération du des données
    // Création du model Student
    // Sauvegarde en base de données

    // Réponse en cas d'erreur
    return json_encode($errorList);

    // Réponse en cas de succès
    return "OK";
}
```

Ici au lieu d'afficher la page avec les erreurs ou de rediriger, nous allons envoyer soit `OK` si tout c'est bien passé, soit la liste des erreurs pour l'afficher.

Une fois la réponse reçue, la fonction `.then` va s'exécuter si tout c'est bien passer
Les données renvoyées par le serveur sont mise à disposition via la variable `response`, qui peux contenir n'importe quel format de données. (texte, json, image)

En cas d'erreur ou d'échec de la requête c'est le `.catch` qui sera executé.
La variable error contiendra un objet avec le détail de l'erreur, que l'on peux afficher avec un `console.error(error)` ou l'on peux exécuter une autre action comme par exemple afficher un message d'erreur sur la page web.
