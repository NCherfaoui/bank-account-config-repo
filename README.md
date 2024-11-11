# Configuration Repository for Bank Account Microservices

Ce dépôt contient les fichiers de configuration pour les microservices de l'application Bank Account. Il est utilisé par le Config Server pour centraliser et gérer la configuration de tous les microservices.

Le code source de l'application Bank Account Microservices se trouve [ici](https://github.com/NCherfaoui/bank-account-app).

## Structure du répertoire

```
config-repo/
│
├── application.properties      # Configuration commune à tous les services
├── customer-service.properties # Configuration spécifique au service client
├── account-service.properties  # Configuration spécifique au service de compte
├── gateway-service.properties  # Configuration spécifique au service de passerelle
└── discovery-service.properties # Configuration spécifique au service de découverte
```

## Utilisation

Ce dépôt est conçu pour être utilisé avec Spring Cloud Config Server. Le Config Server lit ces fichiers et les sert aux microservices correspondants.

Pour utiliser ce dépôt de configuration :

1. Assurez-vous que votre Config Server est configuré pour pointer vers ce dépôt.
2. Dans le `application.properties` (ou `application.yml`) de votre Config Server, ajoutez :

   ```properties
   spring.cloud.config.server.git.uri=https://github.com/NCherfaoui/bank-account-config-repo.git
   spring.cloud.config.server.git.default-label=main
   ```

3. Dans chaque microservice, configurez-le pour utiliser le Config Server en ajoutant les dépendances nécessaires et en configurant l'URL du Config Server.

## Fichiers de configuration

- `application.properties`: Contient la configuration commune à tous les services.
- `customer-service.properties`: Configuration spécifique au service client.
- `account-service.properties`: Configuration spécifique au service de compte.
- `gateway-service.properties`: Configuration spécifique au service de passerelle.
- `discovery-service.properties`: Configuration spécifique au service de découverte (Eureka).

## Mise à jour de la configuration

Pour mettre à jour la configuration :

1. Modifiez les fichiers de propriétés appropriés dans ce dépôt.
2. Committez et poussez les changements.
3. Les services qui utilisent Spring Cloud Config se mettront automatiquement à jour (si configurés pour le faire) ou peuvent être actualisés manuellement en appelant leur endpoint de rafraîchissement.

## Sécurité

Assurez-vous de ne pas stocker d'informations sensibles (comme des mots de passe ou des clés API) directement dans ces fichiers. Utilisez des variables d'environnement ou des coffres-forts de secrets pour les informations sensibles.

## Contribution

Les contributions à ce dépôt de configuration sont les bienvenues. Veuillez suivre le processus standard de fork et de pull request pour proposer des modifications.

## Licence

Ce projet est sous licence MIT. Voir le fichier `LICENSE` pour plus de détails.
