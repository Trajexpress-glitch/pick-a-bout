[README.md](https://github.com/user-attachments/files/27863118/README.md)
# 📱 PICK A BOUT - Documentation Complète

## 🎯 Vue d'ensemble

**Pick A Bout** est une plateforme d'affiliation moderne construite pour promouvoir et vendre les produits **Voghion** via le réseau **Awin**.

### Caractéristiques principales
- ✅ Catalogue de produits Voghion avec toutes les catégories
- ✅ Système de filtrage par catégorie
- ✅ Recherche de produits
- ✅ Affichage des promotions en temps réel
- ✅ Intégration API Awin complète
- ✅ Design professionnel et responsive
- ✅ Pagination intelligente (12 produits par page)

---

## 📋 Prérequis

Avant de commencer, assure-toi d'avoir :

1. **Node.js** (version 14+) - [Télécharger](https://nodejs.org/)
2. **npm** ou **yarn** (gestionnaire de paquets)
3. Tes **identifiants Awin** :
   - ID éditeur : `1075505`
   - Clé API : `3e2cb2e4-9c34-482a-80a1-cea2b00f41b5`
4. Un **éditeur de code** (VS Code, Sublime, etc.)

Vérifie l'installation :
```bash
node --version
npm --version
```

---

## 🚀 Installation et Lancement

### Étape 1 : Créer la structure du projet

```bash
# Crée un dossier pour ton projet
mkdir pick-a-bout
cd pick-a-bout

# Crée les dossiers backend et frontend
mkdir backend frontend
```

### Étape 2 : Configuration du Backend

```bash
cd backend

# Copie les fichiers
# - server.js (le serveur)
# - package.json (renommé de backend-package.json)
# - .env (copié de .env.example)

# Installe les dépendances
npm install

# Lance le serveur
npm start
```

Le serveur devrait démarrer sur `http://localhost:5000` ✅

### Étape 3 : Configuration du Frontend

```bash
cd ../frontend

# Installe Vite (si pas déjà installé)
npm create vite@latest . -- --template react

# Ou si tu as déjà les fichiers :
# - App.jsx
# - App.css
# - components/ (Header.jsx, ProductCatalog.jsx, etc.)
# - package.json (renommé de frontend-package.json)

# Installe les dépendances
npm install

# Lance le serveur de développement
npm run dev
```

Le frontend devrait être accessible sur `http://localhost:5173` 🎉

---

## 📁 Structure du Projet

```
pick-a-bout/
│
├── backend/
│   ├── server.js              # Serveur Express principal
│   ├── package.json           # Dépendances Node.js
│   └── .env                   # Variables d'environnement
│
├── frontend/
│   ├── src/
│   │   ├── App.jsx            # Composant principal
│   │   ├── App.css            # Styles globaux
│   │   ├── main.jsx           # Point d'entrée React
│   │   ├── index.css          # Styles de base
│   │   └── components/
│   │       ├── Header.jsx
│   │       ├── ProductCatalog.jsx
│   │       ├── ProductCard.jsx
│   │       ├── CategoryFilter.jsx
│   │       ├── Promotions.jsx
│   │       └── Footer.jsx
│   │
│   ├── package.json
│   ├── vite.config.js         # Configuration Vite
│   └── index.html             # HTML principal
│
└── README.md                  # Ce fichier
```

---

## 🔧 Configuration des Variables d'Environnement

### Backend (.env)

```
PORT=5000
AWIN_PUBLISHER_ID=1075505
AWIN_API_KEY=3e2cb2e4-9c34-482a-80a1-cea2b00f41b5
VOGHION_MERCHANT_ID=44635
```

### Frontend (.env ou .env.local)

```
REACT_APP_API_URL=http://localhost:5000
```

---

## 📡 API Endpoints

### Base URL
```
http://localhost:5000/api
```

### Endpoints disponibles

#### 1. Récupérer tous les produits
```
GET /api/products?page=1&limit=12&category=1&search=mode
```

**Paramètres** :
- `page` (optionnel) : Numéro de page (défaut: 1)
- `limit` (optionnel) : Produits par page (défaut: 12)
- `category` (optionnel) : ID de catégorie
- `search` (optionnel) : Terme de recherche

**Réponse** :
```json
{
  "success": true,
  "products": [
    {
      "id": "123",
      "name": "Chemise Bleue",
      "price": 49.99,
      "originalPrice": 79.99,
      "discount": 37,
      "category": "Mode",
      "image": "url",
      "clickUrl": "lien_awin",
      "commissionRate": 5
    }
  ],
  "total": 150,
  "page": 1,
  "limit": 12,
  "pages": 13
}
```

#### 2. Récupérer un produit spécifique
```
GET /api/products/:id
```

#### 3. Récupérer les catégories
```
GET /api/categories
```

#### 4. Récupérer les promotions
```
GET /api/promotions
```

#### 5. Vérifier la santé de l'API
```
GET /api/health
```

---

## 🎨 Personnalisation

### Changer les couleurs

Dans `App.css`, modifie les variables CSS :

```css
:root {
  --color-primary: #0052CC;        /* Bleu principal */
  --color-primary-dark: #003A99;   /* Bleu foncé */
  --color-secondary: #E8F0FF;      /* Bleu clair */
  --color-background: #FAFBFC;     /* Fond */
  /* ... autres couleurs */
}
```

### Ajouter un logo

1. Place ton image dans `frontend/public/logo.png`
2. Modifie le composant `Header.jsx` :

```jsx
<div className="logo-section">
  <img src="/logo.png" alt="Pick A Bout" className="logo-img" />
  <p className="tagline">Votre boutique d'affiliation Voghion</p>
</div>
```

3. Ajoute les styles CSS :

```css
.logo-img {
  height: 50px;
  width: auto;
}
```

### Modifier le nombre de produits par page

1. Dans `server.js`, change `limit: 12` 
2. Dans le formulaire, change aussi `REACT_APP_PRODUCTS_PER_PAGE=12`

---

## 🐛 Dépannage

### Erreur : "Cannot find module 'express'"

**Solution** : Installe les dépendances
```bash
cd backend
npm install
```

### Erreur : "API_KEY not found"

**Solution** : Vérifie que ton `.env` contient :
```
AWIN_API_KEY=3e2cb2e4-9c34-482a-80a1-cea2b00f41b5
```

### Le frontend n'affiche pas les produits

**Solutions** :
1. Vérifie que le backend est lancé (`http://localhost:5000`)
2. Ouvre la console du navigateur (F12) pour voir les erreurs
3. Vérifie l'URL de l'API dans `.env`

### CORS Error

Si tu vois une erreur CORS :

**Solution** : Le backend inclut déjà `cors()`. Sinon, ajoute :
```javascript
const cors = require('cors');
app.use(cors());
```

---

## 🌍 Déploiement

### Déployer le Backend

**Option 1 : Heroku**
1. Crée un compte sur [heroku.com](https://heroku.com)
2. Installe Heroku CLI
3. Pousse ton code :
```bash
heroku login
heroku create pick-a-bout-api
git push heroku main
```

**Option 2 : Railway, Render, ou autre**
- Suis leur documentation spécifique
- Renseigne les variables d'environnement

### Déployer le Frontend

**Option 1 : Vercel (Recommandé)**
```bash
npm install -g vercel
vercel
```

**Option 2 : Netlify**
```bash
npm run build
# Glisse le dossier 'dist' sur Netlify
```

**Option 3 : GitHub Pages**
```bash
npm run build
# Pousse le dossier 'dist' sur gh-pages
```

---

## 📊 Suivi des ventes Awin

Toutes les ventes via les liens `clickUrl` des produits sont automatiquement trackées par Awin.

**Comment vérifier tes ventes** :
1. Va sur [awin.com](https://awin.com)
2. Connecte-toi avec ton compte
3. Accède à "Reports" ou "Performance"
4. Tu verras tes clics, conversions et commissions

---

## 💡 Conseils pour augmenter tes ventes

1. **Partage ton site** : Sur les réseaux sociaux, forums, blogs
2. **Écris des avis** : Crée des articles détaillés (si tu ajoutes le blog)
3. **Utilise les codes promo** : Mets en avant les codes Voghion
4. **Optimise pour SEO** : Utilise des mots-clés pertinents
5. **Mise en page** : Rends les appels à l'action (boutons) clairs et visibles

---

## 🔒 Sécurité

- **API Key** : Garde-la secrète ! Ne la commit pas sur GitHub
- **Environment variables** : Utilise `.env` et `.gitignore`
- **HTTPS** : Utilise HTTPS en production
- **CORS** : Restreins l'accès à ton domaine

---

## 📞 Support

### Awin
- Documentation : https://wiki.awin.com
- Support : support@awin.com
- API Docs : https://api.awin.com

### Voghion
- Contact : partner@voghion.sg
- Programme : https://www.awin.com

### Vite & React
- Docs Vite : https://vitejs.dev
- Docs React : https://react.dev

---

## 📝 Changelog

### v1.0.0 (Initial Release)
- ✅ Catalogue complet des produits Voghion
- ✅ Intégration API Awin
- ✅ Design bleu professionnel
- ✅ Responsive design
- ✅ Promotions affichées
- ✅ Documentation complète

---

## 📄 Licence

Ce projet est sous licence MIT. Libre d'utilisation et de modification.

---

**Créé pour Pick A Bout | Votre plateforme d'affiliation Voghion** 🎉

Besoin d'aide ? Contacte Awin ou Voghion directement !
