# Panorama des intelligences artificielles (IA)

## Table des matières
1. Introduction rapide  
2. Méthodologie et limites  
3. Grandes familles d'IA  
   - 3.1 Modèles de langage / Foundation models (LLMs)  
   - 3.2 Agents conversationnels et assistants  
   - 3.3 Génération d'images et multimédia (diffusion, GANs, etc.)  
   - 3.4 Vision par ordinateur et modèles de segmentation  
   - 3.5 Reconnaissance et synthèse vocale (ASR / TTS)  
   - 3.6 Représentations vectorielles & recherche sémantique (embeddings)  
   - 3.7 Recommandation et personnalisation  
   - 3.8 Robotic Process Automation (RPA) et agents d'automatisation  
   - 3.9 AutoML et plateformes MLOps  
   - 3.10 IA embarquée (Edge AI / TinyML)  
   - 3.11 IA pour la robotique et contrôle (RL et planification)  
   - 3.12 Modèles spécialisés (santé, juridique, finance)  
4. Critères de choix selon l’usage  
5. Risques, bonnes pratiques et points juridiques à prévoir  
6. Roadmap d’adoption  
7. Annexes : fournisseurs & projets open-source  
8. Glossaire court  

---

## 1. Introduction rapide
Ce document vise à donner une vue claire et actionnable des catégories d'IA les plus utiles aujourd'hui, avec pour chaque catégorie :
- Une **description concise**  
- Des **exemples représentatifs**  
- Des **usages concrets** (quel intérêt)  
- Les **contraintes techniques ou organisationnelles** à anticiper  

👉 Objectif : permettre d’identifier rapidement quelle IA utiliser selon un besoin donné (ex. automatiser la saisie, améliorer la recherche documentaire, générer des visuels marketing, transcrire des réunions, etc.).

---

## 2. Méthodologie et limites
- **Méthode** : classification par finalité technique et par type d'outputs (texte, image, son, actions).  
- **Limites** :  
  - Multiples variantes open-source  
  - Marché en constante évolution (nouvelles versions, mises à jour fréquentes)  
  - Ce document est une **synthèse représentative** et non une base exhaustive.  

---

## 3. Grandes familles d'IA

### 3.1 Modèles de langage / Foundation models (LLMs)
**Quoi :** grands modèles pré-entraînés sur du texte (souvent multimodaux) capables de génération, compréhension, traduction, résumé, etc.  
**Exemples :** GPT (OpenAI), Claude (Anthropic), LLaMA (Meta), Mistral, Cohere.  
**Usages :**
- Rédaction & synthèse (e-mails, rapports, résumés)  
- Support client (chatbots 24/7)  
- Génération de code & debugging  
- Extraction d’information  
- RAG (recherche augmentée)  
**Contraintes :** coûts d’infra/API, hallucinations, régulations sectorielles.  

---

### 3.2 Agents conversationnels et assistants
**Quoi :** couche logicielle orchestrant un LLM + outils (API, calendriers, bases de données).  
**Usages :**
- Assistant personnel (planification, résumés)  
- Automatisation décisionnelle  
- Front-office & self-service  
**Contraintes :** sécurité des accès, gestion des permissions, traçabilité.  

---

### 3.3 Génération d’images et multimédia (diffusion, GANs, etc.)
**Quoi :** modèles génératifs (texte → image, image → image, inpainting, vidéo).  
**Exemples :** Stable Diffusion, DALL·E, Midjourney.  
**Usages :**
- Marketing & création (illustrations, assets)  
- Design produit  
- Contenu personnalisé  
**Contraintes :** droits d’auteur, qualité fine-tuning, contrôle du style.  

---

### 3.4 Vision par ordinateur et modèles de segmentation
**Quoi :** détection, classification, segmentation, suivi vidéo.  
**Usages :**
- Contrôle qualité industriel  
- Imagerie médicale  
- Analyse vidéo (sécurité, comptage)  
**Contraintes :** annotations lourdes, biais dataset, régulations strictes.  

---

### 3.5 Reconnaissance & synthèse vocale (ASR / TTS)
**Quoi :** audio → texte (ASR) ou texte → voix (TTS).  
**Exemples :** Whisper (OpenAI), Google Speech-to-Text, Amazon Polly.  
**Usages :**
- Transcription de réunions  
- Assistants vocaux  
- Accessibilité  
**Contraintes :** précision selon langue/accents, confidentialité audio.  

