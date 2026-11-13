# Forces & Propeller — Quand ∑ẑᵢ = 0 relie Lagrange, Gauss et Ramanujan

> **Démos interactives** : [Forces & Gaussian Propeller](https://lombard-web-services.github.io/Gaussian-Propeller-Ramanujan/Forces_and_Gaussian_Propeller.html) · [Max-Cut & Propeller](https://lombard-web-services.github.io/Gaussian-Propeller-Ramanujan/maxcut-propeller-ramanujan.html)

## Le pont géométrique

Ce projet explore une intuition visuelle : **l'équilibre de trois forces concourantes**, **le flux d'un champ de Gauss**, et **la partition en cônes d'un "propeller" gaussien** ne sont qu'une seule et même géométrie, vue sous trois angles.

Le fil rouge est l'équation `∑ ẑᵢ = 0` — la somme des directions de centroïdes d'une partition optimale s'annule. Cette contrainte, qui apparaît naturellement en mécanique lagrangienne (polygone des forces fermé), structure aussi les partitions de Voronoi et les bornes d'approximation pour Max-Cut.

### Ce que les démos montrent

| Scène | Concept | Lien avec la littérature |
|-------|---------|--------------------------|
| Équilibre de trois forces | `P + Q + S = 0` | Leçon 3 §24 (mécanique classique) |
| Parallélogramme des forces | `R = P + Q` | Leçon 3 §29 |
| Dipôle source/puits | `⟨zᵢ, zⱼ⟩ < 0` | Lemme 2.2, cônes "dos à dos" |
| Cônes Kᵢ du propeller | Partition par score maximal | Khot–Naor (kernel clustering) |
| Arrondi gaussien | `αₖ = (8π/9)(1 − 1/k)` | Théorème 2.1 de Khot–Naor |
| Max-Cut & hyperplan GW | `α_GW ≈ 0.878` | Goemans–Williamson |
| Borne de Grothendieck | `K_G ∈ [1.676, 1.782]` | Formes quadratiques, SDP |
| Graphes de Ramanujan | `|λ| ≤ 2√(d−1)` | Expansion, NP-difficulté |

## Contexte scientifique

Le résultat central qui motive cette exploration est le **Gaussian propeller bound** :

> **Théorème** (OpenAI, *The Gaussian propeller bound in every dimension*, 24 septembre 2026 [citation:1][citation:5])
> Pour toute partition mesurable `(A₁, …, Aₖ)` de `ℝ^d` et pour la mesure gaussienne standard `γ_d` :
> ```
> ∑ᵢ ‖ ∫_{Aᵢ} x dγ_d(x) ‖²  ≤  9/(8π)
> ```
> La borne est atteinte, pour `d ≥ 2` et `k ≥ 3`, par trois secteurs planaires d'angle `2π/3`, étendus orthogonalement.

Ce résultat a une conséquence pour le **kernel clustering** : combiné au théorème Unique Games, il prouve la NP-difficulté de toute approximation déterministe du clustering à cible identité avec un facteur de perte inférieur à `αₖ = (8π/9)(1 − 1/k)` pour `k ≥ 3` [citation:1][citation:7].

**Ce que ce projet n'est pas** : une preuve, ni une implémentation de l'algorithme d'arrondi. C'est un **outil pédagogique** pour voir la géométrie derrière les équations.

## Les deux démos

### 1. Forces & Gaussian Propeller (pédagogique)

**[Ouvrir la démo](https://lombard-web-services.github.io/Gaussian-Propeller-Ramanujan/Forces_and_Gaussian_Propeller.html)**

24 scènes 3D interactives, navigables à la souris, avec panneau de paramètres et mode cinéma automatique. Chaque scène isole un concept géométrique (équilibre de forces, flux, cônes, graphes) et le relie aux autres.

**Public** : étudiants, curieux, enseignants.
**Ton** : visuel, sans prérequis au-delà de la géométrie de base.

### 2. Max-Cut & Propeller (recherche / expérimental)

**[Ouvrir la démo](https://lombard-web-services.github.io/Gaussian-Propeller-Ramanujan/maxcut-propeller-ramanujan.html)**

Exploration plus technique : tentatives de garantie `α` sur Max-Cut via des constructions géométriques inspirées du propeller et de l'équation d'Allen–Cahn. Inclut des visualisations de l'arrondi gaussien, de la borne de Grothendieck, et des partitions de Voronoi.

**Public** : lecteurs familiers avec SDP, Max-Cut, et les réductions NP-difficiles.
**Statut** : expérimental — voir la section « Limites ».

## Ce que le projet a vraiment prouvé (et ce qu'il n'a pas prouvé)

**Prouvé (au sens de la littérature citée)** : la borne `9/(8π)` est un théorème d'OpenAI (2026), formellement vérifié en Lean pour l'énoncé principal [citation:3][citation:9]. Les bornes `α_GW` et `K_G` sont des résultats classiques.

**Non prouvé par ce projet** : aucune des visualisations ne constitue une preuve. Les scènes « Max-Cut » illustrent des concepts ; elles ne remplacent pas une analyse rigoureuse. Les tentatives de garantie `α` via Allen–Cahn sont des explorations, pas des théorèmes.

**La question ouverte** : peut-on *voir* une amélioration de garantie sur Max-Cut en utilisant la géométrie du propeller ? La réponse actuelle est : non, pas dans ce projet. La géométrie aide à *comprendre* pourquoi `9/(8π)` est une limite naturelle, pas à la contourner.

## Basé sur

- **OpenAI**, *The Gaussian propeller bound in every dimension*, 24 septembre 2026. [PDF](https://github.com/openai/math/blob/main/preprints/The-Gaussian-Propeller-Bound-in-Every-Dimension-September-24-2026/main.pdf) [citation:1][citation:5]
- **Khot & Naor**, *Approximate kernel clustering*, Mathematika 55 (2009). — Le cadre `αₖ` et l'arrondi gaussien.
- **Heilman, Jagannath & Naor**, *Solution of the propeller conjecture in ℝ³*, Discrete Comput. Geom. 50 (2013). — Base du cas `m ≤ 4`.
- **Goemans & Williamson**, *Improved approximation algorithms for maximum cut*, JACM 42 (1995). — `α_GW`.
- **Physique des Lumières** (démos de physique) : [github.com/Lombard-Web-Services/Physique-des-Lumieres](https://github.com/Lombard-Web-Services/Physique-des-Lumieres) — inspiration pour le rendu canvas et les scènes 3D.

## Utilisation

Les deux démos sont des fichiers HTML autonomes. Aucune installation, aucun build.

```bash
# Cloner et ouvrir localement
git clone https://github.com/Lombard-Web-Services/Gaussian-Propeller-Ramanujan.git
cd Gaussian-Propeller-Ramanujan
# Ouvrir Forces_and_Gaussian_Propeller.html dans un navigateur
