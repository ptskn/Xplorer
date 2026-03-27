# Game Design Document — Architecte Magique

## Version 0.1 — Concept initial

---

## 1. Vision

**Titre de travail** : Architecte Magique (nom definitif a trouver avec ta fille)

**Pitch en une phrase** :
Une apprentie architecte-magicienne explore des iles flottantes et construit des structures magiques en 3D pour resoudre des enigmes — ou la magie, c'est la geometrie.

**Cible** : 7-10 ans (CE2 → CM2), jouable manette PS5 sur PC

**Pilliers de design** :
1. **Construire** — Manipuler des formes 3D, assembler, transformer
2. **Decouvrir** — Explorer des mondes beaux et surprenants
3. **Apprendre sans s'en rendre compte** — Les maths/sciences sont la mecanique, pas un quiz plaque

---

## 2. Univers & histoire

### Le monde
Un archipel d'**iles flottantes** dans le ciel, chacune avec un ecosysteme et un theme visuel distinct. Les iles sont reliees par des ponts magiques que le joueur doit construire ou reparer.

### Iles (mondes/niveaux)
| Ile | Theme visuel | Theme educatif | Inspirations |
|-----|-------------|----------------|-------------|
| **Ile des Formes** | Cristaux geometriques, grottes | Formes 2D/3D, angles, symetrie | Tutoriel |
| **Ile Celeste** | Ciel, etoiles, observatoire | Systeme solaire, distances, echelles | Concept 1 (Spatial) |
| **Ile Verdoyante** | Foret luxuriante, cascades | Ecosysteme, chaines alimentaires, cycles | Concept 3 (Labo Vivant) |
| **Ile de Givre** | Glace, neige, aurores boreales | Etats de la matiere, temperatures, mesures | Sciences |
| **Ile des Mecanismes** | Engrenages, steampunk doux | Forces, equilibre, leviers, poids | Sciences/techno |
| **Ile du Temps** | Ruines anciennes, sabliers | Histoire, chronologie, fractions (sabliers) | Concept 4 (Chrono) |

### Personnage principal
L'apprentie (personnalisable : apparence, nom). Elle a un **compagnon** — une petite creature geometrique (un polyedre vivant qui change de forme selon les emotions — sphere quand content, tetraedre quand nerveux, etc.).

### Narratif leger
Le Grand Architecte a disparu. Les iles se desagregent. L'apprentie doit reconstruire les structures magiques de chaque ile pour les stabiliser. Chaque ile restauree revele un indice sur la disparition du Grand Architecte.

---

## 3. Gameplay

### Boucle principale
```
Explorer l'ile → Trouver un puzzle → Construire la solution → L'ile se transforme/guerit → Debloquer la suite
```

### Mecanique coeur : la Construction Magique

Le joueur dispose d'un **inventaire de formes** (cubes, spheres, cylindres, pyramides, prismes...) et de **sorts geometriques** :

| Sort | Effet | Concept maths |
|------|-------|--------------|
| **Mirroir** | Cree une copie symetrique | Symetrie axiale |
| **Grandir / Retrecir** | Change l'echelle x2, x3, /2 | Multiplication, division, proportions |
| **Tourner** | Rotation 90°, 45° | Angles, rotation |
| **Fusionner** | Combine 2 formes | Composition de formes, aires |
| **Peser** | Affiche le poids d'un bloc | Mesures, comparaisons, equilibre |
| **Decouper** | Coupe une forme en parts | Fractions |
| **Colorer** | Change la matiere/texture | Observation, classification |

### Types de puzzles

1. **Construction libre guidee** — "Construis un pont entre ces deux points" (plusieurs solutions possibles)
2. **Puzzle d'equilibre** — "Place les blocs pour que la balance soit equilibree" (poids, calcul)
3. **Puzzle de symetrie** — "Complete le motif" (symetrie axiale et centrale)
4. **Puzzle de perspective** — "Cette forme doit ressembler a un cercle vue de face et un carre vue de cote" (geometrie 3D, projection)
5. **Puzzle d'ecosysteme** (ile Verdoyante) — "Construis un habitat pour que cet animal puisse vivre" (sciences)
6. **Puzzle de mecanisme** — "Connecte les engrenages pour ouvrir la porte" (forces, logique)

### Progression de difficulte

| Phase | Niveau scolaire | Maths | Nouveaux sorts |
|-------|----------------|-------|---------------|
| Iles 1-2 | CE2 | Formes de base, symetrie simple, additions | Mirroir, Tourner, Colorer |
| Iles 3-4 | CE2-CM1 | Angles, mesures, multiplications | Grandir/Retrecir, Peser |
| Iles 5-6 | CM1 | Fractions, proportions, geometrie avancee | Decouper, Fusionner |

### Mode Bac a Sable
En parallele de l'aventure, un **mode creatif libre** ou elle peut construire ce qu'elle veut sans contrainte. Les formes et sorts debloques en aventure sont disponibles ici.

---

