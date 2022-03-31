GraphQL

Le GraphQL est un langage de query permettant de récupérer facilement des information sur un serveur de base de donnée

**playground :**

<http://163.172.93.149:3010/graphql/>

le lien ci-dessus mène au playground GraphQL du serveur

C’est un espace dans lequel nous pouvons tester l’envoie de query ou mutation au serveur

![](../resources/TUTO_Liaison_Serveur_GraphQL/Aspose.Words.e909697a-fd51-49f4-b76b-3756a2e2d285.001.png)

ci-dessus est un exemple de query (la query currentPosts), elle récupère tous les posts enregistré sur le serveur

Cette query est composé de 3 fenêtre, une fenêtre input (haut à gauche), une fenêtre output (à droite) et une fenêtre headers (bas à gauche)

**Query:**

Une méthode ayant pour but de récupérer une information précise en fonction d’un argument

**Mutation:**

Une méthode ayant une action sur le serveur, notamment, login ou createPost


![](../resources/TUTO_Liaison_Serveur_GraphQL/Aspose.Words.e909697a-fd51-49f4-b76b-3756a2e2d285.002.png)![](Aspose.Words.e909697a-fd51-49f4-b76b-3756a2e2d285.003.png)

Toutes les méthodes sont répertorié dans l’onglet schéma à droite de l’écran![](Aspose.Words.e909697a-fd51-49f4-b76b-3756a2e2d285.004.png)

**X-Access-Token / Header:**

La plupart des Query et Mutation, on besoin d’un x-access-token 

Il faut donc le récupérer cette access token (aussi appelé JWT) avec une mutation de Login ou de Register

![](../resources/TUTO_Liaison_Serveur_GraphQL/Aspose.Words.e909697a-fd51-49f4-b76b-3756a2e2d285.005.png)

Dans le playground l’x-access-token resemble à 

{“x-access-token” = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiI1ZDZkMTYzNzRhOGJjNDQ3YThhY2ZjYTUiLCJpc3MiOiJHYW1lIENvcmUiLCJ1c2VybmFtZSI6IjEiLCJvcmdzIjpbXSwiZW50X29yZ3MiOltdLCJlbnRzIjpbXSwic2NvcGUiOlsiZ3Vlc3QiXSwiaWF0IjoxNTY4NzEwNjAxLCJleHAiOjE1Njg3OTcwMDF9.ou2bRAWhPTTJleDvri8jb1HeV2eV\_yfL\_nb1-qd-VW8"}

Au bout d’un moment ce token devient invalide mais à chaque connection, un nouvelle x-access-token est généré

Si la méthode demande un token, et que ce token et manquant, incomplet, ou vide, la plupart des query/mutation ne fonctionnent pas et renverra un message vide

![](../resources/TUTO_Liaison_Serveur_GraphQL/Aspose.Words.e909697a-fd51-49f4-b76b-3756a2e2d285.006.png)

**Dans Unity:**

Dans Unity nous utilison l’Api GraphQL Cette Api nous permet d’envoyer plus simplement des requêtes GraphQL vers le serveur

- GraphQuery.cs

(Example de Query, currentPosts)

SocialFeedScreen.cs

![](../resources/TUTO_Liaison_Serveur_GraphQL/Aspose.Words.e909697a-fd51-49f4-b76b-3756a2e2d285.007.png)

![](../resources/TUTO_Liaison_Serveur_GraphQL/Aspose.Words.e909697a-fd51-49f4-b76b-3756a2e2d285.008.png)

On commence par Clear() l'éventuelle Query précédente.

On Set l’Url avec <http://163.172.93.149:3010/graphql/>

On Set le Header/x-access-token avec le token récupéré lors que login/register

On sélectionne la méthode à exécuter quand la query est achevé 

On finit par POST la query souhaité 

La méthode exécuté après est utilisé pour “Parse” le message renvoyé par le serveur

(Example de Mutation, createPost)

PostHandler.cs

![](../resources/TUTO_Liaison_Serveur_GraphQL/Aspose.Words.e909697a-fd51-49f4-b76b-3756a2e2d285.007.png)

![](../resources/TUTO_Liaison_Serveur_GraphQL/Aspose.Words.e909697a-fd51-49f4-b76b-3756a2e2d285.009.png)

À noter : les queries peuvent avoir des éléments variables, notamment ici “title” et “description” pour que ces variables soit prise en compte il faut dans la query, encadré le morceau de query par $ et ^ (“$title^” et “$description^”)

Dans ce cas la ligne, *GraphQuery.variable[“title”] = post.message;* ,va remplacer $title^ de la query par le message souhaité
