# Exercice Git – Gestion de conflit et récupération de fichier supprimé

# Objectifs :
- Manipuler les branches Git  
- Gérer un **conflit de fusion**  
- **Récupérer un fichier supprimé accidentellement** à l'aide de Git  



# Contexte :
Vous travaillez sur un projet collaboratif en équipe. Le fichier `note.txt` contient des informations importantes. Deux branches (`main` et `feature`) sont modifiées en parallèle, ce qui entraîne un conflit lors de la fusion.



# Étapes à suivre :

## Étape 1 : Initialiser le dépôt
```bash
mkdir projet-git-exo
cd projet-git-exo
git init
echo "Version initiale du projet" > note.txt
git add note.txt
git commit -m "Initial commit with note.txt"
```

## Étape 2 : Créer une branche `feature`
```bash
git checkout -b feature
echo "Ajout depuis la branche feature" >> note.txt
git add note.txt
git commit -m "Modification dans feature"
```

## Étape 3 : Retourner à `main` et modifier aussi `note.txt`
```bash
git checkout main
echo "Ajout depuis la branche main" >> note.txt
git commit -am "Modification dans main"
```

## Étape 4 : Tenter de fusionner `feature` dans `main` (conflit attendu)
```bash
git merge feature
```

👉 Résolvez le conflit manuellement dans `note.txt`. Gardez **les deux ajouts**.  
Ensuite :
```bash
git add note.txt
git commit -m "Résolution de conflit"
```



## 🗑️ Étape 5 : Suppression accidentelle
Supposez que quelqu’un supprime le fichier :
```bash
rm note.txt
git rm note.txt
git commit -m "Suppression accidentelle de note.txt"
```

## ♻️ Étape 6 : Récupérer le fichier supprimé
- Utilisez une commande Git pour restaurer le fichier supprimé à son dernier état avant suppression.

> 💡 Astuce : Utilisez `git log`, `git checkout`, ou `git restore` selon votre méthode.



## Critères d’évaluation :
- Le conflit est bien résolu avec les deux versions conservées.
- Le fichier `note.txt` est récupéré sans erreur.
- Les commits sont clairs et reflètent chaque étape.

