## TOC
- [Notes](#notes)
- [URL de base et version](#url-de-base-et-version)
- [Authentification](#authentification)
- Endpoints

## Notes

## URL de base et version
Tous les calls sont réalisés sous la forme:

```
base_url/endpoint?params
```
Avec:
- `base_url`: Composée d'une racine `root_url` et d'un numéro de version de l'API `vX`, sous la forme `root_url/vX`. Ces éléments sont paramétrables dans l'app dans le fichier `ApiService.js`.
- `endpoint?params`: Les endpoints sont décrits ci-dessous et sont regroupés dans le fichier `ApiService.js`.

Les paramètres de la `base_url` (`root_url` et `vX`) pourront facilement être modifiés lors de la mise en production et des évolutions de l'API.

## Authentification
### Login
L'app prévoit uniquement une action de Login. La création d'utilisateurs, le recouvrement de mot de passe, etc. se fait en back office Embix. Le schéma d'authentification se fait de la façon suivante:
- l'utilisateur se rend sur l'app et arrive sur le composant de Log In
- Il renseigne son `email` et son `password`
- L'app de front post une requête `base_url/auth/login` avec `email` et `password` en corps de requête
- En cas d'échec, le serveur répond avec une erreur (cf. )
- En cas de success, le serveur répond avec la ressource `User` et un `token`
Ce token est stocké dans le hash de session du navigateur de l'utilisateur et ré-utilisé pour tous les autres calls de l'API.

### Call Authentifié
En dehors du call de Login, tous les call à 