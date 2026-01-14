#  Sokoban — Jeu en Python (Tkinter)

##  Description générale
Ce projet est une implémentation du jeu **Sokoban** développée en **Python**,
en utilisant la bibliothèque graphique **Tkinter** pour créer une interface utilisateur interactive.

L’objectif du jeu est de déplacer des boîtes dans un entrepôt afin de les placer
sur des cases objectifs, en respectant une logique stricte d’interactions entre
les différents éléments : joueur, boîtes, murs et objectifs.

---

##  Technologies utilisées
- Python
- Tkinter (interface graphique)
- Programmation orientée objet
- Gestion de matrices (format XSB)
- Jupyter Notebook

---

##  Architecture et composants principaux

###  Classe `Mover` — Le joueur
La classe `Mover` représente le joueur (ou tout élément mobile).

**Responsabilités principales :**
- **Gestion des déplacements**  
  La méthode `moveTowards` permet au joueur de se déplacer dans une direction donnée.
  Le déplacement est validé par la méthode `canMove`.  
  Si un déplacement est impossible, une animation visuelle (cercle rouge)
  signale l’obstacle.  
  Lorsqu’une boîte est rencontrée, elle est poussée si la case suivante est libre.

- **Gestion de l’apparence**  
  L’image du joueur change selon la direction du déplacement
  (`Left`, `Right`, `Up`, `Down`) via la méthode `setupImageForDirection`.

- **Autres méthodes importantes**
  - `xsbChar` : génère le caractère correspondant au joueur dans la matrice XSB
  - `isMoveable` : vérifie si l’élément peut être déplacé
  - `canBeCovered` : vérifie si une case peut être occupée

---

###  Classe `Level` — Un niveau du jeu
La classe `Level` représente un niveau complet du jeu, construit à partir
d’une matrice XSB (`xsbMatrix`).

**Fonctionnalités :**
- **Initialisation du niveau**  
  Analyse de la matrice ligne par ligne pour identifier :
  - murs
  - boîtes
  - objectifs
  - joueur
  - sol vide  

  Chaque caractère génère une instance correspondante
  (`Wall`, `Box`, `Goal`, `Mover`) stockée dans une matrice interne (`warehouse`).

- **Dimensions dynamiques**  
  Le canevas est automatiquement redimensionné en fonction
  du nombre de lignes et de colonnes du niveau.

- **Gestion du clavier**  
  Les touches directionnelles (`Left`, `Right`, `Up`, `Down`)
  sont associées aux mouvements du joueur.

- **Superposition graphique**  
  L’affichage est géré à l’aide de tags Tkinter :
  - `static` pour les éléments fixes
  - `movable` pour les éléments mobiles  
  afin de garantir un rendu visuel correct.

---

###  Classe `Sokoban` — Menu principal
La classe `Sokoban` constitue le **point d’entrée** du programme.

**Fonctionnalités :**
- Sélection du niveau via un menu déroulant (`OptionMenu`)
- Bouton **Start** pour lancer le niveau choisi
- Gestion de la navigation entre les fenêtres (menu → jeu)

---

##  Fonctionnement du jeu

### Chargement des niveaux
Les niveaux sont définis dans la structure `SokobanXSBLevels`,
sous forme de matrices XSB.

**Symboles utilisés :**
- `#` : Mur  
- `$` : Boîte  
- `.` : Objectif  
- `@` : Joueur  
- `+` : Joueur sur un objectif  
- `*` : Boîte sur un objectif  
- ` ` : Sol vide  

---

### Mouvements et interactions
- Le joueur se déplace via les touches directionnelles
- Une boîte est poussée uniquement si la case suivante est libre
- Les déplacements impossibles sont signalés par une animation visuelle

---

### Affichage
- Les éléments sont affichés sur un **Canvas Tkinter**
- Les images (ex. `player.png`) sont chargées et positionnées
  selon les coordonnées de la matrice

---

### Fin de partie
La condition de victoire n’est pas encore implémentée,
mais peut être ajoutée facilement en vérifiant, après chaque mouvement,
si toutes les boîtes sont positionnées sur les objectifs.

---

##  Propositions d’amélioration

- **Mode multijoueur** (coopératif ou compétitif)
- **Statistiques de jeu** : nombre de mouvements, temps, scores
- **Mode créatif** : éditeur de niveaux
- **Intelligence artificielle**
  - Solveur automatique (ex. algorithme A*)
  - Analyse des stratégies du joueur
  - Génération dynamique de niveaux
- **Amélioration graphique** : animations, effets sonores
- **Défis quotidiens** avec puzzles générés automatiquement

---

##  Lancer le jeu
1. Installer Python 3
2. Cloner le dépôt
3. Se placer dans le dossier du projet
4. Lancer :
```bash
python main.py
