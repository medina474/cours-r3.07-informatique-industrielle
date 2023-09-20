---
title: "Variables"
date: 2022-11-27
draft: false
---

>Une variable est un espace de stockage dans la mémoire de l'ordinateur qui associe un **identifiant** à une **valeur**.
{.definition}

### Caractéristiques

Une variable possède plusieurs caractéristiques ou propriétés.

La **déclaration**, c'est l'endroit dans le code qui défini l'existence de la variable.

```C
int age;
```

Un **nom** sous lequel la variable est déclarée. Dans cette déclaration le nom de la variable est `age`.

Un **type**. Dans la mémoire d'un ordinateur, toute information est stockée sous forme d'éléments binaires appelés `bit` (en: binary digit, nombre binaire). Un même ensemble de bits peut être représenté sous différentes aspects : nombre entier, nombre réel, texte, photo, vidéo, audio, ... C'est la convention d'interprétation du type qui défini la valeur de la variable.

Dans cette déclaration le type de la variable `age` est un entier `int`.

La **taille** associée au type. Dans le cas des types fixe, le type de la variable spécifie aussi le nombre de bits ou le nombre de mots (en: bytes, octets) utilisés.

Dans cette déclaration la taille de la variable `age` est de 4 octets soit 32 bits, qui est la taille associée à un type `int`.

La **valeur**, c'est la valeur intrasèque des bits suivant la représentation associée au type;

```C
age = 10;
```

Dans cet exemple la valeur de la variable `age` est `10`.

L'**adresse**, c'est l'endroit dans la mémoire de l'ordinateur où est stockée physiquement la variable.

```C
printf("%p", &age);
```

La **portée**, c'est la portion de code où la variable est utilisable. Une variable est accessible depuis sa définition jusqu'à la fin du bloc où elle est déclarée.

Sa **durée de vie**, c'est le temps d'exécution pendant laquelle la variable existe. Il est possible de masquer une variable par une autre en utilisant un même identifiant. La première variable est hors de portée mais existe toujours. Une variable `static` est utilisable que dans la fonction dans laquelle elle a été déclarée, cependant sa durée de vie s'étend sur l'intégralité de l'éxécution du programme.

Sa **visibilité**, dans un langage évolué comme le C++, le C# ou Java, c'est un ensemble de règles qui fixe qui peut utiliser la variable.

### Règles

#### Déclaration

>Les variables doivent être déclarées **avant** d'être utilisées.
{.warning}

```C
#include <stdio.h>

void main()
{
  printf("%d", age);
  int age = 10;
}
```

Ce code provoque une erreur : la variable est non déclarée avant sont utilisation !

```
error: ‘age’ undeclared (first use in this function)
```

Voici le code correct

```C
#include <stdio.h>

void main()
{
  int age = 10;
  printf("%d", age);
}
```

## Expressions littérales

Dans un programme il est possible de manipuler des valeurs sans pour autant les avoir déclarées avant. Ces valeurs existent de manières littérales à l'intérieur même du code du programme.

>Attention, dans le cas des chaines de caractères, il ne faut pas confondre le nom de la variable avec sa valeur.
{.warning}

```C
char joueur[10] = "Alice";

printf("%s\n", "joueur");
printf("%s\n", joueur);
```

`"joueur"` avec des guillemets est une valeur littérale. On peut considérer, sans que cela soit le cas, que c'est une variable sans nom, qui possède la valeur `joueur`.

## Types de données

Le codage des types de données dépend du compilateur utilisé et par conséquent de la plateforme sur laquelle sera exécutée le programme.

- Compilateur 16 bits ⇒ Entier codé sur 16 bits ⇒ Processeur 16 (ou 32) bits.
- Compilateur 32 bits ⇒ Entier codé sur 32 bits ⇒ Processeur 32 (ou 64) bits.

### Les entiers signés

 type | bits |  min  | max
---|--:|--:|--:
char          |  8 | -127 | 128
short int     | 16 |  −32 768  | 32 767
int           | 32 |  −2 147 483 648 | 2 147 483 647
long int      | 32 |  −2 147 483 648 | 2 147 483 647
long long int | 64 |  −9 223 372 036 854 775 808 | 9 223 372 036 854 775 807


### Les entiers non signés

type | bits | max
---|--:|--:
unsigned char          |  8 | 255
unsigned short int     | 16 | 65 535
unsigned int           | 32 | 4 294 967 295
unsigned long int      | 32 | 4 294 967 295
unsigned long long int | 64 | 18 446 744 073 709 551 615

### Les caractères

I char : codé sur 8 bits (de −127 à 128) ;
I unsigned char : codé sur 8 bits (de 0 à 255) ;
I Utilisable pour stocker des entiers. (Ex : images numériques).
I Contiennent des codes ASCII → 256 caractères.
I Problème des caractères étendus....

### Les flottants

Les nombres à virgule flottante permettent de représenter des nombres de très grandes dimensions de manière équivalente à la notation scientifique 10<sup>n</sup>.

Il y a deux aspects très importants à prendre en compte.

Premièrement le nombre de chiffres significatifs. Avec un nombre à 20 chiffres, les 20 chiffres ne sont pas tous représentés. Au bout d'un certain nombre la puissance intervient et les chiffres de poids faibles sont perdus.

Par exemple 85 362 465 409 651 267 158 est représenté en nombre à virgule flottante par 8,535 246.10<sup>19</sup> ce qui est après 246 est perdu. Le nombre réel que l'on pourraint obtenir en base 10 est 85 362 460 000 000 000 000.

Contrairements aux calcultatrices scientifiques l'exposant n'est pas 10. Le nombre n'est pas sous la forme 8,535.10<sup>19</sup> mais sous la forme 8,535.2<sup>60</sup>. La conséquence est que les nombres décimaux relatifs, c'est à dire avec des nombres limités de chiffres après la virgule, ne le sont peut être plus quand ils sont exprimés en base 2.


type | octets |  bits | min  | max
---|--:|--:|--:|--:
float       |  4 |  32 | 1.175494e-38 | 3.402823e+38
double      |  8 |  64 | 2.225074e-308 | 1.797693e+308
long double |  16 | 128 |3.362103e-4932 |  1.189731e+4932


I float : codé sur 32 bits : 1 bit de signe, 23 bits de mantisse, 8 bits
d’exposant (de ≈ −3, 4.1038 à ≈ 3, 4.1038) - Précision de 10−7


I double : codé sur 64 bits : 1 bit de signe, 52 bits de mantisse, 11 bits
d’exposant (de ≈ −1, 8.10308 à ≈ 1, 8.10308) - Précision de 10−16 ;

I long double : codé sur 80 bits : 1 bit de signe, 64 bits de mantisse, 15
bits d’exposant (de ≈ −3, 4.104932 à ≈ 3, 4.104932) - Précision de 10−19 ;

I Problème du codage en virgule flottante...
