
---

## 🚀 Déploiement (AWS Amplify)
1. Push du code sur GitHub (`main`)
2. AWS Amplify → **New app** → **Host web app**
3. Connecter le repo GitHub + choisir la branche `main`
4. Lancer le build et récupérer l’URL publique

✅ Chaque `git push` déclenche automatiquement un nouveau déploiement.

---

## 🔐 Authentification (Amazon Cognito)
Configuration typique :
- User Pool
- Email comme identifiant
- Hosted UI activé
- App client configuré (Client ID, callback URL, sign-out URL)

📌 Les pages `login.html` et `admin.html` utilisent le flux Cognito (redirections) pour sécuriser l’accès.

---

## 🧪 Démo / Tests
- Accès public : `index.html` → lecture posts
- Accès admin : clic “Admin” → redirection Cognito → retour sur dashboard

---

## 📌 Notes importantes
- Ne pas exposer de secrets dans le repo.
- Si tu changes le domaine Amplify, pense à mettre à jour les **Callback URLs / Sign-out URLs** dans Cognito.

---

## 👤 Auteur
**Jean Christophe Désiré Bogbé**  
PFB CEDITECH 

---

## ✅ Licence
Projet éducatif / démonstration (PFE).
