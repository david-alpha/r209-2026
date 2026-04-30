# TD 1 — Mise en place de l'environnement de développement

**Formation :** Application Kanban — Développement web full-stack
**Durée :** 1h30
**Niveau :** Débutant
**Pré-requis :** Aucun (un ordinateur, une connexion internet, une adresse e-mail)

---

## Objectifs pédagogiques

À l'issue de ce TD, l'étudiant sera capable de :

1. Créer et configurer un compte **GitHub**, **Supabase** et **Vercel**.
2. Installer les outils de base (Node.js, Git, VS Code) sur sa machine.
3. Initialiser un projet **React** minimal et le pousser sur un dépôt distant.
4. Déployer ce projet en ligne via **Vercel** et vérifier qu'il fonctionne.

> **Contexte du parcours :** Ce TD pose les fondations techniques. Lors des prochaines séances, vous construirez progressivement une application **Kanban** (gestion de tâches type Trello) reliée à une base de données. Ne sautez aucune étape — un environnement mal configuré aujourd'hui = des heures perdues plus tard.

---

## Déroulé prévisionnel

| Étape | Durée | Activité |
|---|---|---|
| 1 | 10 min | Installation des outils locaux |
| 2 | 15 min | Création des comptes GitHub, Supabase, Vercel |
| 3 | 20 min | Initialisation du projet React |
| 4 | 15 min | Push du projet sur GitHub |
| 5 | 15 min | Déploiement sur Vercel |
| 6 | 10 min | Vérifications & livrable |
| Marge | 5 min | Questions / dépannage |

---

## Étape 1 — Installer les outils locaux *(10 min)*

Avant tout, installez ces trois logiciels gratuits sur votre machine.

### 1.1 Node.js (avec npm)

Node.js permet d'exécuter du JavaScript hors d'un navigateur. `npm` (installé avec) sert à gérer les bibliothèques.

- Rendez-vous sur **https://nodejs.org/**
- Téléchargez la version **LTS** (Long Term Support).
- Installez en gardant les options par défaut.

**Vérification dans un terminal :**

```bash
node --version
npm --version
```

Vous devez obtenir deux numéros de version (ex : `v20.x.x` et `10.x.x`).

### 1.2 Git

Git est l'outil de versioning. Il enregistre l'historique de votre code.

- Téléchargez sur **https://git-scm.com/downloads**
- Installez avec les options par défaut.

**Vérification :**

```bash
git --version
```

### 1.3 Visual Studio Code

C'est l'éditeur de code que nous utiliserons.

- Téléchargez sur **https://code.visualstudio.com/**
- Installez normalement.

> 💡 **Astuce :** Pendant l'installation de VS Code (Windows), cochez les cases « Ajouter au PATH » et « Ouvrir avec Code » dans le menu contextuel.

---

## Étape 2 — Créer les trois comptes *(15 min)*

### 2.1 Compte GitHub *(5 min)*

GitHub héberge le code source en ligne. C'est aussi votre vitrine professionnelle.

1. Allez sur **https://github.com/**
2. Cliquez sur **Sign up**.
3. Renseignez votre **e-mail** *(privilégiez votre adresse étudiante ou personnelle pérenne)*.
4. Choisissez un **nom d'utilisateur** professionnel — il apparaîtra dans toutes vos URLs publiques.
   - ✅ Bon : `marie-dupont`, `mdupont-dev`
   - ❌ À éviter : `xX_Marie_Xx`, `coolgirl2025`
5. Validez l'e-mail reçu.

**Configuration de Git en local** *(à faire une seule fois sur votre machine)* :

```bash
git config --global user.name "Votre Nom"
git config --global user.email "votre-email@exemple.com"
```

Utilisez **le même e-mail** que celui de GitHub.

### 2.2 Compte Supabase *(5 min)*

Supabase est notre future base de données (PostgreSQL hébergé) avec authentification intégrée. Nous l'utiliserons à partir du TD 3.

