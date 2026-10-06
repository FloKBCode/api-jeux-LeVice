# 1. Fusionner les pull requests avec « Squash and merge »

- **Date** : 2026-10-06
- **Statut** : Proposée

## Contexte

Le projet est repris par une petite équipe. Chaque changement arrive sur `main` par une pull request relue (voir la PR des statistiques, #6). GitHub propose trois façons de fusionner une PR ; il faut en choisir une et s'y tenir, pour que l'historique de `main` reste lisible et que `main` fonctionne toujours.

## Options envisagées

1. **Merge commit.** Pour : conserve tout l'historique des commits et ajoute un commit de fusion. Contre : les commits de travail (`wip`, `fix typo`) arrivent sur `main` et le rendent illisible.
2. **Squash and merge.** Pour : un seul commit par PR sur `main`, historique propre, et le titre de la PR devient le message du commit. Contre : le détail des commits intermédiaires d'une branche disparaît.
3. **Rebase and merge.** Pour : historique linéaire, sans commit de fusion. Contre : exige des commits déjà propres sur la branche, plus difficile à tenir pour l'équipe.

## Décision

Nous fusionnons les pull requests avec **Squash and merge**. Un commit sur `main` correspond donc à une PR relue, et son message est le titre de la PR.

## Conséquences

- L'historique de `main` est lisible : une ligne par fonctionnalité ou correction, facile à parcourir et à revenir en arrière si besoin.
- Le détail des commits intermédiaires d'une branche est perdu après la fusion : il faut donc soigner le titre de la PR, qui devient le message du commit sur `main`.
- À revoir si l'équipe grandit et a besoin de retrouver le détail des commits après fusion : on envisagerait alors « Rebase and merge » avec des commits propres.
