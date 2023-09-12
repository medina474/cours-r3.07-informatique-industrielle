---
title: "Arduino"
date: 2022-11-15T07:02:33+01:00
draft: false
---

## Temporisation retardée à la montée (TON)

La liste des fonctions permettant de gérer cette temporisation est décrite dans la suite.

### Création de la temporisation

La création de la temporisation prend en param`etre la durée en millisecondes de la temporisation. Elle doit se faire en haut du fichier et en dehors de toute fonction pour ˆetre utilisable partout dans le code.

Prototype de la fonction : TemporisationRetardMontee nomDeLaTempo(int duree)
1 // Exemple de creation d’une temporisation de 2.5s
2 TemporisationRetardMontee maTempo(2500);


#### Activation de la temporisation

L’activation de la temporisation se fait à l’aide de la fonction activation(). Cette fonction doit ˆetre appelée au moins le temps de la durée de la temporisation pour que la sortie puisse passer à true. Dans le cas contraire la sortie restera à false.

Prototype de la fonction : void activation()
// Exemple d’enclenchement de la temporisation sur une condition
if (condition)
{
  maTempo.activation();
}


## Temporisation retardée à la descente (TOFF)

### Consultation du temps écoulé

Le temps écoulé depuis le début de l’activation de la tempo est récupérable à l’aide de la fonction getTempsEcoule().
Cette fonction renvoie un entier long non signé.
Prototype de la fonction : unsigned long getTempsEcoule()

```C
// Exemple de recuperation du temps ecoule depuis le debut de l’activation
unsigned long t;

if (condition)
{
  maTempo.activation();
  t = maTempo.getTempsEcoule();
  Serial.println(t);
}
```

2.1.4 Consultation de la sortie
