# Remise à niveau HTTP
Dans cet exercice on va revoir les bases de HTTP via un petit jeu de piste sur une API.

Vous allez devoir accéder à plusieurs routes dans un certain ordre, parfois les appels API vous retournerons des informations utile pour passer à la route suivante, a vous de récupérer les informations en fonction des consignes.

**Le domaine de l'API est `herokuapp.com` le schéma d'url est `https` et le sous domaine est `m1-mds-web-simple-api-tester`.**

Vous pouvez dores et déjà voir des score d'exemple, en accédant à la racine de l'URL d'API. Cette page permet de savoir qui à réussi quels tests pour voir l'avancement de chacun.

* Pour réaliser cet exercice, vous pouvez utilisez des outils comme Insomnia ou Postman, mais vous pouvez également réaliser les appels avec du code et un autre langage de programmation au choix.

* Puis en faisant l'exercice vous validez automatiquement les tests sur le serveur qui sauvegarde votre avancement.

* Essayez de bien comprendre chaque mot et concept qui vous semble flou ou pas compris pour vous. Après cet exercice, j'estime que vous serez à niveau vis à vis du protocole HTTP et donc il pourra y avoir des questions sur cela lors de l'examen final.

## C'est parti 
Définissez vous un `Student-Name` que vous devrez passer dans les headers de chacune de vos request à l'API. 

* Exemple: `Student-Name: anthony` Prenez en 1 qui vous est propre et qui me permet de savoir qui vous êtes.

> Tous les chemins des requêtes doivent être préfixés par `/api`

Regardez bien les status des réponses de l'API, notamment `400, 403, 401, 200`, etc. et vérifiez sur internet a quoi correspondent-ils. Cela explique pourquoi l'API rejette votre requête si c'est le cas.

## Route 1
La première route est sur l'URL `/route-1`, vous devez utiliser la méthode `GET`.

Elle attend un `header` avec une clé `pokemon` et en valeur votre pokémon favori. En retour, cette route vous fournira un code secret 🔑 , utile pour la suite.

## Route 2
La route a pour URL `/route-2` , vous devez utiliser la méthode `GET`

Cette route attend un tableau de paramètres dans l'URL sous forme de `query parameters`.

Ce tableau se nomme `favoritesPokemon` et doit contenir au moins 2 valeurs.

La route fonctionnera uniquement si vous entrez un header avec la clé `Secret-Code` et en valeur le code secret obtenu à la Route 1.

> 🔑 La route vous enverra un nouveau code secret pour la Route 3

## Route 3
La route a pour URL `/route-3` vous devez utiliser la méthode `POST`
Cette route attend un body de request avec un objet `JSON` a l'intérieur (pensez à spécifier le `Content-Type` dans vos `headers` pour que le serveur comprenne que vous envoyez du `JSON` .

L'objet JSON doit avoir cette structure 
```json
{
	"color": "grey",
	"type" : "car",
	"brand" : "peugeot",
	"model" : "208"
}
```

Vous devez inclure le code secret 🔑  obtenu précédemment dans le `header` dans une clé `Secret-Code`.
## Route 4
URL de la route `/route-4` vous devrez utiliser la méthode `POST` et en body un formulaire de type `Multipart form data`.
N'oubliez pas le `Content-Type` !

Ce formulaire doit contenir une clé `image_description` avec une valeur et une clé `image` de type `file` avec une image à l'intérieur (de moins de 5Mo).

## Route 5

URL de la route `/route-5` vous devrez utiliser la méthode `POST` et en body un formulaire encodé sous la forme `UrlEncoded` Form.

Ce formulaire doit contenir au moins 3 clés avec leur valeur, au choix pour vous.

> N'oubliez pas le `Content-Type` !

## Route 6
URL de la route `/route-6` vous devrez utiliser la méthode `DELETE` sans body.

Cette route demandera un `query parameter` ayant pour clé `user_id` et une valeur `integer` aléatoire.

## Route 7 
URL de la route `/route-7`, vous devrez utiliser la méthode POST avec le même body que pour la route 4.

Vous devez ajouter 2 paramètres de chemin ou path parameter pour que la requête fonctionne, peu importe leur valeur.

## Route 8
URL de la route `/route-8` vous devrez utiliser la méthode PATCH avec un body JSON libre, mais avec au moins un champ JSON.

## Route 9
La route 9 est protégée par un système d'authentification d'API. 
L'URL de la route 9 est `/route-9` si vous tentez d'y acceder vous aller récupérer un code d'erreur spécifique 401.

Pour y accéder il va falloir vous enregistrer puis vous connecter à l'API. 

## Route d'enregistrement 
`/register` en utilisant la méthode `POST` , vous allez devoir créer un compte sur l'API. Cette route attend un formulaire ( `multiPart` ou `urlEncoded`) qui contient 3 champs : 

* `name` (utilisez le `Student-Name` que vous utilisez depuis le début pour lier votre score à votre compte)
* `password` vous pouvez mettre ce que vous voulez
* `email` imaginer un faux mail, il doit être bien formaté, et unique dans la BDD.
## Route de connexion
Puisque c'est une API Rest, vous allez vous authentifier via un `token` qui est généré par l'API. Chaque API / Framework ou développeur peut utiliser un système de génération de token différent. Mais l'utilisation général est de :

1. Demander un token
2. Le conserver quelque part
3. L'injecter dans les futures requete qui demandent une authentification.

Utilisez donc la route `/login` avec la méthode `POST` et passez `email` et `password` dans le body sous le format d'un formulaire ( `multiPart` ou `urlEncoded`).
Cette route doit vous renvoyer un token, qui a une validité de 10 minutes.
## Retour sur la Route 9
Ce token doit être injecté en tant que `Bearer` token dans votre requête. 
Vous devriez pouvoir accéder à la Route 9 (en GET) et obtenir quelques liens interessants dans la réponse.

# Fin
Voilà vous devriez avoir terminer l'exercice ;) 
