# 🔥 Configurar Firebase — PropInvest Pro

## Passo 1 — Criar projecto Firebase (grátis)
1. Vai a https://console.firebase.google.com
2. Clica "Criar um projecto"
3. Dá um nome (ex: `propinvest-pro`) e clica em Continuar
4. Desactiva Google Analytics (opcional) → Criar projecto

## Passo 2 — Registar a Web App
1. No painel do projecto clica no ícone **</>** (Web)
2. Dá um nome (ex: `PropInvest Web`) → Registar app
3. Copia o objecto `firebaseConfig` que aparece:
```js
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "propinvest-xxx.firebaseapp.com",
  projectId: "propinvest-xxx",
  storageBucket: "propinvest-xxx.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123:web:abc123"
};
```

## Passo 3 — Activar Authentication
1. No menu esquerdo → **Authentication** → Começar
2. Aba **Sign-in method** → Activar:
   - ✅ **Email/Password**
   - ✅ **Google** (escolhe email de suporte)

## Passo 4 — Activar Firestore
1. No menu → **Firestore Database** → Criar base de dados
2. Escolhe **Modo de produção** → Seguinte
3. Escolhe a região mais próxima (ex: `europe-west1`) → Activar

## Passo 5 — Configurar Regras Firestore
1. Firestore → aba **Regras** → Cola isto e publica:
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

## Passo 6 — Colocar config no index.html
Abre o `index.html` e procura (linha ~400):
```js
const FIREBASE_CONFIG = {
  apiKey:            "SUBSTITUI_AQUI",
  ...
```
Substitui cada campo pelos valores do teu projecto.

## Passo 7 — Deploy no Netlify
Faz upload da pasta para o Netlify normalmente.

## ✅ Resultado
- Login com email/password ou Google
- Dados sincronizam automaticamente entre todos os dispositivos
- Funciona offline (dados em cache local)
- Cada utilizador vê só os seus próprios projetos
