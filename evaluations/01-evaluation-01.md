## CONSIGNES GÉNÉRALES

- Complétez chaque section dans l’ordre.  
- Ne sautez **aucune étape**.  
- **Respectez strictement les noms de fichiers, de branches et messages de commit.**  
- Ne recréez **aucun fichier manuellement après suppression**.  
- Ne faites **aucun raccourci** (pas de commandes combinées ou implicites).

<br/>
<br/>

## PARTIE 2.1 – Initialisation et première version

```bash
Commande 1 : ___________________________________________   # Créer un dossier nommé projet_git_features
Commande 2 : ___________________________________________   # Se déplacer dans le dossier
Commande 3 : ___________________________________________   # Initialiser un dépôt Git
Commande 4 : ___________________________________________   # Créer un fichier README.md avec le texte "Projet Git Features"
Commande 5 : ___________________________________________   # Ajouter README.md à la zone d’indexation
Commande 6 : ___________________________________________   # Effectuer un commit avec le message : Initialisation avec README.md
```

<br/>
<br/>

## PARTIE 2.2 – Création de branches en cascade

## Branche feature-1 :

```bash
Commande 7 : ___________________________________________   # Créer et basculer sur la branche feature-1
Commande 8 : ___________________________________________   # Créer log.txt avec la ligne "version 1"
Commande 9 : ___________________________________________   # Ajouter log.txt à l’index
Commande 10 : __________________________________________   # Commit avec le message : Ajout de la version 1 dans log.txt
```

## Branche feature-2 :

```bash
Commande 11 : ___________________________________________   # Créer et basculer sur la branche feature-2 depuis feature-1
Commande 12 : ___________________________________________   # Ajouter la ligne "version 2" à log.txt
Commande 13 : ___________________________________________   # Ajouter à l’index
Commande 14 : ___________________________________________   # Commit avec le message : Ajout de la version 2 dans log.txt
```

## Branche feature-3 :

```bash
Commande 15 : ___________________________________________   # Créer et basculer sur la branche feature-3 depuis feature-2
Commande 16 : ___________________________________________   # Ajouter la ligne "version 3" à log.txt
Commande 17 : ___________________________________________   # Ajouter à l’index
Commande 18 : ___________________________________________   # Commit avec le message : Ajout de la version 3 dans log.txt
```

## Branche feature-4 :

```bash
Commande 19 : ___________________________________________   # Créer et basculer sur la branche feature-4 depuis feature-3
Commande 20 : ___________________________________________   # Ajouter la ligne "version 4" à log.txt
Commande 21 : ___________________________________________   # Ajouter à l’index
Commande 22 : ___________________________________________   # Commit avec le message : Ajout de la version 4 dans log.txt
```

## Branche feature-5 :

```bash
Commande 23 : ___________________________________________   # Créer et basculer sur la branche feature-5 depuis feature-4
Commande 24 : ___________________________________________   # Ajouter la ligne "version 5" à log.txt
Commande 25 : ___________________________________________   # Ajouter à l’index
Commande 26 : ___________________________________________   # Commit avec le message : Ajout de la version 5 dans log.txt
```

<br/>
<br/>

## PARTIE 2.3 – Fusions successives et suppression de branches

## Fusion feature-5 → feature-4 :

```bash
Commande 27 : ___________________________________________   # Basculez sur la branche feature-4
Commande 28 : ___________________________________________   # Fusionner la branche feature-5 dans feature-4
Commande 29 : ___________________________________________   # Supprimer localement la branche feature-5
Commande 30 : ___________________________________________   # Afficher l’historique simplifié (graphique)
```

> Répétez cette séquence pour fusionner :
- feature-4 dans feature-3
- feature-3 dans feature-2
- feature-2 dans feature-1
- feature-1 dans main

Continuez la numérotation :  
**Commande 31 à 50**

<br/>
<br/>

## PARTIE 2.4 – Projet ambigu avec contenu perdu

```bash
Commande 51 : ___________________________________________   # Créer un dossier ambigu-git
Commande 52 : ___________________________________________   # Se déplacer dans le dossier
Commande 53 : ___________________________________________   # Initialiser un dépôt Git
Commande 54 : ___________________________________________   # Créer log.txt avec le contenu : Base du projet
Commande 55 : ___________________________________________   # Ajouter log.txt à l’index
Commande 56 : ___________________________________________   # Commit avec le message : Initialisation du projet avec log.txt
```

<br/>
<br/>

## PARTIE 2.5 – Modification non validée et fusion sans effet

```bash
Commande 57 : ___________________________________________   # Créer une branche config-dev
Commande 58 : ___________________________________________   # Ajouter une ligne non commitée : Contenu temporaire mais critique
Commande 59 : ___________________________________________   # Créer une branche patch-x depuis config-dev
Commande 60 : ___________________________________________   # Créer patch.txt avec une ligne de votre choix
Commande 61 : ___________________________________________   # Ajouter patch.txt à l’index
Commande 62 : ___________________________________________   # Commit avec le message : Ajout du patch X
Commande 63 : ___________________________________________   # Basculez dans la branche main
Commande 64 : ___________________________________________   # Fusionner config-dev dans main
```

<br/>
<br/>

## PARTIE 2.6 – Restauration du contenu perdu

```bash
Commande 65 : ___________________________________________   # Récupérer le contenu non commité de log.txt
Commande 66 : ___________________________________________   # Ajouter log.txt à l’index
Commande 67 : ___________________________________________   # Commit avec le message : Restauration du contenu perdu de log.txt depuis config-dev
```

<br/>
<br/>

## PARTIE 2.7 – Suppression accidentelle et récupération d’un fichier

## 2.7.1 – Création du projet

```bash
Commande 68 : ___________________________________________   # Créer un dossier restauration-fichier
Commande 69 : ___________________________________________   # Se déplacer dans ce dossier
Commande 70 : ___________________________________________   # Initialiser un dépôt Git
Commande 71 : ___________________________________________   # Créer log.txt avec les 5 lignes version 1 à version 5
Commande 72 : ___________________________________________   # Ajouter log.txt à l’index
Commande 73 : ___________________________________________   # Commit avec le message : Ajout initial de log.txt avec cinq versions
```

## 2.7.2 – Suppression accidentelle

```bash
Commande 74 : ___________________________________________   # Supprimer physiquement log.txt
Commande 75 : ___________________________________________   # Enregistrer la suppression avec git rm
Commande 76 : ___________________________________________   # Commit avec le message : Suppression accidentelle de log.txt
```

## 2.7.3 – Récupération

```bash
Commande 77 : ___________________________________________   # Restaurer le fichier supprimé avec Git
Commande 78 : ___________________________________________   # Ajouter à l’index
Commande 79 : ___________________________________________   # Commit avec le message : Restauration complète de log.txt après suppression
```

<br/>
<br/>

## FICHIERS À REMETTRE

- Dossiers `.git` de :
  - `projet_git_features/`  
  - `ambigu-git/`  
  - `restauration-fichier/`  
- `git_commands.txt` rempli  
- `analyse.txt` avec les réponses suivantes :

### QUESTIONS POUR `analyse.txt`

1. Pourquoi la fusion avec `config-dev` n’a-t-elle ramené aucun contenu ?  
2. À quel moment précis le contenu a-t-il été perdu ?  
3. Quelle commande permet de le restaurer ?  
4. Quelle commande permet de récupérer un fichier supprimé ?  
5. Quelles bonnes pratiques professionnelles permettent d’éviter ce genre de perte ?