1. Allez sur **https://supabase.com/**
2. Cliquez sur **Start your project**.
3. **Connectez-vous avec votre compte GitHub** *(plus simple, pas de mot de passe à retenir).*
4. Acceptez les autorisations demandées.

> ℹ️ Pas besoin de créer de projet Supabase aujourd'hui — uniquement le compte. Nous créerons un projet « Kanban » lors du TD 3.

### 2.3 Compte Vercel *(5 min)*

Vercel héberge et déploie automatiquement les applications React/Next.js. Chaque fois que vous pousserez du code sur GitHub, Vercel mettra à jour le site en ligne.

1. Allez sur **https://vercel.com/**
2. Cliquez sur **Sign Up**.
3. **Choisissez "Continue with GitHub"** *(c'est essentiel pour la suite).*
4. Autorisez Vercel à accéder à vos dépôts GitHub.
5. Choisissez le plan **Hobby** (gratuit) quand on vous le propose.

---

## Étape 3 — Créer le projet React *(20 min)*

Nous allons créer une application React minimale avec **Vite** *(plus rapide et moderne que Create React App).*

### 3.1 Ouvrir un terminal au bon endroit

Choisissez un dossier sur votre machine pour vos projets de cours, par exemple `Documents/cours-kanban`.

```bash
cd Documents
mkdir cours-kanban
cd cours-kanban
```

### 3.2 Créer le projet avec Vite

```bash
npm create vite@latest mon-kanban -- --template react
```

À chaque prompt, validez par défaut.

Puis :

```bash
cd mon-kanban
npm install
```

`npm install` télécharge toutes les dépendances *(le dossier `node_modules` est créé — il est volumineux mais normal).*

### 3.3 Lancer le serveur de développement

```bash
npm run dev
```

Vous devez voir un message du type :

```
VITE v5.x.x  ready in 423 ms

➜  Local:   http://localhost:5173/
```

Ouvrez **http://localhost:5173/** dans votre navigateur. Vous devez voir la page d'accueil React + Vite (logo qui tourne).

> 🛑 **Pour arrêter le serveur :** dans le terminal, faites `Ctrl + C`.

### 3.4 Personnaliser la page

Ouvrez le projet dans VS Code :

```bash
code .
```

Modifiez le fichier `src/App.jsx` — remplacez tout son contenu par :

```jsx
function App() {
  return (
    <div style={{ fontFamily: 'sans-serif', padding: '2rem', textAlign: 'center' }}>
      <h1>🚀 Mon premier déploiement</h1>
      <p>Projet réalisé par <strong>Prénom NOM</strong></p>
      <p>Future application : gestion de tâches Kanban</p>
    </div>
  );
}

export default App;
```

**Remplacez « Prénom NOM » par le vôtre.** Sauvegardez (`Ctrl + S`). La page se recharge automatiquement dans le navigateur.

---

## Étape 4 — Pousser le projet sur GitHub *(15 min)*

### 4.1 Initialiser Git localement

Vite a déjà initialisé un dépôt Git. Vérifiez avec :

```bash
git status
```

Si la commande dit `not a git repository`, lancez `git init`.

### 4.2 Créer un dépôt vide sur GitHub

1. Sur **github.com**, cliquez sur le bouton **+** en haut à droite → **New repository**.
2. Nom du dépôt : `mon-kanban`
3. **Laissez le dépôt vide** (ne cochez ni README, ni .gitignore, ni licence).
4. Cliquez **Create repository**.

GitHub affiche une page avec des commandes — gardez-la ouverte.

### 4.3 Premier commit et push

Dans le terminal, à la racine de `mon-kanban` :

```bash
git add .
git commit -m "Initialisation du projet Kanban"
git branch -M main
git remote add origin https://github.com/VOTRE-USERNAME/mon-kanban.git
git push -u origin main
```

> ⚠️ Remplacez `VOTRE-USERNAME` par votre vrai nom d'utilisateur GitHub.

Lors du `push`, GitHub peut vous demander de vous authentifier (token ou navigateur). Suivez les instructions.

**Vérification :** rafraîchissez la page du dépôt sur GitHub. Vous devez y voir tous les fichiers du projet.

---

## Étape 5 — Déployer sur Vercel *(15 min)*

### 5.1 Importer le projet

1. Connectez-vous sur **https://vercel.com/dashboard**
2. Cliquez sur **Add New...** → **Project**.
3. Dans la liste, trouvez le dépôt **`mon-kanban`** et cliquez sur **Import**.
4. Sur la page de configuration :
   - **Framework Preset** : Vite *(détecté automatiquement)*
   - Laissez tout le reste par défaut.
5. Cliquez sur **Deploy**.

Le déploiement prend 30 à 60 secondes. À la fin, vous obtenez une URL du type :

```
https://mon-kanban-abc123.vercel.app
```

**Cliquez sur l'URL** : votre site est en ligne, accessible depuis n'importe où dans le monde 🌍.

### 5.2 Vérifier le déploiement automatique

Pour confirmer que tout est bien câblé, modifiez votre projet local :

1. Dans `src/App.jsx`, changez `🚀 Mon premier déploiement` en `🚀 Déploiement automatique opérationnel`.
2. Dans le terminal :

```bash
git add .
git commit -m "Test du déploiement automatique"
git push
```

3. Retournez sur **vercel.com** → vous voyez un nouveau déploiement en cours.
4. Une fois terminé, rafraîchissez l'URL Vercel : la page est mise à jour ✅.

C'est ce qu'on appelle le **Continuous Deployment** : à chaque `git push`, Vercel reconstruit et publie le site.

---

## Étape 6 — Livrable de fin de séance *(10 min)*

Pour valider ce TD, déposez sur la plateforme de cours **un fichier texte ou e-mail** contenant :

1. ✅ L'**URL de votre dépôt GitHub** *(ex : github.com/marie-dupont/mon-kanban)*
2. ✅ L'**URL de votre site Vercel** *(ex : mon-kanban-abc123.vercel.app)*
3. ✅ Une **capture d'écran** de la page en ligne affichant votre nom.
4. ✅ La confirmation que vos comptes Supabase et Vercel sont bien créés *(une simple phrase suffit).*

---

## Dépannage — problèmes fréquents

| Problème | Solution |
|---|---|
| `command not found: npm` | Node.js n'est pas installé ou pas dans le PATH. Redémarrez le terminal après installation. |
| `Permission denied (publickey)` au push | Configurez l'authentification GitHub : **Settings → Developer settings → Personal access tokens** ou utilisez GitHub Desktop. |
| Le `npm install` est très long | C'est normal au premier lancement (plusieurs centaines de paquets). Patience — environ 1 à 3 minutes. |
| Vercel ne trouve pas mon dépôt | Allez dans **Vercel → Settings → Git → Manage GitHub App Installation** et autorisez le dépôt. |
| Page blanche sur Vercel | Vérifiez l'onglet **Deployments → Logs**. Souvent une erreur de syntaxe dans `App.jsx`. |
| Le site marche en local mais pas en ligne | Refaites un `git push` après avoir corrigé. Vercel redéploie automatiquement. |

---

## Pour aller plus loin *(optionnel, à la maison)*

- Personnalisez davantage votre page d'accueil (couleurs, image de profil).
- Explorez le tableau de bord Vercel : domaines personnalisés, variables d'environnement, analytics.
- Lisez la doc React officielle : **https://react.dev/learn**
- Faites un tour rapide sur **https://supabase.com/docs** pour anticiper le TD 3.

---

## Aperçu des prochaines séances

| TD | Thème |
|---|---|
| **TD 1** | Environnement & déploiement *(ce TD)* |
| TD 2 | Composants React & state — première version statique du Kanban |
| TD 3 | Connexion à Supabase — base de données et authentification |
| TD 4 | CRUD complet : créer, lire, modifier, supprimer des tâches |
| TD 5 | Drag & drop entre colonnes |
| TD 6 | Mise en production finale & soutenance |

---

*ARES FORMATION — 8 boulevard Jules FERRY — 42300 ROANNE*
*OF & CFA certifié Qualiopi — www.aresformation.com*
