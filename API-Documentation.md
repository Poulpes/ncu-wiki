## TOC
- [Notes](#notes)
- [URL de base et version](#url-de-base-et-version)
- Authentification
- Endpoints

## Notes

## URL de base et version
Tous les calls sont réalisés sous la forme:

```
url-de-base\vX\endpoint?params
```
Avec:
- `url-de-base`: Paramétrable dans l'app dans le fichier `ApiService.js` dans la variable $$.
- `vX`: Paramétrable dans l'app dans le fichier `ApiService.js` dans la variable $$.
- `endpoint?params`: Les endpoints sont décrits ci-dessous et sont regroupés dans le fichier `ApiService.js`.

L'`url-de-base` pourra facilement être modifié lors de la mise en production.
L'usage du numéro de version `vX` dans les call permettra de faire évoluer l'API sans bloquer les calls de l'App de FRont.