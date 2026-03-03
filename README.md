# CP1 – Bug du Lobby

## Pourquoi tous les boutons ont changé ?

La classe `.button` est définie dans `Lobby.css`, un fichier CSS global.
En React, les fichiers CSS ne sont pas scopés : ils s'appliquent à toute l'application.

Modifier `.button` dans `Lobby.css` change donc tous les éléments qui utilisent cette classe, y compris ceux de la Navbar.

## Fix

Utiliser une classe plus spécifique comme `.join-btn` au lieu de `.button` pour éviter les collisions.
