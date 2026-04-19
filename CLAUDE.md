# PM Daily Digest — CLAUDE.md

## Ce projet
Une Routine Claude Code qui lit mes newsletters Gmail chaque matin à 8h, score les contenus selon leur pertinence pour un PM senior en recherche d'emploi dans l'écosystème IA/Produit, et génère un digest HTML lisible directement dans l'interface Claude Code.

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

Générer en HTML avec ce format exact :

```html
<h1>[Date] — PM Daily Digest</h1>

<h2>🔴 Le signal fort</h2>
<p><strong>[Titre accrocheur en 1 ligne]</strong></p>
<p>[2-3 phrases. Une idée par phrase. Pas de jargon.
   Chaque phrase doit tenir seule.]</p>
<p><em>Source : [newsletter]</em></p>
<hr>

<h2>📍 Ce qui se passe en ce moment</h2>
<p>[2-3 phrases de contexte. Pourquoi maintenant.
   Ce que les autres font.]</p>
<hr>

<h2>⚡ Ce que tu peux faire en tant que PM</h2>
<ul>
  <li><strong>En entretien :</strong> [formulation prête à l'emploi, entre guillemets]</li>
  <li><strong>À tester :</strong> [1 action concrète cette semaine]</li>
  <li><strong>Impact attendu :</strong> [résultat si tu appliques ça]</li>
</ul>
<hr>

<h2>📌 À retenir cette semaine</h2>
<ul>
  <li><strong>[Newsletter]</strong> — [1 phrase d'essentiel, actionnable]</li>
</ul>
<hr>

<h2>🔇 Bruit écarté</h2>
<p>[1 phrase. Ce qui a circulé mais ne vaut pas ton attention.]</p>

<p><small>[X] emails traités — [date]</small></p>
```

**Règles de rédaction :**
- Phrases courtes — maximum 20 mots par phrase
- Pas de "il est important de noter que"
- Pas de bullet points dans le signal fort
- Les formulations "En entretien" doivent être entre guillemets, prêtes à être dites telles quelles

---

## Livraison

- **Format** : HTML rendu directement dans la session Routine Claude Code
- **Heure** : 8h00 via Routine planifiée
- **Consultation** : ouvrir Claude Code à 8h30, la session Routine est visible dans la sidebar
- **Modèle** : Haiku 4.5

---

## Connecteurs requis

- Gmail (natif Anthropic) — lecture des emails non lus + marquage comme lus

---

## Prompt de la Routine

```
Lis les emails non lus dans Gmail de ces expéditeurs :
The Pragmatic Engineer, First Round Review, ByteByteGo, Aakash Gupta,
David Pereira, Le Ticket, Jordan Chenevier, Timothee How They Grow,
Ben Yoskovitz, Pawel Product Compass, Yann Leonardi, Milan Boisgard,
Valentina Jemuovic, Olivier Productivist.

Score chaque email (Axe 1 pertinence 0-3 + Axe 2 actionnabilité 0-2)
selon les règles définies dans CLAUDE.md.

Génère le digest en HTML selon le format exact défini dans CLAUDE.md.

Classe comme lus tous les emails traités dans Gmail.
```

---

## Architecture

```
pm-daily-digest/
└── CLAUDE.md     ← ce fichier, lu par la Routine à chaque exécution
```

Pas de script Python. Pas de cron local. La Routine tourne sur l'infrastructure Anthropic.

---

## Roadmap

- [x] v0 : session interactive — test du scoring et du format
- [ ] v1 : Routine planifiée à 8h → digest HTML dans Claude Code
- [ ] v2 : affiner le prompt selon les retours des premiers digests
- [ ] v3 : digest hebdo avec liste de tâches à tester

---

## Historique des sessions

### Session 1 — 19 avril 2026
- Premier test en session interactive avec Sonnet 4.6
- 8 emails traités, scoring fonctionnel
- Format HTML validé
- Consommation contexte session : ~53k / 200k tokens (27%)
- Prochaine étape : créer la Routine + repo GitHub
