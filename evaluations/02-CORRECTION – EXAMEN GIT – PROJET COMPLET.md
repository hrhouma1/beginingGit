# CORRECTION – EXAMEN GIT – PROJET COMPLET

<br/>

### PARTIE 2.1 – Initialisation et première version

```bash
Commande 1 : mkdir projet_git_features
Commande 2 : cd projet_git_features
Commande 3 : git init
Commande 4 : echo "Projet Git Features" > README.md
Commande 5 : git add README.md
Commande 6 : git commit -m "Initialisation avec README.md"
```

<br/>

### PARTIE 2.2 – Création de branches en cascade

#### Branche feature-1

```bash
Commande 7 : git checkout -b feature-1
Commande 8 : echo "version 1" > log.txt
Commande 9 : git add log.txt
Commande 10 : git commit -m "Ajout de la version 1 dans log.txt"
```

#### Branche feature-2

```bash
Commande 11 : git checkout -b feature-2
Commande 12 : echo "version 2" >> log.txt
Commande 13 : git add log.txt
Commande 14 : git commit -m "Ajout de la version 2 dans log.txt"
```

#### Branche feature-3

```bash
Commande 15 : git checkout -b feature-3
Commande 16 : echo "version 3" >> log.txt
Commande 17 : git add log.txt
Commande 18 : git commit -m "Ajout de la version 3 dans log.txt"
```

#### Branche feature-4

```bash
Commande 19 : git checkout -b feature-4
Commande 20 : echo "version 4" >> log.txt
Commande 21 : git add log.txt
Commande 22 : git commit -m "Ajout de la version 4 dans log.txt"
```

#### Branche feature-5

```bash
Commande 23 : git checkout -b feature-5
Commande 24 : echo "version 5" >> log.txt
Commande 25 : git add log.txt
Commande 26 : git commit -m "Ajout de la version 5 dans log.txt"
```

<br/>

### PARTIE 2.3 – Fusions successives et suppression de branches

#### Fusion feature-5 → feature-4

```bash
Commande 27 : git checkout feature-4
Commande 28 : git merge feature-5
Commande 29 : git branch -d feature-5
Commande 30 : git log --oneline --graph --all
```

#### Fusion feature-4 → feature-3

```bash
Commande 31 : git checkout feature-3
Commande 32 : git merge feature-4
Commande 33 : git branch -d feature-4
Commande 34 : git log --oneline --graph --all
```

#### Fusion feature-3 → feature-2

```bash
Commande 35 : git checkout feature-2
Commande 36 : git merge feature-3
Commande 37 : git branch -d feature-3
Commande 38 : git log --oneline --graph --all
```

#### Fusion feature-2 → feature-1

```bash
Commande 39 : git checkout feature-1
Commande 40 : git merge feature-2
Commande 41 : git branch -d feature-2
Commande 42 : git log --oneline --graph --all
```

#### Fusion feature-1 → main

```bash
Commande 43 : git checkout main
Commande 44 : git merge feature-1
Commande 45 : git branch -d feature-1
Commande 46 : git log --oneline --graph --all
```

#### Nettoyage final

```bash
Commande 47 : git branch                         # Vérification des branches restantes
Commande 48 : git status                         # Vérification de l’état du projet
Commande 49 : cat log.txt                        # Vérification du contenu cumulé
Commande 50 : git log --oneline                  # Vérification des commits
```

<br/>

### PARTIE 2.4 – Projet ambigu avec contenu perdu

```bash
Commande 51 : mkdir ambigu-git
Commande 52 : cd ambigu-git
Commande 53 : git init
Commande 54 : echo "Base du projet" > log.txt
Commande 55 : git add log.txt
Commande 56 : git commit -m "Initialisation du projet avec log.txt"
```

<br/>

### PARTIE 2.5 – Modification non validée et fusion sans effet

```bash
Commande 57 : git checkout -b config-dev
Commande 58 : echo "Contenu temporaire mais critique" >> log.txt
Commande 59 : git checkout -b patch-x
Commande 60 : echo "Correctif appliqué" > patch.txt
Commande 61 : git add patch.txt
Commande 62 : git commit -m "Ajout du patch X"
Commande 63 : git checkout main
Commande 64 : git merge config-dev
```

<br/>

### PARTIE 2.6 – Restauration du contenu perdu

```bash
Commande 65 : git checkout config-dev -- log.txt
Commande 66 : git add log.txt
Commande 67 : git commit -m "Restauration du contenu perdu de log.txt depuis config-dev"
```

<br/>

### PARTIE 2.7 – Suppression accidentelle et récupération d’un fichier

#### Création du projet

```bash
Commande 68 : mkdir restauration-fichier
Commande 69 : cd restauration-fichier
Commande 70 : git init
Commande 71 : echo -e "version 1\nversion 2\nversion 3\nversion 4\nversion 5" > log.txt
Commande 72 : git add log.txt
Commande 73 : git commit -m "Ajout initial de log.txt avec cinq versions"
```

#### Suppression accidentelle

```bash
Commande 74 : rm log.txt
Commande 75 : git rm log.txt
Commande 76 : git commit -m "Suppression accidentelle de log.txt"
```

#### Récupération

```bash
Commande 77 : git checkout HEAD^ -- log.txt
Commande 78 : git add log.txt
Commande 79 : git commit -m "Restauration complète de log.txt après suppression"
```

<br/>

### QUESTIONS POUR `analyse.txt`

1. **Pourquoi la fusion avec `config-dev` n’a-t-elle ramené aucun contenu ?**  
   Parce que les modifications n’ont jamais été validées dans un commit. Git ne fusionne que les modifications validées.

2. **À quel moment précis le contenu a-t-il été perdu ?**  
   Lors du changement de branche de `config-dev` vers `patch-x`, sans commit préalable. La modification dans `log.txt` était en mémoire mais non sauvegardée.

3. **Quelle commande permet de le restaurer ?**  
   `git checkout config-dev -- log.txt`

4. **Quelle commande permet de récupérer un fichier supprimé ?**  
   `git checkout HEAD^ -- nom_du_fichier`

5. **Quelles bonnes pratiques professionnelles permettent d’éviter ce genre de perte ?**  
   - Toujours valider (`commit`) les changements importants.  
   - Utiliser des branches de travail bien identifiées.  
   - Utiliser `git stash` pour sauvegarder temporairement les modifications non terminées.  
   - Vérifier l’état du projet avec `git status` avant tout changement de branche.  
   - Sauvegarder fréquemment avec des commits clairs et fréquents.
