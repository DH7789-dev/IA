# Principe universel (formule P.R.O.M.P.T.)

Pense toujours en **P.R.O.M.P.T.** — chaque lettre correspond à un élément obligatoire :

* **P**ersona — qui doit être l’agent (ex : « Tu es un ingénieur prompts senior »).
* **R**ésultat attendu — format précis et critère d’acceptation (ex : JSON, 3 options, sujet + email).
* **O**rigin / Contexte — données, historique ou contraintes métier utiles.
* **M**éthode / Contraintes — style, longueur, ton, étapes, outils interdits, « temperature » si API.
* **P**reuves / Exemples — 1–3 exemples (input → output) pour enseigner le format.
* **T**ests & Critères — comment vérifier si le résultat est bon (rubrique d’évaluation).

# Checklist rapide (avant d’exécuter)

1. Objectif clair en 1 phrase.
2. Format de sortie strict (ex : JSON avec clés).
3. Contraintes mesurables (longueur, mots-clés interdits).
4. 1 exemple d’entrée -> sortie.
5. Demande de vérification / correction si incertain.

# Templates prêts à l’emploi

### Template simple (résumé / réponse courte)

```
Tu es un assistant expert en [domaine]. 
Objectif : [ce que tu veux]. 
Contrainte : [longueur, ton, éléments à inclure ou exclure]. 
Sortie : [format exact — ex : 3 points numérotés, 50–80 mots]. 
Contexte : [données brutes / résumé]. 
Si incertain, demande 1 question de clarification.
```

### Template pour sortie structurée (API / automatisation)

```
SYSTEM: Tu es un assistant qui respecte strictement le format JSON demandé.
TASK: [décris la tâche]
INPUT: [données ici]
OUTPUT_SCHEMA:
{
  "title": "string",
  "summary": "string (<= 200 chars)",
  "priority": "low|medium|high"
}
CONSTRAINTS: ne pas inclure de texte hors du JSON; utiliser la clé `notes` seulement si nécessaire.
EXAMPLES:
#1 INPUT: ... -> OUTPUT: {...}
EVALUATION: le résumé doit contenir le mot-clé X; priorité basée sur Y.
```

### Template pour génération de code

```
Tu es un développeur senior Python.
Tâche: écrire une fonction `def calculate(...):` qui fait X.
Contraintes:
- Python 3.11 compatible
- Tests unitaires pytest inclus
- Complexité O(n)
Sortie: {code}, puis un bref commentaire expliquant la logique (max 3 phrases).
```

# Exemples concrets — Mauvais vs Parfait

### Exemple A — résumé d’article

Mauvais :
`Résume ce texte.`

Parfait :

```
Tu es un rédacteur professionnel. Résume le texte ci-dessous en 4 phrases maximum, en conservant les chiffres et les noms propres. Ne change pas le sens. Style : neutre, clair. 
Sortie : 4 phrases séparées par des sauts de ligne.
Texte: [insère texte]
```

### Exemple B — email professionnel

Mauvais :
`Écris un email pour convaincre un client.`

Parfait :

```
Tu es un responsable commercial bilingue (FR/EN). Rédige un email en français pour proposer une démo produit à un prospect qui a exprimé un intérêt. Inclure :
- Objet (<= 60 chars)
- 3 paragraphes : 1) rappel contexte, 2) proposition de valeur + bénéfices, 3) CTA clair (3 plages horaires proposées).
Ton : professionnel, chaleureux. Longueur totale : 160–220 mots.
```

# Astuces avancées (améliorent nettement la qualité)

* **Donne des exemples concrets (few-shot)** : montre 1–3 paires entrée→sortie; le modèle va imiter le format.
* **Demande un OUTPUT_SCHEMA (JSON)** si tu veux automatiser le parsing.
* **Décompose la tâche** : “Étape 1: propose 3 approches; Étape 2: choisis la meilleure et détaille plan en 5 étapes.”
* **Utilise les messages système** (si possible) : définis rôle et règles globales.
* **Pour des réponses déterministes** : en API, règle `temperature=0`; dans chat, demande “réponse factuelle, concise, pas d’inventions”.
* **Pour créativité** : augmente la diversité (`temperature>0.7`) et demande plusieurs variantes.
* **Auto-vérification** : demande ensuite “Vérifie que la sortie respecte le format X et corrige les erreurs” — le modèle corrigera souvent ses propres erreurs.
* **Limiter les hallucinations** : demande “cite les sources” ou “répond seulement si tu es sûr à 90%” (pas parfait mais utile).

# Pièges fréquents à éviter

* Trop vague : pas d’objectif précis.
* Pas de format demandé → réponses inconsistantes.
* Trop de tâches mêlées dans un seul prompt.
* Oublier d’indiquer la contrainte de longueur/style.
* Ne pas fournir d’exemples quand le format est complexe.

# Stratégie d’itération (amélioration rapide)

1. Écris prompt initial selon P.R.O.M.P.T.
2. Lance et collecte la sortie.
3. Mesure selon critères (exactitude, format, ton).
4. Ajoute exemples ou renforce contraintes sur les erreurs observées.
5. Répète jusqu’à satisfaction.

# Exemples d’« ingénierie » avancée

* **Demander au modèle d’expliquer sa méthode** : “Donne un résumé et ensuite explique en 3 points comment tu as trouvé ces éléments.”
* **Demander plusieurs sorties** : “Donne 3 variations (ton formel, casual, persuasive).”
* **Prompt de debug** : “Trouve les 5 erreurs potentielles dans le code ci-dessous et propose des corrections + test unitaire minimal.”
* **Prompt « chef d’orchestre »** (pour tâches complexes) : “Simule 3 spécialistes (designer, dev, market) — chaque section doit commencer par [Designer]: … etc.”

# Exemples rapides (prêts à copier)

**Générer un pitch de 30s (startups)**

```
Tu es un startup founder expérimenté. Rédige un pitch pitch-deck verbal de 30 secondes pour [produit] destiné à [audience]. 
Contraintes : 50–65 mots, inclure problème, solution, marché, demande d’action (call to action).
```

**Traduction fidèle + style**

```
Tu es traducteur professionnel FR→EN. Traduis le texte suivant en anglais en conservant le ton informel, les idiomes et la longueur approximative. Indique également 2 alternatives plus formelles. 
Texte: [...]
```

# Rubrique d’évaluation (exemple simple)

Pour juger si un prompt est « parfait », mesure :

* **Conformité au format** (0–5)
* **Précision / exactitude** (0–5)
* **Tonalité / style respectés** (0–5)
* **Concision / longueur respectée** (0–5)
  Score total ≥18 = très bon.

