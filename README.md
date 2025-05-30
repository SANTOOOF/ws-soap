## Projet ws-soap

Ce projet met en œuvre un service web SOAP simple en Java, accompagné d'un client Java pour interagir avec ce service. Il illustre les concepts de base de la création et de la consommation de services web SOAP à l'aide de JAX-WS et Maven.

### Description

Le projet est divisé en deux modules principaux :

1.  **ws-soap** : Ce module contient le code source du service web SOAP. Il définit un service `BanqueService` qui expose des opérations liées à la gestion de comptes bancaires (`Compte`) et potentiellement d'autres fonctionnalités comme la conversion de devises (`ConversionEuroToDH`). Le point d'entrée pour démarrer le serveur de service est la classe `ServerJWS.java`.

2.  **client-soap-java** : Ce module contient le code source d'un client Java qui consomme le `BanqueService`. Il utilise les classes proxy générées à partir du fichier WSDL (`BanqueWS.wsdl`) pour communiquer avec le service web. La classe `Main.java` sert de point d'entrée pour exécuter le client et interagir avec le service.

### Structure du Projet

Le projet suit une structure Maven standard :

```
ws-soap/
├── client-soap-java/      # Module client Java
│   ├── pom.xml
│   └── src/
│       └── main/
│           └── java/
│               ├── net/youssef/Main.java  # Point d'entrée du client
│               └── proxy/                 # Classes proxy générées (WSDL)
├── pom.xml                # Fichier POM principal (peut-être parent)
├── src/                   # Code source du service web
│   └── main/
│       └── java/
│           ├── ServerJWS.java       # Point d'entrée du serveur
│           └── ws/
│               ├── BanqueService.java # Implémentation du service
│               └── Compte.java        # Modèle de données
├── target/                # Fichiers compilés du service
└── ws-soap.iml            # Fichier de configuration IDE (IntelliJ)
```

### Technologies Utilisées

*   Java
*   SOAP (JAX-WS)
*   Maven (pour la gestion des dépendances et la construction)

### Prérequis

*   JDK (Java Development Kit) installé
*   Maven installé

### Compilation

Pour compiler les deux modules, naviguez jusqu'au répertoire racine (`ws-soap/`) où se trouve le `pom.xml` principal (s'il existe, sinon compilez chaque module séparément) et exécutez la commande Maven :

```bash
mvn clean install
```

Si les modules sont indépendants, naviguez dans chaque répertoire (`ws-soap/` et `ws-soap/client-soap-java/`) et exécutez la même commande.

### Exécution

1.  **Démarrer le Service Web** : Exécutez la classe `ServerJWS.java` située dans le module `ws-soap`. Cela démarrera un serveur embarqué (probablement via `Endpoint.publish`) qui hébergera le `BanqueService`.

2.  **Exécuter le Client** : Une fois le service démarré, exécutez la classe `Main.java` située dans le module `client-soap-java`. Le client interagira avec le service web déployé.

### Fichier WSDL

Le fichier `BanqueWS.wsdl` (situé dans `client-soap-java/src/main/java/proxy/`) décrit le contrat du service web `BanqueService`. Il peut être utilisé par d'autres clients ou outils pour comprendre comment interagir avec le service.

