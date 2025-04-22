# TUTORIEL CI/CD – HTML/CSS/JS – DÉPLOIEMENT AUTOMATIQUE AVEC VERCEL

<br/>

### PARTIE 1 – Initialisation du projet local

```bash
Commande 1 : mkdir projet_vercel_ci
Commande 2 : cd projet_vercel_ci
Commande 3 : touch index.html style.css script.js
Commande 4 : echo "# Mon premier site avec CI/CD" > README.md
```

<br/>

### PARTIE 2 – Écriture des fichiers HTML, CSS, JS

**index.html**
```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>CI/CD avec Vercel</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>Bienvenue sur mon site déployé automatiquement</h1>
  <p id="date"></p>
  <script src="script.js"></script>
</body>
</html>
```

**style.css**
```css
body {
  font-family: Arial, sans-serif;
  background-color: #e6f0ff;
  text-align: center;
  padding-top: 50px;
}
```

**script.js**
```javascript
document.getElementById("date").innerText =
  "Date actuelle : " + new Date().toLocaleDateString();
```

<br/>

### PARTIE 3 – Création du dépôt Git

```bash
Commande 5 : git init
Commande 6 : git add .
Commande 7 : git commit -m "Initialisation du projet HTML/CSS/JS"
```

<br/>

### PARTIE 4 – Création et liaison au dépôt GitHub

1. Aller sur [https://github.com](https://github.com) et créer un dépôt nommé `site-vercel`.

2. Ensuite en ligne de commande :

```bash
Commande 8 : git branch -M main
Commande 9 : git remote add origin https://github.com/<utilisateur>/site-vercel.git
Commande 10 : git push -u origin main
```

Remplacer `<utilisateur>` par votre nom d'utilisateur GitHub.

<br/>

### PARTIE 5 – Connexion à Vercel

1. Aller sur [https://vercel.com](https://vercel.com)
2. Créer un compte (ou se connecter) avec GitHub
3. Cliquer sur "Add New Project"
4. Sélectionner le dépôt `site-vercel`
5. Laisser toutes les options par défaut (pas de framework à spécifier)
6. Cliquer sur "Deploy"

Vercel attribue une URL publique à votre site.

<br/>

### PARTIE 6 – Vérification du déploiement

```bash
Commande 11 : git log --oneline                       # Historique Git
Commande 12 : git status                              # État du projet
Commande 13 : git remote -v                           # Vérification de la connexion à GitHub
```

<br/>

### PARTIE 7 – Mise à jour du site (test du CI/CD)

1. Modifier `index.html` :

```html
<h1>Site mis à jour automatiquement avec Git + Vercel</h1>
```

2. Puis :

```bash
Commande 14 : git add index.html
Commande 15 : git commit -m "Mise à jour du titre principal"
Commande 16 : git push
```

Attendre quelques secondes. Le site est automatiquement redéployé.

<br/>

### PARTIE 8 – Résultat attendu

- Code source versionné sur GitHub
- Site déployé automatiquement via CI/CD
- URL publique en HTTPS générée par Vercel
- Processus reproductible sans outil complexe

<br/>
