# Correction – Exercice Git : Conflit et Récupération de fichier supprimé



# Étape 1 : Initialisation du dépôt

```bash
mkdir projet-git-exo
cd projet-git-exo
git init
echo "Version initiale du projet" > note.txt
git add note.txt
git commit -m "Initial commit with note.txt"
```



# Étape 2 : Création et modification de la branche `feature`

```bash
git checkout -b feature
echo "Ajout depuis la branche feature" >> note.txt
git add note.txt
git commit -m "Modification dans feature"
```

Le fichier `note.txt` contient maintenant :

```
Version initiale du projet
Ajout depuis la branche feature
```



# Étape 3 : Retour sur `main` et modification indépendante

```bash
git checkout main
echo "Ajout depuis la branche main" >> note.txt
git add note.txt
git commit -m "Modification dans main"
```

Le fichier `note.txt` contient alors :

```
Version initiale du projet
Ajout depuis la branche main
```



# Étape 4 : Fusion et gestion du conflit

```bash
git merge feature
```

Git détecte un **conflit dans `note.txt`**, le fichier sera modifié comme suit :

```text
Version initiale du projet
<<<<<<< HEAD
Ajout depuis la branche main
=======
Ajout depuis la branche feature
>>>>>>> feature
```

Le conflit doit être **résolu manuellement** en conservant les deux ajouts :

```text
Version initiale du projet
Ajout depuis la branche main
Ajout depuis la branche feature
```

Une fois modifié :

```bash
git add note.txt
git commit -m "Résolution de conflit entre main et feature"
```



# Étape 5 : Suppression accidentelle du fichier

```bash
rm note.txt
git rm note.txt
git commit -m "Suppression accidentelle de note.txt"
```



# Étape 6 : Récupération du fichier supprimé

Méthode 1 : Récupérer depuis le dernier commit avant suppression

```bash
git checkout HEAD^ -- note.txt
# ou bien
git restore --source=HEAD^ note.txt
```

Puis valider la restauration :

```bash
git add note.txt
git commit -m "Restauration de note.txt après suppression accidentelle"
```



### Résultat final attendu

```bash
git log --oneline
```

Affichera quelque chose comme :

```
f6c3a67 Restauration de note.txt après suppression accidentelle
8b1d9a1 Suppression accidentelle de note.txt
e5b93fe Résolution de conflit entre main et feature
a32f7c1 Modification dans main
bb8d4d1 Modification dans feature
c1f76d0 Initial commit with note.txt
```

