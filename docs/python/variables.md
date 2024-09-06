# Variables et affectations

**Niveau** : intermédiaire

**Prérequis** :

- Connaître les types de données en Python (chaînes de caractères, listes,
  tuples...)
- Connaître les opérations de base en Python
- Avoir déjà utilisé des variables en Python

## Comment lire ce document ?

Même s'il n'y a pas d'exercices dans ce guide, tu peux lancer un interpréteur
Python pour tester les différents exemples de code.

Les variables sont certes un sujet pour débutants, mais il risque de te rebuter
si tu débutes. Il vaut mieux avoir déjà manipulé des variables en Python avant
de creuser ce sujet comme présenté ici.

## Principes

Quelques principes à connaître qui auront un impact plus tard :

**Les affectations créent des références à des objets.**

Python stocke des références à des objets dans des noms, aussi appelés
variables. Les variables ne stockent pas directement les objets, mais des
références à ces objets. On peut considérer les variables comme des pointeurs
plutôt que des "boîtes" qui contiendraient des données.

**Les noms sont créés lorsqu'ils sont affectés.**

Les noms de variables n'ont pas besoin d'être déclarés explicitement. Ils sont
créés lorsqu'ils sont affectés pour la première fois.

Une fois l'affectation faite, le nom sera remplacé par la valeur de l'objet
vers lequel il pointe.

**Les noms doivent être affectés avant d'être utilisés.**

Python va levé une exception si tu essaies d'utiliser un nom qui n'a pas été
affecté.

**Certaines instructions effectuent des affectations implicites.**

Par exemple, les importations de modules, les affectations dans les boucles
`for`, les affectations dans les listes en compréhension...

Ces affectations fonctionnent comme les autres, elles n'utilisent pas forcément
le signe `=`.

## Types d'affectations

| Instruction         | Signification         |
|---------------------|-----------------------|
| a = 0               | Affectation basique   |
| a = b = 0           | Affectation multiple  |
| a, b = 0, 1         | Affectation de tuple  |
| [a, b] = [0, 1]     | Affectation de liste  |
| a, b, c, d = "1234" | Affectation de chaîne |
| a, *b = 0, 1, 2, 3  | Affectation étendue   |
| a += 1              | Affectation augmentée |