---

### 3.6 Représentations vectorielles & recherche sémantique (embeddings)
**Quoi :** transformer documents/requêtes en vecteurs pour la recherche par similarité.  
**Usages :**
- Recherche documentaire avancée  
- RAG pour LLMs  
- Clustering / déduplication  
**Contraintes :** coûts de stockage, mise à jour des embeddings, sécurité.  

---

### 3.7 Recommandation & personnalisation
**Quoi :** systèmes prédictifs pour proposer produits/contenus.  
**Usages :**
- E-commerce  
- Médias / plateformes de contenu  
**Contraintes :** vie privée, bulles de filtres, métriques complexes.  

---

### 3.8 Robotic Process Automation (RPA) & agents d’automatisation
**Quoi :** robots logiciels automatisant tâches répétitives sur interfaces existantes.  
**Usages :**
- Comptabilité (saisie, rapprochement)  
- RH & back-office  
**Contraintes :** fragilité face aux changements d’interface, orchestration nécessaire.  

---

### 3.9 AutoML & plateformes MLOps
**Quoi :** automatisation de l’entraînement, tuning, déploiement, monitoring des modèles.  
**Usages :**
- Prototypage rapide (accessible aux non-experts)  
- Industrialisation (CI/CD, monitoring dérive)  
**Contraintes :** manque de transparence, besoin de gouvernance claire.  

---

### 3.10 IA embarquée (Edge AI / TinyML)
**Quoi :** modèles optimisés pour appareils contraints (IoT, smartphones).  
**Usages :**
- Inference locale (confidentialité, faible latence)  
- Maintenance prédictive  
**Contraintes :** ressources limitées, mises à jour complexes.  

---

### 3.11 IA pour la robotique et contrôle (RL, planification)
**Quoi :** algorithmes pour planification et apprentissage par renforcement.  
**Usages :**
- Robots industriels  
- Drones, véhicules autonomes  
**Contraintes :** sécurité physique, validation lourde, simulations coûteuses.  

---

### 3.12 Modèles spécialisés (santé, juridique, finance)
**Quoi :** IA adaptées à des domaines réglementés.  
**Usages :**
- Santé (aide au diagnostic)  
- Juridique (analyse de contrats)  
- Finance (scoring, fraude)  
**Contraintes :** conformité réglementaire, audits, explicabilité.  

---

## 4. Critères de choix selon l’usage
Checklist rapide :  
- Données (volume, sensibilité, annotations)  
- Latence (temps réel vs batch)  
- Coût (infra, API)  
- Contrôle (cloud vs on-premise)  
- Explainability (réglementaire)  
- Maintenance (updates, monitoring dérive)  

---

## 5. Risques, bonnes pratiques et aspects juridiques
- **Hallucinations** : vérification humaine indispensable  
- **Biais** : audit régulier des datasets et outputs  
- **Droits d’auteur** : attention aux contenus protégés  
- **Sécurité & confidentialité** : chiffrement, anonymisation, contrats fournisseurs  
- **Traçabilité** : logs, data lineage, gouvernance claire  

---

## 6. Roadmap d’adoption
- **Pilote (1–2 mois)** : POC simple (transcription, recherche sémantique, RPA)  
- **Industrialisation (3–9 mois)** : CI/CD, monitoring, SLOs  
- **Gouvernance (continu)** : comité de risques IA, registre des modèles, revue éthique  

---

## 7. Annexes — fournisseurs & projets représentatifs
- **LLMs** : OpenAI (GPT), Anthropic (Claude), Google (PaLM), Meta (LLaMA), Mistral, Cohere  
- **Images & multimédia** : Stability AI (Stable Diffusion), OpenAI (DALL·E), Midjourney  
- **Vision** : Meta (SAM), NVIDIA, OpenCV, Detectron  
- **Speech** : OpenAI Whisper, Google Speech-to-Text, Amazon Transcribe  
- **RPA** : UiPath, Automation Anywhere, Blue Prism  
- **AutoML / MLOps** : Google Vertex AI, H2O.ai, DataRobot  
- **Open-source & infra** : Hugging Face, TensorFlow, PyTorch, ONNX  

---

## 8. Glossaire court
- **LLM** : Large Language Model  
- **ASR** : Automatic Speech Recognition  
- **TTS** : Text-To-Speech  
- **RAG** : Retrieval-Augmented Generation  
- **RPA** : Robotic Process Automation  
