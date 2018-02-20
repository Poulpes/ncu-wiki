```
   TO UPDATE AFTER REUNION - VENTILATION /USAGE - ENR QUARTIER / RESEAU / PROD / CONSO
```

Nous proposons de manipuler les ressources suivantes:
- [enrQuartierMois](#enrquartiermois)
- [enrQuartierAnnee](#enrquartierannee)
- [enrReseauMois](#enrreseaumois)
- [enrReseauAnnee](#enrreseauannee)

**En fait, peut-être enrQuartierMois et enrReseauMois ne diffère que par une ou 2 clés ! Ne faudrait-il pas mieux alors faire 2 types de ressource suiviMois et suiviAnnee ?**



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
```

**La data incomplète est présentée sous forme `null` et non pas comme une absence de data**. Par exemple, si le backend ne dispose pas de data ou pas de data valable pour les données de productions et pas de donnes cibles pour les facture bureau au m2, la réponse sera comme suit:
```
{
  annee: 2017, // Integer
  mois: 1, // Integer, mois indexé à partir de 1
  taux: {reel: 32, cible: 34}, // Entiers compris entre [0..100]
  ecarts: { meteo: 1, occupation: 0, performance: 1 }, // Entiers relatifs
  tauxRT2012: { reel: 32, cible: 34 }, // Entiers compris entre [0..100]
  prod: { reel: null, cible: null }, // Entiers positifs
  factureLogement: { reel: 42, cible: 45 }, // Entiers positifs
  factureCommerceM2: { reel: 13, cible: 15 }, // Entiers positifs
  factureBureauM2: { reel: 5, cible: null }, // Entiers positifs
  picElectrique: { value: 146, date: "2017-05-11T09:00:00.000Z"},// Entier positif et DateTime
  picThermique: { value: 266, date: "2017-05-11T09:00:00.000Z"},// Entier positif et DateTime
  tauxOccupation: '85-90%' // String
}
```

### enrQuartierAnnee
`enrQuartierAnnee` décrit les infos liées aux taux d'ENR produits/utilisés par quartier pour une annee. Il est décrit comme suit:
```
{
  annee: 2015,
  taux: {reel: 32, cible: 34}, // Entiers compris entre [0..100]
  ecarts: { meteo: 1, occupation: 0, performance: 1 }, // Entiers relatifs
  tauxRT2012: { reel: 32, cible: 34 }, // Entiers compris entre [0..100]
  prod: { reel: null, cible: null }, // Entiers positifs
  factureLogement: { reel: 42, cible: 45 }, // Entiers positifs
  factureCommerceM2: { reel: 13, cible: 15 }, // Entiers positifs
  factureBureauM2: { reel: 5, cible: null }, // Entiers positifs
  picElectrique: { value: 146, date: "2017-05-11T09:00:00.000Z"},// Entier positif et DateTime
  picThermique: { value: 266, date: "2017-05-11T09:00:00.000Z"},// Entier positif et DateTime
  tauxOccupation: '85-90%' // String
}
```

**La data incomplète est présentée sous forme `null` et non pas comme une absence de data**. (cf. [enrQuartierMois](#enrquartiermois)).

### enrReseauMois
`enrReseauMois` décrit les infos liées aux taux d'ENR produits/utilisés par réseau de chaleur pour un mois. **Nous avons supposé, qu'il pouvait se décrire comme `enrQuartierMois`**:
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
```

**La data incomplète est présentée sous forme `null` et non pas comme une absence de data**.. (cf. [enrQuartierMois](#enrquartiermois)).

### enrReseauAnnee
`enrReseauAnnee` décrit les infos liées aux taux d'ENR produits/utilisés par réseau de chaleur pour une année. Il est décrit comme suit:
```
{
  annee: 2015,
  taux: {reel: 32, cible: 34}, // Entiers compris entre [0..100]
  ecarts: { meteo: 1, occupation: 0, performance: 1 }, // Entiers relatifs
  tauxRT2012: { reel: 32, cible: 34 }, // Entiers compris entre [0..100]
  prod: { reel: null, cible: null }, // Entiers positifs
  factureLogement: { reel: 42, cible: 45 }, // Entiers positifs
  factureCommerceM2: { reel: 13, cible: 15 }, // Entiers positifs
  factureBureauM2: { reel: 5, cible: null }, // Entiers positifs
  picElectrique: { value: 146, date: "2017-05-11T09:00:00.000Z"},// Entier positif et DateTime
  picThermique: { value: 266, date: "2017-05-11T09:00:00.000Z"},// Entier positif et DateTime
  tauxOccupation: '85-90%' // String
}
```

**La data incomplète est présentée sous forme `null` et non pas comme une absence de data**. (cf. [enrQuartierMois](#enrquartiermois)).

