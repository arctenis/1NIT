# Coder un pomodoro

**Niveau** : débutant

**Prérequis** : 

- Avoir Python installé sur sa machine
- Ecrire un script Python
- Utiliser un terminal et la ligne de commande
- Exécuter un script Python

## Comment lire ce document

Ne copie pas le code au fur et à mesure. Lis une première fois. Puis, essaie de coder le script 
sans regarder ce guide. Si tu es bloqué, reviens lire les explications.

## Introduction

Un pomodoro est une technique de gestion du temps. Elle consiste à travailler
pendant 25 minutes, puis à faire une pause de 5 minutes. Après 4 pomodoros, on
fait une pause de 15 à 30 minutes.

Le script que tu vas coder va afficher un compte à rebours dans le terminal. Tu
pourras préciser en arguments les durées de travail et de pause.

## Objectif

Pour lancer le script, tu pourras taper :

```bash
python pomo.py 25 5
```

Il affichera un compte à rebours de 25 minutes, puis de 5 minutes et
s'arrêtera.

```
$ python pomo.py 25 5
Work time: 25 minutes
Break time: 5 minutes
Press Ctrl+C to exit
WORK
21:42
```
## Les modules

Créer un script Python, par exemple `pomo.py`.

Importe les modules `time` et `sys`.

Le module `time` te permettra de gérer le temps. Le module `sys` te permettra
de récupérer les arguments passés au script.

```python
import time
import sys
```

## Les arguments

Récupère les arguments passés au script.

```python
args = sys.argv[1:]
```

`sys.argv` est une liste qui contient les arguments passés au script. Le
premier élément est le nom du script. Les arguments passés au script sont les
éléments suivants.

Pour récupérer tous les éléments d'une liste sauf le premier, on utilise une
technique appelée *slicing*. 

> Pour plus d'infos sur le *slicing*, tu pourras lire [cet article](slicing.md).

Vérifie s'il y a bien deux arguments passés au script. Si ce n'est pas le cas,
affiche un message d'erreur.

D'abord, vérifie la longueur de la liste `args`. Si elle n'est pas égale à 2,
affiche un message d'erreur où tu précises comment utiliser le script.

Puis, quitte le script avec le code d'erreur 1.

Historiquement, quand un programme se déroule bien, il retourne la valeur 0. Si
un programme se termine avec une erreur, il retourne une valeur différente de
0. Il n'y a pas de règle précise pour les valeurs de retour, mais le code 1 est
souvent utilisé pour les erreurs.

```python
if len(args) != 2:
    print("Usage: python pomo.py <work_time_in_min> <break_time_in_min>")
    sys.exit(1)
```

`args` contient certes les arguments passés au script par l'utilisateur, mais
ce sont des chaînes de caractères. Il faut les convertir en entiers pour
pouvoir les utiliser.

```python
work_time = int(args[0])
break_time = int(args[1])
```

La fonction `int` fournit par Python convertit une chaîne de caractères en
entier, à condition bien sûr que la chaîne ne contienne que des chiffres.

On accède aux éléments de la liste `args` par leur indice. L'indice du premier
élément est 0, celui du deuxième est 1, etc. Les indices sont spécifiés entre
crochets comme tu peux le voir.

Pour rappel, on compte à partir de 0 en informatique.

## Afficher les durées

Affiche les durées de travail et de pause.

```python
print(f"Work time: {work_time} minutes")
print(f"Break time: {break_time} minutes")
print("Press Ctrl+C to exit")
```

Grâce au formatage de chaînes de caractères, en ajoutant un `f` avant les
guillemets, tu peux insérer des variables dans une chaîne en utilisant des
accolades `{}`. Tu peux aussi ajouter des expressions Python dans les
accolades.

Pour rappel, `Ctrl+C` permet d'arrêter un script Python en cours d'éxécution.

## Le compte à rebours

Notre compte à rebours va se dérouler en deux étapes : le travail et la pause.

On va donc le lancer deux fois. Il prendra en argument un nombre de minutes.

Aussi, il va afficher le temps restant toutes les secondes.

