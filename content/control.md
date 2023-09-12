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

## Conditions

### Sauts

### break

L’instruction `break` sor directement de la boucle d'instruction.

### continue

L’instruction `continue` retourne directement à l’évaluation de la condition d'une boucle. Elle permet de se passer de l'exécution de la fin du bloc d'instruction.

### goto
