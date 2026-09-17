# MY ID CAMEROUN — dossier de production

Ce dossier contient les 2 premières pages réelles du site (pas juste des maquettes) :

- `index.html` — la page d'accueil
- `connexion.html` — connexion / inscription (relié à Firebase my-id-cameroun-8002f)
- `tableau-de-bord.html` — l'espace personnel de chaque utilisateur connecté
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

## Important : activer Firestore

Les profils utilisateurs sont enregistrés dans Firestore. Dans la Console
Firebase → **Firestore Database** → **Créer une base de données** → mode
**production** → choisis une région (europe-west par exemple). Sans cette
étape, la connexion fonctionne mais le profil n'est pas sauvegardé.

## Ce qui reste à construire

- Page "Déclarer un document perdu"
- Page "Déclarer un document trouvé"
- Page "Rechercher un document"
- Tableau de bord "Mes déclarations"
- Espace Admin
- Connexion à Supabase (stockage des déclarations, photos)
- OCR (Google Gemini), paiement (IkePay), SMS

On avance une page à la fois — dis-moi laquelle tu veux ensuite.