## 4. Controles (DualSense PS5)

| Input | Action |
|-------|--------|
| **Stick gauche** | Deplacer le personnage |
| **Stick droit** | Camera |
| **X (croix)** | Interagir / Poser un bloc |
| **O (rond)** | Annuler / Retirer un bloc |
| **Triangle** | Ouvrir inventaire de formes |
| **Carre** | Ouvrir roue des sorts |
| **L1 / R1** | Tourner le bloc selectionne |
| **L2 / R2** | Zoom avant/arriere (triggers adaptatifs : resistance selon le poids du bloc) |
| **D-pad** | Navigation rapide sorts |
| **Touchpad** | Basculer vue 1ere/3eme personne |
| **Haptique** | Vibration douce quand un bloc "s'emboite" correctement |
| **Triggers adaptatifs** | Resistance quand on souleve un bloc lourd |

---

## 5. Direction artistique

### Style visuel
- **Low-poly colore** — Formes geometriques bien definies, coherent avec le theme
- Palette lumineuse et chaleureuse, inspiration Ghibli / Journey / Tearaway
- Chaque ile a sa palette dominante
- Les formes geometriques sont des elements naturels du monde (les arbres sont des cones, les rochers des polyedres)

### Audio
- Musique douce et melodique par ile (inspiration : Ni no Kuni, Zelda Wind Waker)
- Sons satisfaisants d'assemblage (ASMR construction)
- Le compagnon a des petits sons expressifs

---

## 6. Aspects techniques

### Moteur : Unreal Engine 5
- Rendu stylise (low-poly, pas realiste) — performant
- Nanite pas necessaire (low-poly), Lumen possible pour l'eclairage
- Enhanced Input System pour DualSense
- Blueprint pour la logique de puzzles (ta fille peut participer)
- C++ pour les systemes core (grille de construction, physique puzzles, sauvegarde)

### Architecture envisagee
```
Source/
  Core/           — Game instance, save system, progression
  Player/         — Character, camera, input
  Building/       — Grille de construction, blocs, sorts geometriques
  Puzzles/        — Base puzzle + types specifiques
  World/          — Iles, transitions, ecosystemes
  UI/             — HUD, inventaire, menus
  Companion/      — IA et comportement du compagnon
Content/
  Maps/           — Une map par ile
  Meshes/         — Formes geometriques, decors
  Materials/      — Shaders stylises
  Blueprints/     — Logique puzzles, interactions
  Audio/          — Musique + SFX
```

---

## 7. Scope du prototype (POC)

Pour valider le concept rapidement :

### POC v0.1 — "Le premier puzzle"
- [ ] Un plan 3D simple (une piece de l'ile des Formes)
- [ ] Personnage 3eme personne basique (capsule ou mannequin UE5)
- [ ] Deplacement + camera manette
- [ ] 3 formes placables : cube, sphere, pyramide
- [ ] Grille de snapping (les formes s'alignent proprement)
- [ ] 1 sort : Tourner (rotation 90°)
- [ ] 1 puzzle : "Construis un escalier pour atteindre la plateforme"
- [ ] Feedback visuel/sonore quand le puzzle est resolu

### POC v0.2 — "Ca devient magique"
- [ ] Ile des Formes complete (petit niveau)
- [ ] Sort Mirroir (symetrie)
- [ ] Sort Grandir/Retrecir
- [ ] 3-4 puzzles enchaines
- [ ] Compagnon (suit le joueur, commente)
- [ ] Menu pause basique
- [ ] Sauvegarde

---

## 8. Participation de ta fille

| Tache | Qui | Comment |
|-------|-----|---------|
| Design des iles (dessin) | Elle | Papier, puis on reproduit dans UE5 |
| Apparence du personnage | Elle | Dessiner → modeliser ensemble |
| Design du compagnon | Elle | Choisir les formes et emotions |
| Placer les elements dans les niveaux | Elle | Directement dans l'editeur UE5 (drag & drop) |
| Creer des puzzles | Elle | Blueprints visuels (simple) |
| Tester et donner du feedback | Elle | Jouer a la manette ! |
| Nommer le jeu, les iles, les sorts | Elle | Brainstorm ensemble |
| Logique de sorts (Blueprints) | Ensemble | Tu guides, elle connecte les noeuds |
| Code C++ (systemes) | Toi | Building system, save, core |
| Shaders et rendu | Toi + moi | Materials UE5 |

---

## 9. References visuelles et ludiques

- **Monument Valley** — Puzzles de perspective, esthetique geometrique
- **Tearaway / Tearaway Unfolded** — Monde artisanal, interaction tactile
- **Captain Toad Treasure Tracker** — Puzzles 3D compacts, accessible enfants
- **Fantastic Contraption VR** — Construction physique creative
- **Journey** — Ambiance, direction artistique
- **Zelda: Tears of the Kingdom** — Systeme de construction libre (Ultrahand)
- **Minecraft** — Mode creatif, accessibilite enfants
