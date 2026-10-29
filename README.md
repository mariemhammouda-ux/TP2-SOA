# TP2 : Mise en œuvre de Jakarta XML Web Services

![Java](https://img.shields.io/badge/Java-8-orange)
![Maven](https://img.shields.io/badge/Maven-Project-blue)
![SOAP](https://img.shields.io/badge/Web_Service-SOAP-green)

## Informations générales

| Information | Détail |
|---|---|
| Établissement | Faculté des Sciences de Sfax |
| Département | Informatique et Communications |
| Filière | LSI3-GLSI |
| Matière | Architecture SOA et services web |
| Année universitaire | 2025-2026 |
| Projet | CalculatriceWS |

---

## 1. Présentation du projet

Ce projet consiste à développer un service web SOAP en Java permettant d'effectuer quatre opérations mathématiques : la somme, la multiplication, la soustraction et la division.

Le service est développé avec Maven et JAX-WS. Il est publié à l'aide de `Endpoint.publish()` et testé avec SoapUI.

## 2. Objectifs du TP

- Configurer un projet Maven pour développer un service web SOAP.
- Créer une interface Java définissant les opérations du service.
- Implémenter les opérations mathématiques.
- Utiliser les annotations JAX-WS.
- Publier le service web.
- Consulter le WSDL et le schéma XSD.
- Tester les opérations avec SoapUI.

## 3. Technologies utilisées

- **Java** : développement de l'application.
- **Maven** : gestion des dépendances.
- **JAX-WS** : création et publication du service web.
- **SOAP** : protocole de communication.
- **WSDL** : description du contrat du service.
- **XSD** : définition des structures des données XML.
- **SoapUI** : test des opérations SOAP.
- **IntelliJ IDEA** : environnement de développement.

## 4. Structure du projet

```text
CalculatriceWS/
├── pom.xml
├── README.md
└── src/
    └── main/
        └── java/
            ├── org/
            │   └── example/
            │       └── Main.java
            ├── service/
            │   ├── ICalculatrice.java
            │   └── Calculatrice.java
            └── serveur/
                └── ServeurJWS.java
```

## 5. Description des classes

### 5.1. ICalculatrice.java

Cette interface définit le contrat du service web et déclare les quatre opérations :

- `somme(a, b)`
- `multiplication(a, b)`
- `soustraction(a, b)`
- `division(a, b)`

Les annotations `@WebService`, `@WebMethod` et `@WebParam` permettent de décrire les opérations exposées par le service.

### 5.2. Calculatrice.java

Cette classe implémente l'interface `ICalculatrice`.

Elle contient les méthodes qui réalisent les calculs et traite le cas de la division par zéro.

### 5.3. ServeurJWS.java

Cette classe permet de publier le service web à l'aide de `Endpoint.publish()`.

### 5.4. Main.java

Cette classe contient la méthode `main()` permettant de démarrer l'application.

**Remarque :** une seule classe de lancement est nécessaire pour publier le service. Si `Main.java` et `ServeurJWS.java` publient tous les deux le même service, il faut en choisir une seule pour éviter les conflits de port.

## 6. Publication du service web

Le service est publié à l'adresse suivante :

```text
http://localhost:8080/CalculatriceWS
```

Le contrat WSDL est accessible à l'adresse :

```text
http://localhost:8080/CalculatriceWS?wsdl
```

Pour consulter le WSDL, le serveur doit être démarré et rester en cours d'exécution.

### Capture 1 : Démarrage du service
![Capture du démarrage du serveur](cp1.png)
## 7. Tests avec SoapUI

Les tests sont effectués avec SoapUI en important le WSDL du service.

### Étapes de test

1. Démarrer le serveur dans IntelliJ IDEA.
2. Créer un nouveau projet SOAP dans SoapUI.
3. Importer le WSDL du service.
4. Sélectionner l'opération à tester.
5. Envoyer la requête SOAP.
6. Vérifier le résultat retourné.

## 8. Résultats des tests

Les opérations sont testées avec les valeurs suivantes :

| N° | Opération | Paramètre A | Paramètre B | Résultat attendu |
|---|---|---:|---:|---:|
| 1 | Somme | 5 | 3 | 8 |
| 2 | Multiplication | 5 | 3 | 15 |
| 3 | Soustraction | 5 | 3 | 2 |
| 4 | Division | 6 | 3 | 2 |

### 8.1. Test de la somme

La méthode `somme()` additionne les deux valeurs transmises par le client.

**Requête :** `somme(5, 3)`

**Résultat attendu :** `8.0`

**Capture 3 : Test de la somme**

![Résultat du test de la somme](cp2.png)

### 8.2. Test de la multiplication

La méthode `multiplication()` calcule le produit des deux nombres.

**Requête :** `multiplication(5, 3)`

**Résultat attendu :** `15.0`

**Capture 4 : Test de la multiplication**

![Résultat du test de multiplication](cp3.png)

### 8.3. Test de la soustraction

La méthode `soustraction()` calcule la différence entre les deux nombres.

**Requête :** `soustraction(5, 3)`

**Résultat attendu :** `2.0`

**Capture 5 : Test de la soustraction**

![Résultat du test de soustraction](cp4.png)

### 8.4. Test de la division

La méthode `division()` calcule le quotient des deux nombres.

**Requête :** `division(6, 3)`

**Résultat attendu :** `2.0`

La division par zéro est traitée comme un cas d'erreur.

**Capture 6 : Test de la division**

![Résultat du test de division](cp5.png)

## 9. Bilan des tests

| Opération | Résultat attendu | Résultat obtenu | Statut |
|---|---:|---:|---|
| Somme | 8.0 | À compléter | À compléter |
| Multiplication | 15.0 | À compléter | À compléter |
| Soustraction | 2.0 | À compléter | À compléter |
| Division | 2.0 | À compléter | À compléter |

Ce tableau sera complété après l'exécution des tests dans SoapUI.

## 10. Conclusion

Ce TP a permis de mettre en pratique les étapes essentielles du développement d'un service web SOAP en Java : configuration Maven, définition du contrat, implémentation des opérations, publication du service et tests avec SoapUI.

Il a également permis de comprendre le rôle du WSDL dans la description du service et celui du XSD dans la définition des structures de données XML.

---

**Fin du compte rendu — TP2 CalculatriceWS**