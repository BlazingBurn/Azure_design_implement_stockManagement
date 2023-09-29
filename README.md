
# Stock Management

Le but de ce projet est d’identifier un problème ou un scénario du monde réel. Cela peut se faire par le principe de résoudre ou améliorer la solution à l'aide de la technologie azure.

Afin de réaliser ce projet nous allons passer par plusieurs étape :

    1. Identifier un scénario ou un problème du monde réel
    2. Concevoir l'architecture de la solution 
    3. Mise en œuvre de la solution
    4. Documenter et évaluer (ce document et d’autres qui seront fournis)
    5. Tester la résilience de la solution

Cette documentation décrit le principe d’un projet d’entreprise et comment une petite partie simple du projet a été mise en place.




## Analyse du sujet

Le sujet choisi est le suivant : “la gestion de l'inventaire”. Un des problèmes pourrait être le suivant : "Une entreprise X gère un grand inventaire de produits, y compris des articles de vente au détail, des matières premières et des équipements. Cependant, elle éprouve des difficultés dans la gestion efficace de son inventaire, ce qui entraîne des problèmes tels que des ruptures de stock, des coûts de stockage élevés et une mauvaise visibilité sur les niveaux d'inventaire actuels. L'entreprise souhaite mettre en place un système de gestion de l'inventaire qui résolve ces problèmes."


**Pour répondre à ce problème nous pouvons utiliser différentes technologies azure tels que :**

- Azure SQL Database : Pour stocker des informations détaillées sur chaque article de l'inventaire, telles que les descriptions, les niveaux de stock, les fournisseurs, les coûts, etc.

- Azure Functions : Utilisées pour créer des processus automatisés, tels que la mise à jour des niveaux de stock en temps réel, l'envoi d'alertes en cas de rupture de stock, etc.

- Azure Logic Apps :  Pour automatiser des flux de travail de gestion de l'inventaire, tels que la gestion des commandes, la réception de marchandises, etc.

- Azure IoT Hub : Si l’inventaire comprend des équipements ou des produits IoT il serait possible d’y collecter des données en temps réel sur leur état.

- Azure DevOps : Pour la gestion de projet, le suivi des tâches et le déploiement continu de la solution.

- Azure Monitor : Surveiller les performances du système de gestion de l'inventaire pour détecter les problèmes et optimiser les performances.

- Azure Active Directory : Côté sécurité, Azure AD peut être utilisé pour gérer l'authentification et l'autorisation des utilisateurs qui accèdent au système de gestion de l'inventaire.

- Azure Cosmos DB : Si besoin de stocker des données non structurées ou semi-structurées.

- Azure Power BI : Afin d’y créer des tableaux de bord et des rapports visuels pour avoir une visibilité en temps réel sur l'état de l'inventaire.

- Azure Kubernetes Service (AKS) : Si le besoin de gérer des charges de travail conteneurisées pour des applications spécifiques liées à l'inventaire se fait ressentir.


*Avec cette liste d’exemples des fonctionnalités principales qui pourraient être implémentées dans le projet nous allons en prendre quelques-unes notamment : Azure SQL DB, Azure Functions et Azure App Services.*

## Contraintes/exigences

Nous pouvons également relever quelques contraintes et exigences sur ce projet.

**Contraintes :**

- Budget : L'une des contraintes les plus importantes est le budget disponible pour la mise en œuvre de la solution.

- Temps : Il peut y avoir des contraintes de temps, notamment des délais pour la mise en œuvre complète du système de gestion de l'inventaire.

- Systèmes existants : La migration de données s' ils existent déjà.

- Capacité de stockage et de traitement : Il peut y avoir des contraintes liées à la capacité de stockage et de traitement des données.

**Exigences :**

- Suivi en temps réel : Une des exigences clés pourrait être la capacité de suivre en temps réel les niveaux de stock, les mouvements d'inventaire et les modifications apportées aux données de l'inventaire.

- Automatisation : L'automatisation des tâches liées à la gestion de l'inventaire, telles que la réapprovisionnement, la gestion des commandes et la gestion des alertes de rupture de stock, peut être important.

- Sécurité : La sécurité des données de l'inventaire est cruciale.

- Scalabilité : La solution doit être évolutive pour répondre à la croissance future de l'entreprise. Elle doit pouvoir gérer des niveaux d'inventaire plus importants si l'entreprise se développe.

- Rapports et analyse : Les capacités de création de rapports et d'analyse sont souvent nécessaires pour évaluer les performances de l'inventaire, suivre les tendances et prendre des décisions éclairées.

## Architecture

Voici la V1 qui va être implémenté pour ce test :

![Diag1-ArchiBase drawio](https://github.com/BlazingBurn/Azure_design_implement_stockManagement/assets/49305403/2b0d65f2-2d7a-4b62-9600-a8499e548c97)

La V2 de l'architecture :

![Diag2-ArchiBase drawio](https://github.com/BlazingBurn/Azure_design_implement_stockManagement/assets/49305403/2a9dfac9-178c-4a00-81b7-5b0693ce83ef)

**Pour la V3 nous pouvons ajouter la partie Capteur IoT, K8s, etc…**

## Implémentation de la solution

### 1 - Mettre l’app dans azure container et App Services

Dockerfile utilisé :

```html

```

commande utilisé :

docker build -t stockmanagement .
docker images
docker tag stockmanagement testdockerhelloworldh3.azurecr.io/stockmanagement:latest
docker login testdockerhelloworldh3.azurecr.io
docker push testdockerhelloworldh3.azurecr.io/stockmanagement


Image du déploiement sur Azure container :

![azurecontainer](https://github.com/BlazingBurn/Azure_design_implement_stockManagement/assets/49305403/50f525da-c7f5-4d98-b0cf-24c40d52f0ec)

Mise en place dans App Services :

![appservice](https://github.com/BlazingBurn/Azure_design_implement_stockManagement/assets/49305403/261b4043-48f8-479a-9946-3a411c33a401)

**Faire la configuration du port**

![appserviceport](https://github.com/BlazingBurn/Azure_design_implement_stockManagement/assets/49305403/f2725bb0-c8c1-4efd-a3f7-b7040898f16c)

Déploiement de la web app :
![logdeploy](https://github.com/BlazingBurn/Azure_design_implement_stockManagement/assets/49305403/a4f242ff-21c8-48c3-8017-43c8e83a6142)
![sitedeploy](https://github.com/BlazingBurn/Azure_design_implement_stockManagement/assets/49305403/76acb657-21a2-412b-bca0-8aa6581e5a60)

### 2 - Utilisation d' Azure SQL DB

Création de la base de données SQL :

![createSQL](https://github.com/BlazingBurn/Azure_design_implement_stockManagement/assets/49305403/827c35dd-2442-45ab-bce1-6850583aeb0b)

Verification de son fonctionnement :

![SQLcheckIsWorking](https://github.com/BlazingBurn/Azure_design_implement_stockManagement/assets/49305403/02390a0f-20b8-4358-9186-f85e87c0ec8b)

**Parametrage du pare-feu pour les adresses IP**

![ParamSQLFireWall](https://github.com/BlazingBurn/Azure_design_implement_stockManagement/assets/49305403/c55c8b0c-f955-49f1-9265-a0c8c1217cbf)

Creation des tables dans Azure Data Studio :

![CreateTableSql](https://github.com/BlazingBurn/Azure_design_implement_stockManagement/assets/49305403/f875f090-eb3e-4546-b6ba-9b42c5da3a38)


## Authors

- [@BlazingBurn](https://www.github.com/BlazingBurn)