Définis une fonction `countdown` qui prend en argument le nombre de minutes.

```python
def countdown(total_minutes):
```

Convertis le nombre de minutes en secondes.

```python
total_seconds = total_minutes * 60
```

Maintenant, on va afficher le temps restant toutes les secondes. Pour cela, il
va falloir boucler sur le nombre de secondes restantes.

```python
while total_seconds:
    # Afficher le temps restant
    time.sleep(1)
    total_seconds -= 1
```

Concernant la boucle `while`, on peut utiliser un entier directement dans une
condition, car un entier égal à zéro est considéré comme faux.

Donc la boucle s'arrêtera dès que `total_seconds` sera égal à zéro.
Tu vas afficher le temps restant au format `mm:ss`. Tu retrouveras souvent ce
type d'abréviation pour la mesure du temps. `mm` pour les minutes et `ss` pour
les secondes.

Pour ça, il faut que tu calcules les minutes et les secondes restantes.

```python
mins, secs = divmod(total_seconds, 60)
```

`divmod` est une fonction qui divise un nombre par un autre et retourne le
résultat de la division et le reste de la division. 

Pense aux divisions avec reste telles qu'on les faisait à l'école.

`divmod` renvoie un *tuple* de deux éléments. C'est pour ça qu'on peut les
assigner à deux variables en même temps.

Ici, on divise le nombre de secondes restantes par 60. `mins` contient le
résultat de la division et `secs` le reste.

Puis il s'agit d'afficher tout ça.

```python
timeformat = f"{mins:02d}:{secs:02d}"
print(timeformat, end="\r")
```

`f"{mins:02d}"` signifie que tu veux afficher `mins` sur deux caractères. Si
`mins` est inférieur à 10, il sera complété par un zéro.

Même chose pour les secondes.

`end="\r"` permet de revenir au début de la ligne. C'est pour que le temps
restant soit affiché sur la même ligne. 

L'option `end` de la fonction `print` permet de spécifier le caractère qui sera
ajouté à la fin de la chaîne à afficher. 

Par défaut, c'est un retour à la ligne. Du coup, on le remplace par un retour
au début de la ligne : `\r`.

Voici la fonction complète :

```python
def countdown(total_minutes):
    total_seconds = total_minutes * 60
    while total_seconds:
        # mins, secs = (total_seconds // 60, total_seconds % 60)
        mins, secs = divmod(total_seconds, 60)
        timeformat = f"{mins:02d}:{secs:02d}"
        print("", end="\r")  # Clear the line
        print(timeformat, end="\r") 
        time.sleep(1)
        total_seconds -= 1
```

J'ai ajouté une ligne pour effacer la ligne avant d'afficher le temps restant.


## Tout le script

```python
#!/usr/bin/python3
"""
Pomodoro timer in the terminal
"""

import time
import sys


def countdown(total_minutes):
    total_seconds = total_minutes * 60
    while total_seconds:
        mins, secs = divmod(total_seconds, 60)
        timeformat = f"{mins:02d}:{secs:02d}"
        print("", end="\r")
        print(timeformat, end="\r") 
        time.sleep(1)
        total_seconds -= 1


args = sys.argv[1:]

if len(args) != 2:
    print("Usage: python pomo.py <work_time> <break_time>")
    print("Time in minutes")
    print("Example: python pomo.py 25 5")
    sys.exit(1)

work_time = int(args[0])
break_time = int(args[1])

print(f"Work time: {work_time} minutes")
print(f"Break time: {break_time} minutes")
print("Press Ctrl+C to exit")

print("WORK")
countdown(work_time)

print("BREAK")
countdown(break_time)

print("Time's up!")
sys.exit(0)
```

Pour finir, on lance le compte à rebours pour le travail, puis pour la pause.
Et on quitte proprement le script avec le code 0.

## Conclusion

Tu as codé un script Python qui affiche un compte à rebours dans le terminal.

Tu as pu voir :

- Comment récupérer les arguments passés au script
- Comment afficher des messages dynamiques dans le terminal
