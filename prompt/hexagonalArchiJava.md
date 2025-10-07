# 🏗️ Checklist Architecture Hexagonale - Étapes de Validation Pré-Codage

## 📋 Phase 1 : Analyse et Compréhension du Contexte

### ✅ 1.1 Identification du Domaine Métier
- [ ] **Clarifier le domaine d'activité** : Quel est le métier principal ?
- [ ] **Identifier les entités métier principales** : Quels sont les objets centraux ?
- [ ] **Définir les règles de gestion** : Quelles sont les contraintes business ?
- [ ] **Mapper les cas d'usage** : Que doit faire l'application ?

### ✅ 1.2 Analyse des Besoins d'Intégration
- [ ] **Identifier les acteurs externes** : Qui utilise l'application ?
- [ ] **Répertorier les services externes** : BDD, APIs, systèmes de fichiers ?
- [ ] **Définir les interfaces d'entrée** : REST, GraphQL, CLI ?
- [ ] **Spécifier les interfaces de sortie** : Persistance, notifications, etc.

## 📐 Phase 2 : Conception Architecturale

### ✅ 2.1 Structure des Modules Maven
- [ ] **Valider la structure 4 modules** :
  - `domain` (cœur hexagonal)
  - `application` (couche application)
  - `infrastructure` (couche infrastructure)
  - `ms-launcher` (module de lancement)

### ✅ 2.2 Définition des Ports
- [ ] **Identifier les Ports API (interfaces exposées par le domaine)** :
  - Services métier que le domaine expose
  - Interfaces appelées par les adaptateurs d'entrée
- [ ] **Identifier les Ports SPI (interfaces requises par le domaine)** :
  - Repositories pour la persistance
  - Services externes (notifications, intégrations)
  - Interfaces que le domaine définit mais n'implémente pas

### ✅ 2.3 Conception des Adaptateurs
- [ ] **Adaptateurs d'Entrée (Driving)** :
  - Contrôleurs REST
  - Interfaces utilisateur
  - Tests automatisés
- [ ] **Adaptateurs de Sortie (Driven)** :
  - Implémentations des repositories
  - Clients pour services externes
  - Systèmes de fichiers/messaging

## 🏛️ Phase 3 : Architecture en Couches

### ✅ 3.1 Module Domain (Cœur)
- [ ] **Vérifier l'isolation complète** : Aucune dépendance externe
- [ ] **Structure du package** :
  ```
  com.{project}.domain/
  ├── model/          # Entités métier
  ├── service/        # Services du domaine  
  ├── port/
  │   ├── in/        # Ports d'entrée (API)
  │   └── out/       # Ports de sortie (SPI)
  └── exception/     # Exceptions métier
  ```

### ✅ 3.2 Module Application
- [ ] **Responsabilités claires** : Exposition des services
- [ ] **Structure du package** :
  ```
  com.{project}.application/
  ├── controller/    # Contrôleurs REST
  ├── dto/          # Data Transfer Objects
  ├── mapper/       # Mappers DTO ↔ Domain
  └── config/       # Configuration Spring
  ```

### ✅ 3.3 Module Infrastructure
- [ ] **Implémentation des SPI** : Tous les ports de sortie
- [ ] **Structure du package** :
  ```
  com.{project}.infrastructure/
  ├── adapter/
  │   ├── in/       # Adaptateurs d'entrée (si applicable)
  │   └── out/      # Adaptateurs de sortie
  ├── repository/   # Implémentations JPA
  ├── entity/       # Entités JPA
  └── mapper/       # Mappers JPA ↔ Domain
  ```

### ✅ 3.4 Module MS-Launcher
- [ ] **Point d'entrée unique** : Classe `@SpringBootApplication`
- [ ] **Assemblage des dépendances** : Configuration complète
- [ ] **Dépendances vers tous les modules**

## 🔧 Phase 4 : Validation Technique

### ✅ 4.1 Gestion des Dépendances
- [ ] **Module domain** : Aucune dépendance externe (sauf tests)
- [ ] **Module application** : Dépend uniquement de `domain`
- [ ] **Module infrastructure** : Dépend uniquement de `domain`
- [ ] **Module ms-launcher** : Dépend de tous les autres modules

