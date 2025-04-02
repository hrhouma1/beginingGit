
##  **Tâche 4.2 – Modifier le microservice client**

### Objectif :
Alléger le code hérité du monolithe pour ne garder **que les fonctionnalités en lecture seule** (supprimer l’ajout, la modification et la suppression de fournisseurs côté client).

### Étapes clés :
1. **Réduire les fonctionnalités dans `supplier.controller.js`** :
   - Conserver uniquement `findAll` et `findOne`.

2. **Alléger `supplier.model.js`** :
   - Garder uniquement `getAll` et `findById`.

3. **Adapter la navigation dans `nav.html`** :
   - Modifier le titre de la navigation.
   - Ajouter un lien vers l’administration (`/admin/suppliers`).

4. **Supprimer les fonctions d’édition côté client** :
   - Supprimer les fichiers HTML : `supplier-add.html`, `supplier-form-fields.html`, `supplier-update.html`.
   - Supprimer les boutons "Ajouter" et "Modifier" dans `supplier-list-all.html`.

5. **Configurer `index.js` pour Docker** :
   - Commenter les lignes 27–37.
   - Changer le port à 8080.

---

##  **Tâche 4.3 – Dockeriser le microservice client**

### Étapes :
1. Créer un fichier `Dockerfile` :
   ```Dockerfile
   FROM node:11-alpine
   RUN mkdir -p /usr/src/app
   WORKDIR /usr/src/app
   COPY . .
   RUN npm install
   EXPOSE 8080
   CMD ["npm", "run", "start"]
   ```

2. Construire l’image Docker :
   ```bash
   docker build --tag customer .
   ```

3. Vérifier les images Docker :
   ```bash
   docker images
   ```

4. Exécuter le conteneur :
   ```bash
   dbEndpoint=$(cat ~/environment/microservices/customer/app/config/config.js | grep 'APP_DB_HOST' | cut -d '"' -f2)
   docker run -d --name customer_1 -p 8080:8080 -e APP_DB_HOST="$dbEndpoint" customer
   ```

5. Vérification dans le navigateur :
   - Accéder à `http://<IP-cloud9>:8080`.
   - Vérifier que les données des fournisseurs s'affichent **sans options d'édition**.

6. Commit et push dans CodeCommit.

---

##  **Tâche 4.4 – Modifier le microservice employé**

### Objectif :
Adapter l'application employé pour gérer **les fonctionnalités d'administration** sous le chemin `/admin`.

### Étapes :
1. Dans `supplier.controller.js`, ajouter `/admin` aux chemins de redirection.

2. Dans `index.js` :
   - Préfixer tous les `app.get` / `app.post` avec `/admin`.
   - Changer le port à 8081.

3. Modifier les fichiers de vues :
   - Mettre à jour les `form action` et les `href` avec `/admin`.
   - Changer les titres dans `header.html` et `nav.html`.
   - Ajouter un lien vers la zone client.

---

##  **Tâche 4.5 – Dockeriser le microservice employé**

### Étapes :
1. Copier le `Dockerfile` du client.
2. Modifier la ligne :
   ```Dockerfile
   EXPOSE 8081
   ```

3. Construire l’image :
   ```bash
   docker build --tag employee .
   ```

4. Lancer le conteneur :
   ```bash
   docker run -d --name employee_1 -p 8081:8081 -e APP_DB_HOST="$dbEndpoint" employee
   ```

5. Accéder à l'interface d'administration :
   - `http://<IP-cloud9>:8081/admin/suppliers`
   - Vérifier les fonctionnalités : ajout, modification, suppression de fournisseurs.

