# Architecture — Vue d'ensemble

> Document conceptuel. Aucun détail d'implémentation, aucun chemin de
> fichier, aucun nom de module. Cette page expose la **vision**, pas le
> moteur.

---

## Principe directeur

**Une IA personnelle agit seulement avec consentement.**

Tout le reste découle de là.

---

## Trois couches

### Couche 1 — Compréhension

Dominus reçoit une requête. Il essaie d'abord de la comprendre via des
règles déterministes (rapide, prédictible). Si la requête échappe à ces
règles, il délègue au modèle local — l'apprenti.

### Couche 2 — Supervision

Avant toute action sensible, une chaîne de validation décide :
**autorisé / clarifier / bloqué**. Aucune action ne franchit cette barrière
sans un verdict explicite. Les actions destructives sont rejetées par
défaut.

### Couche 3 — Mémoire

Tout ce qui est décidé, refusé ou exécuté est journalisé. La mémoire ne
sert pas à apprendre en autonomie : elle sert à **être interrogeable**,
**comparable dans le temps**, et **vérifiable par l'humain**.

---

## Qui décide quoi

| Niveau | Rôle |
|---|---|
| **L'humain** | Décide les règles, valide les évolutions |
| **Dominus (système supervisé)** | Encadre l'exécution, accepte ou refuse les actions |
| **Le modèle de langage** | Propose, rédige, suggère — sans décider seul |

Aucune action sensible ne s'exécute sans passer par les trois niveaux.
Le modèle ne peut rien lancer directement : il passe par Dominus, qui
contrôle, journalise et ne ferme jamais une boucle de décision sans la
validation prévue par les règles que l'humain a fixées.

---

## Pair-à-pair entre instances

Plusieurs Dominus peuvent coexister sur des machines différentes,
appartenant chacun à un utilisateur unique. Ces instances peuvent
**s'échanger des évolutions validées** sans serveur central. Chaque
instance reste **souveraine** : sa mémoire est privée, son utilisateur est
seul à pouvoir lui imposer des règles.

C'est un modèle de réseau de confiance, pas un service mutualisé.

---

## Ce qui n'apparaît PAS dans ce document

- Le langage et la stack technique
- Les noms de modules
- Les chemins de fichiers
- Les protocoles précis
- Les algorithmes de validation
- Les schémas internes

Ces éléments sont **volontairement omis**. Cette page sert à exposer la
**vision**, pas à permettre la reproduction.