### ✅ 4.2 Respect des Patterns
- [ ] **Domain-Driven Design** : Entités, Value Objects, Aggregates
- [ ] **SOLID Principles** : SRP, DIP, ISP appliqués
- [ ] **Repository Pattern** : Abstraction de la persistance
- [ ] **Clean Architecture** : Règle de dépendance respectée

### ✅ 4.3 Configuration Spring
- [ ] **Injection de dépendance** : Utilisation de `@Configuration`
- [ ] **Éviter `@Component`** dans le domaine
- [ ] **Gestion des transactions** : `@Transactional` dans l'application

## 🧪 Phase 5 : Stratégie de Test

### ✅ 5.1 Tests par Couche
- [ ] **Tests unitaires du domaine** : Sans dépendances externes
- [ ] **Tests d'intégration** : Par adaptateur spécifique  
- [ ] **Tests end-to-end** : Flux complets
- [ ] **Mocking strategy** : Interfaces bien définies

### ✅ 5.2 Testabilité
- [ ] **Isolation du domaine** : Tests sans Spring Context
- [ ] **Adaptateurs mockables** : Interfaces clairement définies
- [ ] **Données de test** : Jeux de données cohérents

## 📝 Phase 6 : Naming et Conventions

### ✅ 6.1 Conventions de Nommage
- [ ] **Ports** : Suffixe "Port" ou noms explicites d'interfaces
- [ ] **Adaptateurs** : Suffixe "Adapter" 
- [ ] **Services** : Suffixe "Service"
- [ ] **Repositories** : Suffixe "Repository"

### ✅ 6.2 Structure des Packages
- [ ] **Cohérence** : Nommage uniforme entre modules
- [ ] **Lisibilité** : Structure claire et intuitive
- [ ] **Séparation** : Concerns bien séparés

## 🎯 Phase 7 : Questions de Validation Finale

### ✅ 7.1 Questions Critiques à Se Poser
- [ ] **Le domaine est-il complètement isolé ?**
- [ ] **Les dépendances pointent-elles vers l'intérieur ?**
- [ ] **Peut-on tester le domaine sans Spring ?**
- [ ] **Peut-on changer de base de données sans impact sur le domaine ?**
- [ ] **Peut-on ajouter une nouvelle interface (GraphQL) facilement ?**

### ✅ 7.2 Validation des Flux
- [ ] **Flux d'entrée** : HTTP → Contrôleur → Service → Port API
- [ ] **Flux de sortie** : Port SPI → Adaptateur → Base/Service externe
- [ ] **Mapping** : DTO ↔ Domain ↔ JPA entities clairement défini

## 🚦 Phase 8 : Checklist Pré-Codage

### ✅ 8.1 Avant de Commencer
- [ ] **Architecture validée** avec le demandeur
- [ ] **Modules Maven** structure approuvée
- [ ] **Ports et Adaptateurs** identifiés et documentés
- [ ] **Stack technique** confirmée (Spring Boot, H2, MapStruct)
- [ ] **Stratégie de tests** définie

### ✅ 8.2 Ordre de Développement Recommandé
1. **Module domain** : Entités, services, ports
2. **Module infrastructure** : Adaptateurs de sortie, repositories
3. **Module application** : Contrôleurs, DTOs, mappers
4. **Module ms-launcher** : Configuration, assemblage
5. **Tests** : Unitaires → Intégration → E2E

---

## 💡 Points d'Attention Spéciaux

### ⚠️ Pièges à Éviter
- **Dépendances circulaires** entre modules
- **Logique métier** dans les adaptateurs
- **Annotations Spring** dans le domaine
- **Couplage fort** entre couches
- **Tests qui nécessitent** le contexte Spring pour le domaine

### 🎯 Objectifs à Atteindre
- **Domaine pur** et testable isolément
- **Flexibilité** pour changer d'adaptateurs
- **Maintenabilité** et évolutivité
- **Séparation claire** des responsabilités
- **Code réutilisable** et modulaire