# Roadmap

> Document append-only. Toute modification = nouvelle entrée datée.

---

## Invariant inviolable

**Aucune phase n'est activée sans validation explicite et tracée.**

Pas d'auto-promotion. Pas de bascule silencieuse. Toute transition est une
décision écrite et signée.

---

## Phases livrées (résumé)

| Phase | Description | Statut |
|---|---|---|
| Fondations | Pipeline de base, supervision déterministe initiale | Livrée |
| Stabilisation | Tests, gestion des erreurs, durcissement | Livrée |
| Mémoire | Couches mémoire, traçabilité | Livrée |
| Voix | Synthèse vocale | Livrée |
| Modules métier | Extensions fonctionnelles | Livrée |
| Documentation | Documentation interne | Livrée |

---

## Phase active — Avis avant action

**Statut : active.**

Avant chaque modification, l'assistant émet un verdict :
**sûr / prudence / à éviter**. Le verdict est informatif, **non bloquant**.
Il enrichit la décision de l'humain sans la remplacer.

---

## Phase en test — Observation

**Statut : en test sur quelques nuits.**

Un observateur lit en seule lecture les journaux et produit un rapport
quotidien. Il ne modifie rien, ne propose rien à exécuter. Il s'arrête
automatiquement après une période définie pour attendre validation.

---

## Phases en attente

| Phase | Description | Conditions d'activation |
|---|---|---|
| Propositions | L'assistant propose des actions à partir de l'observation | Plusieurs jours d'usage réel + revue manuelle |
| Mémoire de règles | Pattern observé ≥3 fois sur jours distincts → règle stable | Phase Propositions livrée |
| Replay | Rejouer une session pour analyse | À la demande |
| Reasoning | Expliquer les décisions en langage naturel | Mémoire de règles stable |

Aucune date n'est promise.

---

## Pourquoi cette discipline

Un assistant qui s'auto-modifie sans contrôle n'est plus supervisé. La
roadmap entière est conçue pour empêcher cette dérive : chaque évolution
est observée, datée, validée, et réversible.
