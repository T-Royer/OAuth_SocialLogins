# TP OAuth + JWT - Template

**BUT Informatique S4 - Module R401**

## Objectif du TP

Implémenter **Google OAuth 2.0** dans une application Vue.js + Express déjà fonctionnelle avec authentification JWT classique (email/password).

### **TODO 1** : Configuration Passport Google Strategy
**Fichier** : \`backend/config/passport.js\`

Implémenter la stratégie Google OAuth 2.0 avec :
- clientID, clientSecret, callbackURL depuis .env
- Option passReqToCallback: true
- Callback async qui cherche/crée l'utilisateur

### **TODO 2** : Routes OAuth Google
**Fichier** : \`backend/routes/auth.js\`

Créer 2 routes :
1. **GET /google** : Initie l'authentification Google
2. **GET /google/callback** : Reçoit le callback, génère JWT, redirige


### **TODO 3** : Ajout de nouveaux Social Sign-in
Étendre l’application pour supporter 2 autres Social Sign-In (au choix) parmi :

    GitHub
    Discord
    Facebook
    Twitter / X
    Microsoft

---

## Installation

### Backend

\`\`\`bash
cd backend
npm install
cp .env.example .env
# Éditez .env avec vos Google credentials
\`\`\`

### Frontend

\`\`\`bash
cd frontend
npm install
cp .env.example .env
\`\`\`

---

## Configuration Google Cloud Console

1. Créer un projet sur [Google Cloud Console](https://console.cloud.google.com/)
2. API et services → Écran de consentement OAuth → Type: Externe
3. Ajouter votre email dans Utilisateurs test
4. Créer des identifiants OAuth 2.0:
   - **Origines JavaScript**: http://localhost:3000, http://localhost:5173
   - **URI de redirection**: http://localhost:3000/auth/google/callback
5. Activer l'API People
6. Copier Client ID et Secret dans backend/.env

---

## Lancer l'application

\`\`\`bash
# Terminal 1 - MongoDB
Lancer MongoDB

# Terminal 2 - Backend
cd backend && npm install && npm run dev

# Terminal 3 - Frontend
cd frontend && npm install && npm run dev
\`\`\`

Frontend: http://localhost:5173  
Backend: http://localhost:3000

## Ressources

- [Passport Google OAuth](https://www.passportjs.org/packages/passport-google-oauth20/)
- Slides du cours: slides/oauth-google-nodejs-jwt.html (Slides 21, 23, 18)

---

## Debugging

| Erreur | Solution |
|--------|----------|
| redirect_uri_mismatch | Vérifier URL callback dans Google Cloud Console |
| Access blocked | Ajouter email dans Utilisateurs test |
| Cannot find module | npm install dans backend |


