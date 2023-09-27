---
title: "Temps"
date: 2022-11-27
draft: false
---

Le traitement de la date et de l'heure en C se fait en utilisant les fonctions de la bibliothèque standard C "time.h". Cette bibliothèque fournit des fonctions pour la manipulation de la date et de l'heure, la mesure du temps écoulé, la conversion entre différents formats de temps.

### Epoch time

L'**Epoch time** (également appelé Unix time ou POSIX time) est une représentation numérique du temps utilisée dans les systèmes informatiques, en particulier dans les systèmes d'exploitation de type Unix et dans de nombreuses autres applications. Il définit un point de référence temporelle à partir duquel le temps est mesuré sous la forme d'un **nombre entier de secondes écoulées** depuis un instant spécifique.

> Cet instant est le 1er janvier 1970 à 00:00:00 Coordinated Universal Time (UTC).

Ainsi, chaque seconde qui s'écoule depuis le 1er janvier 1970 est représentée par un nombre entier croissant. Par exemple, si vous avez un timestamp Unix de 1632717365, cela signifie qu'il s'est écoulé 1 632 717 365 secondes depuis le 1er janvier 1970.

L'Epoch time présente plusieurs avantages en informatique, notamment :

1. **Universalité** : Il est largement utilisé dans le monde entier, ce qui le rend idéal pour la communication et le stockage de données temporelles.

2. **Comparaison simple** : Comparer deux timestamps est facile, il suffit de comparer les valeurs numériques.

3. **Calculs de durée** : En soustrayant deux timestamps, vous obtenez la durée exacte entre les deux moments.

4. **Stockage efficace** : Les timestamps Unix sont des entiers 32 bits (dans la plupart des systèmes), ce qui les rend compacts en termes de stockage.

Cependant, l'Epoch time présente quelques limitations, notamment la capacité à représenter des dates antérieures au 1er janvier 1970 (avant l'epoch) sur les systèmes 32 bits, car cela conduit à des valeurs négatives. C'est pourquoi de nombreux systèmes utilisent maintenant des timestamps sur 64 bits pour une représentation plus étendue dans le temps.

### La structure `tm`

La structure `tm` (time structure) est utilisée pour représenter une date et une heure. Elle contient les éléments suivants :

- `tm_sec`: Les secondes (0-59).
- `tm_min`: Les minutes (0-59).
- `tm_hour`: Les heures (0-23).
- `tm_mday`: Le jour du mois (1-31).
- `tm_mon`: Le mois (0-11, janvier est 0).
- `tm_year`: L'année depuis 1900.
- `tm_wday`: Le jour de la semaine (0 pour dimanche, 1 pour lundi, etc.).
- `tm_yday`: Le jour de l'année (0-365).
- `tm_isdst`: Un indicateur pour l'heure d'été (Daylight Saving Time).

### La fonction `time()`

La fonction `time()` renvoie l'epoch time. Le retour se fait soit par le `return`` de la fonction, soit par le pointeur sur le paramètre.

Définition

```c
#include <time.h>
time_t time(time_t *seconds);
```

   Exemple d'utilisation :

   ```c
   #include <stdio.h>
   #include <time.h>

   int main() {
    time_t timestamp;
    timestamp = time(NULL);
    printf("Timestamp: %ld\n", timestamp);
   }
   ```

3. **La fonction `localtime()`**

La fonction `localtime()` convertit un timestamp en une structure `tm` représentant l'heure locale.

Définition

```c
#include <time.h>
struct tm *localtime(const time_t *timep);
```

Exemple d'utilisation :

```c
#include <stdio.h>
#include <time.h>

int main() {
  time_t timestamp;
  struct tm *tm_info;

  timestamp = time(NULL);
  tm_info = localtime(&timestamp);

  printf("Current local time and date: %s", asctime(tm_info));
}
```

### La fonction `strftime()`

La fonction `strftime()` permet de formater une structure `tm` en une chaîne de caractères personnalisée.

Définition

```c
#include <time.h>
size_t strftime(char *str, size_t max, const char *format, const struct tm *tm);
```

Voici un exemple simple de code en C qui utilise ces fonctions pour afficher la date et l'heure actuelles au format lisible par l'homme :

```c
#include <stdio.h>
#include <time.h>

int main() {
    time_t t;
    struct tm *tm_info;
    char buffer[26];

    time(&t);
    tm_info = localtime(&t);

    strftime(buffer, 26, "%Y-%m-%d %H:%M:%S", tm_info);
    printf("Date et heure actuelles : %s\n", buffer);

    return 0;
}
```

Ce code utilise `time()` pour obtenir le timestamp actuel, puis `localtime()` pour le convertir en une structure `tm`, et enfin `strftime()` pour formater la date et l'heure dans un format lisible.


### La fonction `strptime()`

La fonction `strptime()` est utilisée pour analyser une chaîne de caractères dans un format donné pour extraire les éléments de date et d'heure et les stocker dans une structure `tm`.

```c
#include <time.h>
char *strptime(const char *s, const char *format, struct tm *tm);
```

### Manipulation de la date et de l'heure

Vous pouvez utiliser les opérations arithmétiques sur les champs de la structure `tm` pour effectuer des calculs de date et d'heure.
