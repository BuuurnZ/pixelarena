# CP9 — Observations Résilience

## Étape 1 — Lobby tué (Ctrl+C sur T2)

localhost:3000 : le Shell reste affiché. Seule la section Lobby affiche un fallback ("Chargement...").
Header, Catalog et Cart continuent de fonctionner normalement.

## Étape 2 — Lobby relancé

Le Lobby réapparaît sans redémarrer les autres services. Aucun impact.

## Étape 3 — Catalog tué, puis Cart tué

Même comportement : seule la zone du MFE tué affiche un fallback.
Les autres sections restent fonctionnelles.

## Pourquoi un MFE cassé n'arrête pas les autres ?

Chaque MFE est une app indépendante chargée dynamiquement via `import()` dans un `<Suspense>`.
Si le chargement échoue, React affiche le fallback de ce Suspense uniquement.
Les autres MFEs ont déjà été chargés et tournent dans leur propre scope — ils ne dépendent pas des autres à l'exécution.
C'est le principe de l'isolation : un crash reste local.
