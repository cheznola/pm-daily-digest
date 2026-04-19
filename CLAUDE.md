# PM Daily Digest — CLAUDE.md

## Ce projet
Une Routine Claude Code qui lit mes newsletters Gmail chaque matin à 8h, score les contenus selon leur pertinence pour un PM senior en recherche d'emploi dans l'écosystème IA/Produit, et génère un digest lisible directement dans Claude Code.

## Objectif principal
Me rendre plus sharp sur l'IA et le Produit pour que chaque conversation professionnelle soit meilleure. Réduire le bruit et le FOMO. À 8h30, j'ouvre Claude Code, le digest est là, je lis, je ferme.

## Objectif d'apprentissage
Ce projet est un support d'apprentissage Claude Code : Routines, connecteur Gmail natif, structuration de projet, gestion du contexte.

---

## Sources

### Newsletters Gmail (13 sources)

**Tier 1 — Crédibilité IA/Produit directe**
- The Pragmatic Engineer
- First Round Review
- ByteByteGo
- Aakash Gupta
- David Pereira
- Le Ticket ← écosystème French Tech, prioritaire pour le contexte local

**Tier 2 — Insights marché et tendances**
- Jordan Chenevier
- Timothee / How They Grow
- Ben Yoskovitz (Focus)
- Pawel / The Product Compass

**Tier 3 — Signal plus faible**
- Yann Leonardi
- Milan Boisgard (NoCode / IA)
- Valentina Jemuović
- Olivier / Productivist

---

## Système de scoring

Chaque email est scoré sur deux axes :

**Axe 1 — Pertinence thématique (0–3)**
- 3 : IA appliquée au Produit, agents IA, Claude Code, nouvelles pratiques PM, marché French Tech
- 2 : Stratégie produit, growth, marché tech général
- 1 : Généraliste, tips evergreen, contenu sans urgence
- 0 : Hors sujet, promo, événement sans valeur informationnelle

**Axe 2 — Actionnabilité (0–2)**
- 2 : Contient quelque chose à dire, tester ou réutiliser cette semaine
- 1 : Intéressant mais théorique
- 0 : Lecture plaisir, pas d'impact direct

**Score final = Axe1 + Axe2 (max 5)**
- 4–5 → Signal fort, traité en détail dans le digest
- 2–3 → Section "À retenir", résumé court
- 0–1 → Écarté, classé lu automatiquement dans Gmail

---

## Format du digest

**Objectif : 5 minutes de lecture max. Dense, actionnable, sans superflu.**

```
[Date] — PM Daily Digest

🔴 Le signal fort
[Titre en 1 ligne — factuel, pas accrocheur]
[2-3 phrases. Une idée par phrase. Max 20 mots par phrase.
Ton neutre et professionnel. Pas de familiarités.]
Source : [newsletter]

📍 Ce qui se passe en ce moment
[2-3 phrases. Contexte : d'où vient ce signal, pourquoi maintenant,
ce que font les autres acteurs.]

⚡ Ce que tu peux faire en tant que PM
→ En entretien : "[formulation prête à l'emploi, entre guillemets]"
→ À tester : [1 action concrète cette semaine]
→ Impact attendu : [résultat concret si appliqué]

📌 À retenir cette semaine
• [Newsletter] — [1 phrase d'essentiel, actionnable]
• [Newsletter] — [1 phrase d'essentiel, actionnable]
• [Newsletter] — [1 phrase d'essentiel, actionnable]

🔇 Bruit écarté
[1 phrase. Ce qui a circulé mais ne vaut pas l'attention.]

[X] emails traités — [date]
```

**Règles de rédaction strictes :**
- Phrases courtes — maximum 20 mots par phrase
- Ton neutre et professionnel — pas de familiarités, pas d'enthousiasme excessif
- Pas de "il est important de noter que", "c'est massif", "à haut niveau"
- Pas de bullet points dans le signal fort
- Les formulations "En entretien" sont entre guillemets, prêtes à être dites telles quelles
- Pas de HTML — Markdown uniquement

---

## Livraison

- **Format** : Markdown — rendu directement dans la session Routine Claude Code
- **Heure** : 8h00 via Routine planifiée (UTC+2)
- **Consultation** : ouvrir Claude Code à 8h30, la session Routine est visible dans la sidebar
- **Modèle** : Haiku 4.5

---

## Connecteurs requis

- Gmail (natif Anthropic) — lecture des emails non lus + marquage comme lus
- Permissions Gmail : outils d'écriture sur "Toujours autoriser"

---

## Prompt de la Routine

```
Lis les emails non lus dans Gmail de ces expéditeurs :
The Pragmatic Engineer, First Round Review, ByteByteGo, Aakash Gupta,
David Pereira, Le Ticket, Jordan Chenevier, Timothee How They Grow,
Ben Yoskovitz, Pawel Product Compass, Yann Leonardi, Milan Boisgard,
Valentina Jemuovic, Olivier Productivist.

Score chaque email selon le système défini dans CLAUDE.md
(Axe 1 pertinence 0-3 + Axe 2 actionnabilité 0-2).

Génère le digest en Markdown selon le format et les règles
de rédaction définis dans CLAUDE.md.

Classe comme lus tous les emails traités dans Gmail.
```

---

## Architecture

```
pm-daily-digest/
└── CLAUDE.md     ← ce fichier, lu par la Routine à chaque exécution
```

---

## Roadmap

- [x] v0 : session interactive — test du scoring et du format
- [x] v1 : Routine planifiée à 8h → digest Markdown dans Claude Code
- [ ] v2 : affiner le prompt selon les retours des premiers digests
- [ ] v3 : digest hebdo avec liste de tâches à tester

---

## Historique des sessions

### Session 1 — 19 avril 2026
- Premier test en session interactive avec Sonnet 4.6
- 8 emails traités, scoring fonctionnel, format HTML validé
- Routine configurée : runs daily at 8:00 UTC+2
- Repo GitHub : cheznola/pm-daily-digest
- Permissions Gmail écriture : Toujours autoriser ✓
- Consommation contexte session : ~53k / 200k tokens (27%)
- Prochaine étape : valider marquage Gmail + affiner le ton
