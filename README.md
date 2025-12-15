# BlueNotes
Un mini-projet **PFE CEDITECH** : blog statique + **accès Admin sécurisé** via **Amazon Cognito (Hosted UI)**, déployé en ligne sur **AWS Amplify** avec un pipeline **CI/CD GitHub → Amplify**.

---

## Objectif du projet
- Publier un blog accessible au public (lecture).
- Protéger la partie **Admin** (dashboard/gestion) via une authentification Cognito.
- Déployer et mettre à jour automatiquement l’application via GitHub (workflow “entreprise”).

---

##  Fonctionnalités
### Côté public
- Landing page + liste des articles
- Lecture d’un article (page dédiée)

### Côté admin
- Connexion via **Cognito Hosted UI**
- Accès au dashboard Admin après authentification
- (Optionnel) actions CRUD “simples” pour gérer les posts (selon ta version)

---

##  Architecture (simple)
**Utilisateur (navigateur)** → **AWS Amplify (hosting)**  
**Admin** → **Cognito Hosted UI** → redirection vers **admin.html**  
**GitHub** → (push) → **Amplify build & deploy**

---

##  Stack / Outils
- **Frontend** : HTML / CSS / JavaScript (vanilla) + Tailwind CDN
- **Auth** : Amazon Cognito (User Pool + Hosted UI)
- **CI/CD & Déploiement** : GitHub + AWS Amplify
- **Monitoring (optionnel)** : CloudWatch Logs

---

## Structure du projet
bluenotes/
├─ index.html # page d’accueil + liste des articles
├─ post.html # lecture d’un article (page “mode lecture”)
├─ admin.html # dashboard admin (protégé par Cognito)
├─ login.html # page de login/redirect vers Cognito
└─ README.md
---

##  Déploiement (AWS Amplify)
1. Push du code sur GitHub (`main`)
2. AWS Amplify → **New app** → **Host web app**
3. Connecter le repo GitHub + choisir la branche `main`
4. Lancer le build et récupérer l’URL publique

✅ Chaque `git push` déclenche automatiquement un nouveau déploiement.

---

##  Authentification (Amazon Cognito)
Configuration typique :
- User Pool
- Email comme identifiant
- Hosted UI activé
- App client configuré (Client ID, callback URL, sign-out URL)

📌 Les pages `login.html` et `admin.html` utilisent le flux Cognito (redirections) pour sécuriser l’accès.

---

##  Démo / Tests
- Accès public : `index.html` → lecture posts
- Accès admin : clic “Admin” → redirection Cognito → retour sur dashboard

---

## Notes importantes
- Ne pas exposer de secrets dans le repo.
- Si tu changes le domaine Amplify, pense à mettre à jour les **Callback URLs / Sign-out URLs** dans Cognito.

---

##  Auteur
**Jean Christophe Désiré Bogbé**  
PFB CEDITECH 

---

## ✅ Licence
Projet éducatif / démonstration (PFE).
