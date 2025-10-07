# 📝 Prompts pour Développeurs

## 🟢 PROMPT SIMPLE - Pour LLaMA 3.2 (IA locale)

### Tâche : Créer une fonction Python de validation d'email

```
Tu es un développeur Python senior.

Objectif : Écris une fonction Python qui valide une adresse email.

Contraintes :
- Nom de fonction : validate_email()
- Paramètre : email (string)
- Retour : True/False
- Utilise regex
- Ajoute 3-4 lignes de commentaires
- Code compatible Python 3.10+

Sortie : Code Python uniquement, sans explication longue.

Exemple d'utilisation attendue :
validate_email("user@example.com") → True
validate_email("invalid.email") → False
```

---

## 🔵 PROMPT COMPLEXE - Pour Claude Code

### 📋 Spécifications complètes

**PERSONA**
Tu es un développeur full-stack senior spécialisé en React et design moderne.

**RÉSULTAT ATTENDU**
Crée une page web portfolio complète avec :
- Format : Application React (single page)
- Structure : Header + Hero + Projets + Compétences + Contact + Footer
- Fichiers : index.html avec React inline + CSS moderne
- Responsive : mobile-first, breakpoints à 768px et 1024px

**CONTEXTE & CONTRAINTES TECHNIQUES**

Structure HTML/React :
- Utiliser React avec hooks (useState, useEffect)
- Pas de dépendances externes (tout en un seul fichier)
- Header fixe avec navigation smooth scroll
- Section Hero avec animation au chargement
- Galerie de 6 projets avec modal au clic
- Section compétences avec barres de progression animées
- Formulaire de contact avec validation
- Footer avec liens réseaux sociaux

Design & Style :
- Palette : gradient moderne (#667eea → #764ba2)
- Typographie : Segoe UI ou fallback system fonts
- Animations : transitions fluides (0.3s ease)
- Dark mode par défaut avec possibilité de toggle
- Espacement harmonieux (multiples de 8px)
- Cards avec effet hover (elevation + scale)

Fonctionnalités JavaScript :
- Navigation smooth scroll avec highlight de section active
- Modal pour affichage détaillé des projets
- Validation de formulaire en temps réel
- Toggle dark/light mode persistant (localStorage)
- Animations on scroll (intersection observer)
- Menu burger responsive pour mobile

**MÉTHODE**

Étape 1 : Structure HTML avec sections sémantiques
Étape 2 : Composants React (Header, Hero, ProjectCard, SkillBar, ContactForm, Footer)
Étape 3 : CSS avec variables pour thème et responsive
Étape 4 : Logique JavaScript pour interactions
Étape 5 : Tests de responsivité et performance

**EXEMPLES DE STRUCTURE**

Exemple de ProjectCard :
```javascript
const ProjectCard = ({ title, description, image, tech }) => {
  const [isOpen, setIsOpen] = useState(false);
  
  return (
    <div className="project-card" onClick={() => setIsOpen(true)}>
      <img src={image} alt={title} />
      <h3>{title}</h3>
      <p>{description}</p>
      <div className="tech-stack">
        {tech.map(t => <span key={t}>{t}</span>)}
      </div>
    </div>
  );
};
```

Exemple de données projet :
```javascript
const projects = [
  {
    id: 1,
    title: "Application E-commerce",
    description: "Plateforme de vente en ligne avec panier et paiement",
    image: "https://via.placeholder.com/400x300",
    tech: ["React", "Node.js", "MongoDB"],
    fullDescription: "Description détaillée du projet..."
  },
  // 5 autres projets...
];
```

**CRITÈRES DE VALIDATION**

Le code est accepté si :
- ✅ Tout le code tient dans UN SEUL fichier HTML
- ✅ La page est responsive (testé mobile, tablette, desktop)
- ✅ Les animations fonctionnent sans lag
- ✅ Le formulaire valide : email format, champs requis, longueur min
- ✅ Le dark mode fonctionne et persiste au refresh
- ✅ Le smooth scroll fonctionne sur tous les liens
- ✅ Pas d'erreurs console
- ✅ Code indenté et commenté aux sections clés
- ✅ Performance : page charge en < 2s

**CONTRAINTES SUPPLÉMENTAIRES**
- N'utilise PAS de CDN externe pour React (code inline ou utilise un seul CDN)
- Optimise les images (placeholder ou suggestions d'URLs)
- Ajoute des commentaires pour chaque section majeure
- Inclus un README en commentaire en haut du fichier

**OUTPUT FINAL ATTENDU**
Un fichier HTML complet, prêt à être ouvert dans un navigateur, avec :
1. Le code source complet et fonctionnel
2. Des commentaires expliquant les sections principales
3. Des suggestions d'amélioration en fin de fichier (en commentaire)

Si un élément n'est pas clair, pose 1-2 questions de clarification avant de commencer.
```

---

## 📊 Comparaison des deux approches

| Critère | Prompt Simple (LLaMA) | Prompt Complexe (Claude Code) |
|---------|----------------------|-------------------------------|
| **Longueur** | ~100 mots | ~600 mots |
| **Détails** | Basiques | Exhaustifs |
| **Exemples** | 2 lignes | Plusieurs blocs de code |
| **Contraintes** | 5-6 points | 20+ points techniques |
| **Validation** | Implicite | Checklist de 8 critères |
| **Usage** | Tâche simple, rapide | Projet complet, production |

---

## 💡 Conseils d'utilisation

### Pour LLaMA 3.2 (local) :
- Privilégiez les prompts courts et directs
- Une seule tâche à la fois
- Évitez trop de contexte (capacité limitée)
- Testez et itérez rapidement

### Pour Claude Code :
- Investissez du temps dans le prompt initial
- Incluez TOUS les détails techniques
- Fournissez des exemples de structure
- Définissez clairement les critères de succès
- Exploitez la capacité à gérer la complexité

---



