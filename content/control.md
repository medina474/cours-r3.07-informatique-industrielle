---
title: "Structures de contrôle"
date: 2022-11-26T13:37:22+01:00
draft: false
---

Les structures de contrôle, comme les boucles (for, while, do-while) et les instructions conditionnelles (if, else if, else), permettent de contrôler le flux d'exécution du programme en fonction de certaines conditions.

## Boucles

Les boucles permettent de répéter une série d'instructions tant qu'une certaine condition est ou n'est pas vérifiée.

### Boucle while

Tant que expression est vérifiée (c'est à dire non nulle), le bloc d'instruction est exécuté. Si l'expression est nulle au départ, l'instruction ne sera jamais exécutée.

```C
i = 1;
while (i < 10)
{
  printf("\n i = %d",i);
  i++;
}
```

### Boucle do while

La boucle `do while fonctionne comme la boucle `while`, à un détail près : la condition est évaluée **après** le bloc d'instruction. Elle s’exécutera toujours au moins une fois, alors qu’une boucle `while` peut ne pas s’exécuter si la condition est fausse dès le départ.

```C
i = 1;
do
{
  printf("\n i = %d",i);
  i++;
} while (i < 10)
```
### Boucle for

Le for permet de placer au mˆeme endroit l’initialisation, le test de continuit´e
et l’incr´ementation.

f o r (i=0;i <10; i++)
{
printf (" valeur : %d\n",i) ;
}
Il est tout à fait possible de ne pas mettre

## Conditions

if / else

### Sauts

### break

L’instruction `break` sor directement de la boucle d'instruction.

### continue

L’instruction `continue` retourne directement à l’évaluation de la condition d'une boucle. Elle permet de se passer de l'exécution de la fin du bloc d'instruction.

### goto

L’instruction `goto` permet de sauter à un point précis du programme.  Pour ce faire, le langage C nous permet de marquer des instructions à l’aide d’étiquettes (en: label). Une étiquette n’est rien d’autre qu’un nom choisi par nos soins suivi du catactère `:`.

Bien qu’utile dans certaines circonstances, sachez que l'utilisation de l’instruction `goto` est **fortement** déconseillée, principalement pour deux raisons :

- mis à part dans des cas spécifiques, il est possible de réaliser la même action de manière plus claire à l’aide de structures de contrôles ;
- l’utilisation de cette instruction peut amener votre code à être plus difficilement lisible et, dans les pires cas, en faire un code spaghetti.

Elle est essentiellement utilisée dans le cas de la gestion des exceptions et des erreurs.

### switch

L’expression est compar´ee à l’´etiquette. L’ex´ecution s’effectue jusqu’à la fin du switch sauf si une instruction break est rencontr´ee.

Si aucune ´etiquette ne correspond à l’expression, l’´etiquette par d´efaut est s´electionn´ee.

la variable utilis´ee avec l’instruction switch peut ˆetre du type int
(ou compatible) ou char.
