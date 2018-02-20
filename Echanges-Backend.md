## TOC
- [Notes](#notes) **(A traiter / discuter)**
- [URL de base et version](#url-de-base-et-version)
- [Formats](#formats)
- [Authentification](#authentification)
- [Ressources](#ressources)
- [Endpoints](#endpoints)

## Notes
### Remarques sur les graphiques, les onglets manquants
Cf. document de remarques.
### Language du code
Le code Frontend sera en anglais. Doit-on prévoir les call en anglais ? peu importe ?
### Gestion des périodes en cours
2 options sont possibles pour afficher les infos de dates des "périodes en cours". Par exemple:
```
Février 2018
01 - 20 février 2018
-------

Année 2018
Janvier - Février 2018
```

Option 1
> Ces dates proviennent du backend et correspondent à des bornes de calcul des indicateurs et donc pas forcément à "Début calendaire de la période" et "Date d'aujourd'hui" ou "Mois en cours". Le frontend récupère ces dates.

Option 2
> Nous considérons qu'il s'agit toujours d'afficher une période en cours du "début calendaire de la Periode" à la "date d'aujourd'hui" ou au "mois en cours".

**Pour le moment, nous partons du principe que l'option 2 est retenue.**


## URL de base et version
Tous les calls sont réalisés sous la forme:

```
base_url/endpoint?params
```
Avec:
- `base_url`: Composée d'une racine `root_url` et d'un numéro de version du backend `vX`, sous la forme `root_url/vX`. Ces éléments sont paramétrables dans l'app dans le fichier `backendService.js`.
- `endpoint?params`: Les endpoints sont décrits ci-dessous et sont regroupés dans le fichier `backendService.js`.

Les paramètres de la `base_url` (`root_url` et `vX`) pourront facilement être modifiés lors de la mise en production et des évolutions du backend.

## Formats
- Les calls sont réalisés en Ajax et attendent des réponses de `Content-type` `application/json`.
- Les dates sont manipulées au format ISO8601 (2013-09-01T22:04:28.000Z)
- Les numéros de moss renvoyés par le backend sont indexés à partir de 1
- Les données énergie sont toutes exprimées en kWH
- Les données de prix sont toutes exprimées en €

## Authentification
### Login
L'app prévoit uniquement une action de Login. La création d'utilisateurs, le recouvrement de mot de passe, etc. se fait en back office Embix. Le schéma d'authentification se fait de la façon suivante:
- l'utilisateur se rend sur l'app et arrive sur le composant de Log In
- Il renseigne son `email` et son `password`
- L'app de front post une requête `base_url/auth/login` avec `email` et `password` en corps de requête
- En cas d'échec, le serveur répond avec une erreur (cf. )
- En cas de success, le serveur répond avec la ressource `User` et un `token`

Ce token est stocké dans le `localStorage` du navigateur de l'utilisateur et ré-utilisé pour tous les autres calls au Backend.

### Calls Authentifiés
En dehors du call de Login, tous les call au Backend NCU doivent être authentifiés. Pour cela, tous les calls intégreront le token en header de la requête.

**Request Headers**
```
{
  'Authorization': 'Bearer $token'
}
```
Par exemple:
```
{
  'Authorization': 'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9'
}
```
Ce `token` permettra au backend NCU de réaliser les opérations nécessaires pour récupérer la Data en DB, sur l'API Urban Power, etc. Si le token envoyé n'est pas valable (token non valide, token expiré, etc.), le backend NCU répondra une erreur 401 Unauthorized.

### Logout
La déconnexion de l'utilisateur se traduit par une "simple" action front:
- suppression du token sauvé dans le localStorage du navigateur
- redirection de l'utilisateur vers le composant de Login


## Ressources
Nous proposons de manipuler les ressources suivantes:
- enrQuartierMois
- enrQuartierAnnee
- enrReseauMois
- enrReseauAnnee

### enrQuartierMois
`enrQuartierMois` décrit les infos liées aux taux d'ENR produits/utilisés par quartier pour un mois. Il est décrit comme suit:
```
{
  annee: 2017, // Integer
  mois: 1, // Integer, mois indexé à partir de 1
  taux: {reel: 32, cible: 34}, // Entiers compris entre [0..100]
  ecarts: { meteo: 1, occupation: 0, performance: 1 }, // Entiers relatifs
  tauxRT2012: { reel: 32, cible: 34 }, // Entiers compris entre [0..100]
  prod: { reel: 660, cible: 657 }, // Entiers positifs
  factureLogement: { reel: 42, cible: 45 }, // Entiers positifs
  factureCommerceM2: { reel: 13, cible: 15 }, // Entiers positifs
  factureBureauM2: { reel: 5, cible: 5 }, // Entiers positifs
  picElectrique: { value: 146, date: "2017-05-11T09:00:00.000Z"},// Entier positif et DateTime
  picThermique: { value: 266, date: "2017-05-11T09:00:00.000Z"},// Entier positif et DateTime
  tauxOccupation: '85-90%' // String
}
