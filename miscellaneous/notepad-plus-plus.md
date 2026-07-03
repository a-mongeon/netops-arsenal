# Notepad++

## Regex

###

Ne conserver que les lignes contenant la chaîne de caractères :
```
^(?:(?!<word>).)*?$\R*
```

Supprimer *n* fois un charactère *x* à la fin de chaque ligne:
```
[x]{n}$
```
Soit par exemple, 4 fois le charactère ";" :
```
[;]{4}$
```

Supprimer un charactère présent entre d'autres charactères (par exemple, "+" situés entre des ";") :
```
(?<=;)[+](?=;)
```
