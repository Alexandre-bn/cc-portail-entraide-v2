# EXPLICATIONS – CC Git portail d'entraide

**BONO Alexandre**

## Départ

Commit initial : `4a266e1`. Main était sur `76184a8` au départ. La branche fournie `feature/tutorat` (`a43f314`) part aussi de `76184a8`.
J'ai configuré mon nom et mon adresse GitHub noreply avec `git config` avant de commencer.

Test avant modification : la page affichait 200 minutes par créneau, 2 créneaux et 400 minutes après deux clics, puis 0 après Recommencer.

## Mes branches

J'ai créé `feature/accueil` et `feature/contact` depuis `76184a8`, avant toute fusion.

- `3d7ee06` (accueil) : la permanence annonce un accueil libre sans inscription le jeudi à 16 h.
- `1018c37` (contact) : l'adresse entraide@example.org est devenue un lien mailto.

Dans main : la fusion d'accueil s'est faite en fast-forward, puis celle de contact a créé le commit `42d35a8` (pas de conflit, ce ne sont pas les mêmes lignes).

## Conflit avec feature/tutorat

Le conflit vient du fait que mon accueil et le tutorat partent du même commit et modifient la même ligne `<p id="permanence">`.
J'ai gardé les deux informations sur deux lignes séparées : l'accueil libre à 16 h et le tutorat sur inscription à 16 h 30. Le lien de contact est toujours là.
J'ai vérifié qu'il ne restait aucun marqueur, puis j'ai commité la fusion : `ee66aed`. Ses deux parents sont `42d35a8` et `a43f314`.

## Annulation de la durée

Le commit `b88cc98` avait passé la durée de 20 à 200 minutes. Le commit `76184a8`, arrivé après, a ajouté le conseil du README, que je devais garder.
J'ai créé `hotfix/duree` depuis `ee66aed` et fait `git revert b88cc98`, ce qui donne le commit `89b01b3`. Il remet 20 sans effacer l'historique. Puis j'ai fusionné dans main (fast-forward).

## Tests après

20 minutes par créneau, 2 créneaux et 40 minutes après deux clics, 0 après Recommencer. L'accueil, le tutorat, le lien et le conseil du README sont bien présents.

## Publication

Dépôt : https://github.com/Alexandre-bn/cc-portail-entraide-v2
Après publication, `git rev-parse main` et `git ls-remote origin` donnent le même identifiant pour main, et la page GitHub affiche le même commit. Les quatre branches de tâche sont aussi en ligne.
Ce fichier est le dernier commit de main : je donne son identifiant dans mon message de remise.

## Difficultés

Vim s'est ouvert pendant la fusion de contact : j'ai tapé `:wq` puis Entrée, et la fusion `42d35a8` s'est enregistrée. Je n'ai pas eu d'autre difficulté que le conflit prévu.

## Aides utilisées

J’ai réalisé seul les manipulations Git et les tests, et j’ai rédigé ce fichier moi-même.
Claude Code : j’ai demandé « corrige l’orthographe et rends mes phrases plus claires, sans changer le contenu ». Il a corrigé les fautes et reformulé 2 ou 3 phrases. J’ai gardé ses corrections après avoir vérifié que les hash et les informations n’avaient pas changé.
Commit concerné : celui d’EXPLICATIONS.md.
Ressources : cours S2 et documentation git-scm.com.
