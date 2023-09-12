---
title: "Programme"
date: 2023-09-11T13:47:52+01:00
draft: false
---

## De quoi se compose un programme ?


### Fichiers sources

Ils contiennent le code des fonctions et les variables globales. Ils ont l’extension **.c** et un seul contient le main.

## Fichiers d’en-têtes

Ils contiennent uniquement des d´eclarations de type, de fonctions, de macros, de variables globales, etc. Ils ont l’extension .h.

## Librairies

Elles contiennent le code compilé des fonctions des bibliothèques. Elles ont l’extension .lib ou .dll sous Windows (.so sous Linux).

## Compilation

Chaque fichier source doit aussi avoir son fichier d’en-tˆetes.
Fichier somme.c
# include " somme .h"
f l o a t somme ( f l o a t a, f l o a t b)
{
r e t u r n (a+b) ;
}
Fichier somme.h
f l o a t somme ( f l o a t a, f l o a t b) ;
La compilation de chaque fichier .c et de son .h associ´e g´en`ere un fichier .obj (Windows) ou .o (Linux).
Attention
La compilation n’est qu’une v´erification syntaxique du code, cela ne garantie en aucun
le bon fonctionnement du programme ! ! ! !

## L’´edition de liens

Si votre programme utilise des fonctions d’une biblioth`eque C quelconque
(printf, scanf, ....) il faut que le code de ces fonctions soit int´egr´e `a votre
programme.
Pour cela, il faut inclure le fichier d’en-tˆetes.
Fichier xxxx.c
# include < stdio .h >
i n t main ( i n t argc , c h a r * argv [])
{
printf (" Hello World !!! ") ;
}
L’´edition de liens (linkage en anglais) lie chaque librairie `a vos fichiers compil´es pour
g´en´erer l’ex´ecutable .exe (Windows) ou .out (Linux).

Si votre programme utilise des fonctions d’une biblioth`eque C que vous avez
cr´e´ee il faut que le code de ces fonctions soit int´egr´e `a votre programme.
Pour cela, il faut inclure le fichier d’en-tˆetes.
Fichier xxxx.c
# include " somme .h"
i n t main ( i n t argc , c h a r * argv [])
{
printf ("%f",somme (4 ,5) ) ;
}
L’´edition de liens (linkage en anglais) lie chaque librairie `a vos fichiers compil´es pour
g´en´erer l’ex´ecutable (.exe sous Windows) ou .out (Linux).

##
