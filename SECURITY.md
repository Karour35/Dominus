# Sécurité et principes de supervision

> Ce document décrit les **principes** de supervision de Dominus.
> Il ne décrit pas l'implémentation.

---

## Principes inviolables

### 1. Lecture seule absolue par défaut

Toute couche d'observation est en lecture seule. Aucun observateur ne peut
modifier les sources qu'il observe. Si une source change, c'est par main
humaine ou par un module explicitement autorisé.

### 2. Notes immuables

Les observations enregistrées sont **append-only**. On n'efface pas, on
ajoute. Toute correction est une nouvelle entrée datée qui remplace, sans
détruire la trace précédente.

### 3. Validation humaine obligatoire

Aucune règle nouvelle ne s'inscrit dans la mémoire officielle sans :

- pattern observé sur **plusieurs jours distincts**
- validation **explicite** de l'humain
- absence de régression détectée

### 4. Pas de capture de raisonnement live

L'observation se fait sur ce qui est **écrit dans les journaux**, jamais
sur ce qui se passe en mémoire pendant la conversation. Pas de hook live,
pas d'instrumentation runtime. Si ça n'a pas été journalisé, ça n'existe
pas pour l'observation.

### 5. Périmètre fermé

L'observateur ne lit que des sources explicitement listées. Il ne scanne
pas le système au hasard. Toute extension de périmètre est une décision
documentée.

### 6. Pas de boucle d'auto-renforcement

Une analyse produite par l'observateur ne peut pas être relue par
l'observateur lui-même au cycle suivant. Les annotations expertes sont
filtrées par auteur.

---

## Refus par défaut sur les actions sensibles

- Suppressions de fichiers système : **bloqué**
- Lecture de fichiers contenant des secrets potentiels : **bloqué**
- Exécution de commandes hors périmètre déclaré : **bloqué**
- Appel d'un outil non enregistré : **bloqué**

Une action sensible ne s'exécute que si elle est **explicitement
autorisée** dans le périmètre. Le doute = blocage.

---

## Anti-fausse confirmation

L'assistant ne dit **jamais** « c'est fait » sans avoir réellement agi.
Si une action n'a pas été exécutée (outil indisponible, confirmation
manquante, droits insuffisants), il le dit explicitement.

C'est l'invariant le plus simple à expliquer et le plus important du
projet : **ne pas mentir sur ce qui a été fait**.

---

## Si vous trouvez une faille

Ce projet est en développement personnel. Il n'a pas vocation à être
déployé en production. Si vous identifiez une faille de raisonnement dans
les principes ci-dessus, vous pouvez ouvrir une issue publique avec un
résumé conceptuel — sans inclure de POC ni de détails d'exploitation.
