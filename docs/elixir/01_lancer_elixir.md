# Lancer Elixir

## Installer

J'ai une distribution basée sur Arch, donc il s'agit pour moi d'entrer la
commande suivante :

```bash
sudo pacman -S elixir
```

## L'interpréteur

```bash
iex
```

`iex` signifie *Interactive Elixir*. Comme ça tu verras si ton installation
s'est bien passée.

Pour obtenir de l'aide, tape `h`

```elixir
iex> h
```

Pour obtenir des infos sur le module `IO` :

```
iex> h IO
```

ou 

```elixir
iex> h(IO)
```

Le module `IO` contient une fonction `puts` pour afficher une chaîne de
caractère dans la console.

```elixir
iex> h IO.puts
```

## Hello world !

On utilise 2 extensions de fichier pour Elixir: `.ex` et `.exs`.

Les fichiers se terminant par `.ex` sont destinés à être compilés. Tandis que
ceux avec l'extension `.exs` vont être interprétés à la volée par Elixir.

Dans un fichier nommé `hello.exs` :

```elixir
IO.puts "Hello world !
```

Puis lance la commande :

```bash
elixir hello.exs
```
