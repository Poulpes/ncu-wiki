```
   ****************************** DRAFT VERSION ******************************
```


Ce wiki constitue la documentation du projet NCU dans le contexte suivant:

- le Frontend correspond à ce repository. Il s'agit de l'app de front développée par _Poulpes_ qui rend compte des dashboards de visualisation des consommations/productions énergétiques sur le project Nanterre Coeur Université (NCU).
- le Backend correspond à l'application /module back-end développée par Embix pour le projet NCU et qui répond aux calls du Frontend.
- l'API Urban Power développée par Embix et qui centralise la data collectée sur le terrain

Aucun call direct à l'API Urban Power n'est réalisé par le frontend. Le frontend interroge le backend NCU sur des endpoints dédiés et reçoit des réponses sous forme de JSON. Le backend se charge d'interroger l'API Urban Power selon sa propre logique.

La documentation reprend les éléments suivants:

- [Stack Technique Frontend  ](#stack-technique)
- [Getting Started](#getting-started)
- [Echanges Backend](Echanges-Backend)


## Stack Technique

Frontend réalisé en React.js à partir du boilerplate: [create-react-app](https://github.com/facebook/create-react-app). Principales librairies utilisées:

- Routing: [React Router](https://github.com/ReactTraining/react-router)
- Data Storage and Management: [Redux](https://github.com/reactjs/redux), [Redux Saga](https://github.com/redux-saga/redux-saga)
- Call Ajax: [Axios](https://github.com/axios/axios)


## Getting Started

- Cloner le repo
- Dans le terminal `$ npm install` puis `$ npm start`
- L'app est accessible sur `http://localhost:3000/`
