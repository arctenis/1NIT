# Le slicing

Le slicing est une technique qui te permet de récupérer une partie d'une liste.

## Syntaxe

```python
liste[debut:fin:pas]
```

- `debut` : l'indice de départ de la partie à récupérer. Si tu ne précises pas de
  valeur, la partie commence à l'indice 0.
- `fin` : l'indice de fin de la partie à récupérer. Si tu ne précises pas de valeur,
  la partie se termine à la fin de la liste.
- `pas` : le pas de la partie à récupérer. Si tu ne précises pas de valeur, le
  pas est de 1.
  
## Exemples

```python
liste = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

print(liste[2:5]) # [2, 3, 4]
print(liste[:5]) # [0, 1, 2, 3, 4]
print(liste[5:]) # [5, 6, 7, 8, 9]
print(liste[::2]) # [0, 2, 4, 6, 8]
```

## Remarque

Le slicing ne modifie pas la liste d'origine. Il retourne une nouvelle liste.


