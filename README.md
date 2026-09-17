# MY ID CAMEROUN — dossier de production

Ce dossier contient les 2 premières pages réelles du site (pas juste des maquettes) :

- `index.html` — la page d'accueil
- `connexion.html` — connexion / inscription (relié à Firebase my-id-cameroun-8002f)
- `tableau-de-bord.html` — l'espace personnel de chaque utilisateur connecté
- `mes-declarations.html`, `declarer.html`, `notifications.html`, `recherche.html`,
  `paiements.html`, `profil.html`, `aide.html`, `carte-qr.html`, `bureaux.html`
  — toutes les pages accessibles depuis le tableau de bord
- `favicon.png` / `favicon.ico` — l'icône du site (ton logo)

## Mettre le site en ligne (aucune compétence technique requise)

1. Va sur **vercel.com/drop**
2. Connecte-toi (ou crée un compte gratuit Vercel)
3. Glisse-dépose **tout ce dossier** (`myid-cameroun`) directement dans la page
4. Donne un nom au projet, clique sur **Deploy**
5. En quelques secondes, Vercel te donne une adresse en ligne du style
   `https://myid-cameroun.vercel.app` — c'est ton site, déjà accessible à tous.

## Avant de mettre en ligne, une chose à faire dans Firebase

Dans la Console Firebase (console.firebase.google.com) → ton projet →
**Authentication** → **Settings** → **Authorized domains** : ajoute l'adresse
`.vercel.app` que Vercel t'aura donnée. Sinon Firebase refusera les connexions
depuis ce nouveau nom de domaine.

## Important : activer Firestore + les bonnes règles

1. Console Firebase → **Firestore Database** → **Créer une base de données**
   → mode **production** → région europe-west (par exemple).
2. Une fois créée, va dans l'onglet **Règles** et remplace le contenu par :

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /profils/{uid} {
      allow read, write: if request.auth != null && request.auth.uid == uid;
    }
    match /declarations/{id} {
      allow read: if request.auth != null;
      allow create: if request.auth != null && request.resource.data.uid == request.auth.uid;
      allow update, delete: if request.auth != null && resource.data.uid == request.auth.uid;
    }
    match /notifications/{id} {
      allow read: if request.auth != null && resource.data.uid == request.auth.uid;
    }
  }
}
```

Clique sur **Publier**. Sans ces règles, les pages "Mes déclarations",
"Déclarer", "Rechercher" et "Notifications" afficheront un message
d'indisponibilité au lieu de fonctionner.

## Ce qui reste à construire

- Page "Déclarer un document perdu"
- Page "Déclarer un document trouvé"
- Page "Rechercher un document"
- Tableau de bord "Mes déclarations"
- Espace Admin
- Connexion à Supabase (stockage des déclarations, photos)
- OCR (Google Gemini), paiement (IkePay), SMS

On avance une page à la fois — dis-moi laquelle tu veux ensuite.
