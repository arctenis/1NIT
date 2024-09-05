# Coder un pomodoro

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
# work_time, break_time = map(int, args)
```

La fonction `int` fournit par Python convertit une chaîne de caractères en
entier, à condition bien sûr que la chaîne ne contienne que des chiffres.

On accède aux éléments de la liste `args` par leur indice. L'indice du premier
élément est 0, celui du deuxième est 1, etc. Les indices sont spécifiés entre
crochets comme tu peux le voir.

Pour rappel, on compte à partir de 0 en informatique.

J'ai mis en commentaire une autre façon de convertir les éléments de la liste
`args` en entiers. C'est une technique appelée *unpacking*. Elle permet de
déballer les éléments d'une liste dans des variables.

Je ne l'utilise pas ici, mais elle aurait été pratique si jamais la liste était
beaucoup plus longue.

> Pour plus d'infos sur le *unpacking*, tu pourras lire [cet
> article](unpacking.md).

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


```python
def countdown(total_minutes):
    total_seconds = total_minutes * 60
    while total_seconds:
        # mins, secs = (total_seconds // 60, total_seconds % 60)
        mins, secs = divmod(total_seconds, 60)
        timeformat = f"{mins:02d}:{secs:02d}"
        print("", end="\r")  # Clear the line
        print(timeformat, end="\r")  # Print the time on the same line
        time.sleep(1)
        total_seconds -= 1
```

