# Notepad++

## Regex

###

Ne conserver que les lignes contenant la chaîne de caractères :
```
^(?:(?!<word>).)*?$\R*
```

Supprimer *n* fois un charactère *x* à la fin de chaque ligne:
```
[*x*]{*n*}$
```
Soit par exemple, 4 fois le charactre ";" :
```
[;]{4}$
```
