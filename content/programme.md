---
title: "Programme en C"
date: 2023-09-11T13:47:52+01:00
draft: false
---

Le langage de programmation C est apprécié pour sa performance, sa portabilité et sa flexibilité. Il est largement utilisé dans le développement de logiciels système (OS), de pilotes de périphériques, d'applications embarquées, de jeux vidéo, et dans de nombreux autres domaines. De plus, de nombreuses langues de programmation modernes, telles que C++, Java, C#, Dart, GoLang, Swift et Python, ont été influencées par le langage C.

## De quoi se compose un programme ?

### Fichiers sources

Ils contiennent le code des fonctions et les variables globales. Ils ont l’extension **.c** et un seul contient le main.

### Fichiers d’en-têtes

Ils contiennent uniquement des déclarations de type, de fonctions, de macros, de variables globales, etc. Ils ont l’extension .h.

### Librairies

Elles contiennent le code compilé des fonctions des bibliothèques. Elles ont l’extension .lib ou .dll sous Windows (.so sous Linux).

## Étapes pour obtenir un programme exécutable

### Préprocesseur

Le fichier source est analysé par le préprocesseur qui effectue des remplacemens de chaînes de caractères et des inclusions d'autres fichiers source.
...).

### Compilation

Chaque fichier source doit aussi avoir son fichier d’en-tˆetes.

Fichier somme.c

```C
#include "somme .h"
float somme(float a, float b)
{
  return(a+b) ;
}
```

Fichier somme.h

```C
float somme (float a, float b);
```

La compilation de chaque fichier .c et de son .h associé génère un fichier .obj (Windows) ou .o (Linux).

> La compilation n’est qu’une vérification syntaxique du code, cela ne garantie en aucun cas le bon fonctionnement du programme ! ! ! !
{.warning}

### L’édition de liens

un programme est souvent séparé en plusieurs fichiers source, pour des raisons de clarté mais aussi parce qu'il fait généralement appel à des librairies de fonctions standard déjà écrites. Une fois chaque code source compilé en fichiers objets, il faut les lier entre eux. L'édition de liens produit alors un fichier dit exécutable.

Si votre programme utilise des fonctions d’une bibliothèque C quelconque
(printf, scanf, ....) il faut que le code de ces fonctions soit intégré `a votre programme.
Pour cela, il faut inclure le fichier d’en-tˆetes.


```C
#include <stdio .h>

int main (int argc , char *argv[])
{
  printf (" Hello World !!! ") ;
}
```

L’édition de liens (linkage en anglais) lie chaque librairie `a vos fichiers compilés pour générer l’exécutable .exe (Windows) ou .out (Linux).

Si votre programme utilise des fonctions d’une bibliothèque C que vous avez vous même créée il faut que le code de ces fonctions soit intégré `a votre programme.
Pour cela, il faut inclure le fichier d’en-tˆetes.

```C
#include "somme.h"

int main ( int argc , char * argv [])
{
  printf ("%f", somme (4 ,5) ) ;
}
```

L’édition de liens (linkage en anglais) lie chaque librairie `a vos fichiers compilés pour générer l’exécutable (.exe sous Windows) ou .out (Linux).

##
