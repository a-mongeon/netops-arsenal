# Expressions régulières
Quelques expressions régulières utiles.

*Matcher* n'importe quelle chaîne de caractères :
```
(.*)
```

*Matcher* un chiffre entre 0 et 9 :
```
\d
```

*Matcher* n'importe quel nombre :
```
\d+
```

*Matcher* une liste :
```
(word1|word2|word3)
```

Supprimer des lignes sur Notepad++ qui ne contient pas une chaîne de caractères :
^(?:(?!word).)*?$\R*
