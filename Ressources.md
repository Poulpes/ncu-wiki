```
   TO UPDATE AFTER REUNION - VENTILATION /USAGE - ENR QUARTIER / RESEAU / PROD / CONSO
```

Nous proposons de manipuler les ressources suivantes:

- [enrQuartierMois](#enrquartiermois)
- [enrQuartierAnnee](#enrquartierannee)
- [enrReseauMois](#enrreseaumois)
- [enrReseauAnnee](#enrreseauannee)
- [suiviMois](#suiviMois)
- [suiviAnnee](#suiviAnnee)
- [consoMois](#consoMois)
- [consoAnnee](#consoAnnee)


**En fait, peut-être enrQuartierMois et enrReseauMois ne diffère que par une ou 2 clés ! Ne faudrait-il pas mieux alors faire 2 types de ressource `suiviMois` et `suiviAnnee` ?**



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

### suiviMois

`suiviMois` décrit les infos de suivi par mois en termes d'ENR par quartier, ENR par réseau de chaleur, de production d'énergie et de consommation d'énergie:
```
{
  annee: 2017, // Integer
  mois: 4, // Integer, mois indexé à partir de 1
  objectif: 70, // Integer [0..100]
  enrQuartier: {
    taux: {reel: 32, cible: 34}, // Entiers compris entre [0..100],
    rt2012: {reel: 32, cible: 34}, // Entiers compris entre [0..100] même chose que le taux ?,
    prod: { reel: 660, cible: 657 }, // Entiers positifs
    ecarts: { meteo: 1, occupation: 0, performance: 1 } // Entiers relatifs
  },
  enrReseau: {
    taux: {reel: 32, cible: 34}, // Entiers compris entre [0..100],
    rt2012: {reel: 32, cible: 34}, // Entiers compris entre [0..100] même chose que le taux ?,
    prod: { reel: 660, cible: 657 }, // Entiers positifs
    ecarts: { meteo: 1, occupation: 0, performance: 1 } // Entiers relatifs
  },
  conso: {
    toutUsage: {reel: 239, cible: 1367}, // Entiers positifs
    parUsage: {
      eclairage: {reel: 239, cible: 1367}, // Entiers positifs
      auxiliaire: {reel: 139, cible: 1357}, // Entiers positifs
      eauChaude: {reel: 139, cible: 1357}, // Entiers positifs
      chauffage: {reel: 139, cible: 1357}, // Entiers positifs
      refroidissement: {reel: 139, cible: 1357}, // Entiers positifs
      usage_spec: {reel: 139, cible: 1357} // Entiers positifs
    }
  },
  prod: { reel: 660, cible: 657 }, //Entiers positifs
  factureLogement: { reel: 42, cible: 45 }, // Entiers positifs
  factureCommerceM2: { reel: 13, cible: 15 }, // Entiers positifs
  factureBureauM2: { reel: 5, cible: 5 }, // Entiers positifs
  picElectrique: { value: 146, date: "2017-05-11T09:00:00.000Z"},// Entier positif et DateTime
  picThermique: { value: 266, date: "2017-05-11T09:00:00.000Z"},// Entier positif et DateTime
  tauxOccupation: '85-90%', // String
}
```

**La data incomplète est présentée sous forme `null` et non pas comme une absence de data**. (cf. [enrQuartierMois](#enrquartiermois)).

### suiviAnnee

`suiviAnnee` décrit les infos de suivi par année en termes d'ENR par quartier, ENR par réseau de chaleur, de production d'énergie et de consommation d'énergie:
```
{
  annee: 2017, // Integer
  objectif: 70, // Integer [0..100]
  arbreSauves: 15.4, // Réel positif
  tauxCO2: -6, // Reel
  economieLogement: 54,
  enrQuartier: {
    taux: {reel: 32, cible: 34}, // Entiers compris entre [0..100],
    rt2012: {reel: 32, cible: 34}, // Entiers compris entre [0..100] même chose que le taux ?,
    prod: { reel: 660, cible: 657 }, // Entiers positifs
    ecarts: { meteo: 1, occupation: 0, performance: 1 } // Entiers relatifs
  },
  enrReseau: {
    taux: {reel: 32, cible: 34}, // Entiers compris entre [0..100],
    rt2012: {reel: 32, cible: 34}, // Entiers compris entre [0..100] même chose que le taux ?,
    prod: { reel: 660, cible: 657 }, // Entiers positifs
    ecarts: { meteo: 1, occupation: 0, performance: 1 } // Entiers relatifs
  },
  conso: {
    toutUsage: {reel: 239, cible: 1367}, // Entiers positifs
    parUsage: {
      eclairage: {reel: 239, cible: 1367}, // Entiers positifs
      auxiliaire: {reel: 139, cible: 1357}, // Entiers positifs
      eauChaude: {reel: 139, cible: 1357}, // Entiers positifs
      chauffage: {reel: 139, cible: 1357}, // Entiers positifs
      refroidissement: {reel: 139, cible: 1357}, // Entiers positifs
      usage_spec: {reel: 139, cible: 1357} // Entiers positifs
    }
  },
  prod: { reel: 660, cible: 657 }, //Entiers positifs
  factureLogement: { reel: 42, cible: 45 }, // Entiers positifs
  factureCommerceM2: { reel: 13, cible: 15 }, // Entiers positifs
  factureBureauM2: { reel: 5, cible: 5 }, // Entiers positifs
  picElectrique: { value: 146, date: "2017-05-11T09:00:00.000Z"},// Entier positif et DateTime
  picThermique: { value: 266, date: "2017-05-11T09:00:00.000Z"},// Entier positif et DateTime
  tauxOccupation: '85-90%', // String
}
```

**La data incomplète est présentée sous forme `null` et non pas comme une absence de data**. (cf. [enrQuartierMois](#enrquartiermois)).

### consoMois

`consoMois` décrit les infos de consommation par lot et par usage. En fait non, il faudrait mettre en clé principale les lots ! Et ventilés par usage 'en dessous'
```
{
  annee: 2017, // Integer
  mois: 4, // Integer, mois indexé à partir de 1
  conso: {
    toutUsage: {
      toutLot: {reel: 239, cible: 1367, reel_n_1: 22},
      parLot: [
       {label: '3 log', reel: 23, cible: 34, ecart: {meteo: 12, occupation: 5, performance: 6}},
       {label: '3 Com', reel: 23, cible: 34, ecart: {meteo: 12, occupation: 5, performance: 6}},
       {label: '4 Bur', reel: 23, cible: 34, ecart: {meteo: 12, occupation: 5, performance: 6}},
       etc
      ]
    },
    parUsage: {
      eclairage: {
        toutLot: {reel: 239, cible: 1367, reel_n_1: 22},
        parLot: [
         {label: '3 log', reel: 23, cible: 34, ecart: {meteo: 12, occupation: 5, performance: 6}},
         {label: '3 Com', reel: 23, cible: 34, ecart: {meteo: 12, occupation: 5, performance: 6}},
         {label: '4 Bur', reel: 23, cible: 34, ecart: {meteo: 12, occupation: 5, performance: 6}},
         etc
        ]
      },
      eclairage: {
        toutLot: {reel: 239, cible: 1367, reel_n_1: 22},
        parLot: [
         {label: '3 log', reel: 23, cible: 34, ecart: {meteo: 12, occupation: 5, performance: 6}},
         {label: '3 Com', reel: 23, cible: 34, ecart: {meteo: 12, occupation: 5, performance: 6}},
         {label: '4 Bur', reel: 23, cible: 34, ecart: {meteo: 12, occupation: 5, performance: 6}},
         etc
        ]
      },
    }
  },
  prod: { reel: 660, cible: 657 }, //Entiers positifs
  factureLogement: { reel: 42, cible: 45 }, // Entiers positifs
  factureCommerceM2: { reel: 13, cible: 15 }, // Entiers positifs
  factureBureauM2: { reel: 5, cible: 5 }, // Entiers positifs
  picElectrique: { value: 146, date: "2017-05-11T09:00:00.000Z"},// Entier positif et DateTime
  picThermique: { value: 266, date: "2017-05-11T09:00:00.000Z"},// Entier positif et DateTime
  tauxOccupation: '85-90%', // String
}
```

**La data incomplète est présentée sous forme `null` et non pas comme une absence de data**. (cf. [enrQuartierMois](#enrquartiermois)).
