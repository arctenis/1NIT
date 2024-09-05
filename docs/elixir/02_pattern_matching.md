# Pattern matching

Normalement, c'est à ce moment que je devrais parler des variables dans Elixir.

Lance l'interpréteur `iex`.

Et tape : 

```elixir
iex> x = 1
1
iex> x
1
```

On pourrait dire que `x` est une variable. Elle contient la valeur `1`.

Sauf que non.

```elixir
iex> 1 = x
1
```

Cette expression est vraie. `x` est égal à `1`. En fait, les deux côtés de
l'opérateur `=` sont égaux.

```elixir
iex> 2 = x
** (MatchError) no match of right hand side value: 1
```

Cette expression est fausse, car `x` n'est pas égal à `2`.

Elixir ne va seulement changer la valeur qui est à gauche de l'opérateur `=`. A
droite, une variable va être remplacée par sa valeur.

```elixir
iex> list = ["alice", "bob", "charlie"]
["alice", "bob", "charlie"]
iex> [a, b, c] = list
["alice", "bob", "charlie"]
iex> a
"alice"
iex> b
"bob"
iex> c
"charlie"
```

Elixir va essayer de faire correspondre le contenu de la variable de droite
avec la variable de gauche.

Un autre exemple :

```elixir
iex> [a, 12, c] = [6, 12, 24]
[6, 12, 24]
```

Comme les deuxièmes éléments des deux listes sont égaux, Elixir va affecter la
valeur `6` à la variable `a` et la valeur `24` à la variable `c`.

```elixir
iex> list = ["alice", "bob", "charlie"]
["alice", "bob", "charlie"]
iex> [a, "bill", c] = list
** (MatchError) no match of right hand side value: ["alice", "bob", "charlie"]
```

Ici, Elixir n'arrive pas à faire correspondre le contenu de la variable `list`
à la partie gauche.

TODO

