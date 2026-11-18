# SONOR V9 — Neon Session

Nouvelle direction artistique violet nocturne, animations d'ambiance, particules, vinyle, cartes interactives, indicateur de progression des manches, écrans de jeu modernisés et accessibilité mouvement réduit.

## Déployer sur Render
- Dépôt GitHub avec `package.json`, `server.js` et `public/` à la racine.
- Runtime: Node
- Build Command: `npm install`
- Start Command: `npm start`
- Branch: la branche existante du dépôt (`main` ou `master`).

## Local
`npm install` puis `npm start` et ouvrir `http://localhost:3000`.

## Remarques
Le jeu reste basé sur Socket.IO. Les salons en mémoire ne survivent pas à un redémarrage. La lecture YouTube peut être bloquée par certaines restrictions navigateur ou vidéo. La musique d'ambiance s'active après interaction de l'utilisateur.


V10: interface en français, anglais, espagnol et chinois simplifié. Sélecteur de langue dans l’en-tête; préférence enregistrée dans le navigateur. Les situations écrites par les joueurs et les vidéos YouTube ne sont pas traduites automatiquement.


## Pack Footballeurs (1,99 $)
10 images dans `public/assets/avatar-foot01.webp` à `avatar-foot10.webp`.
Les 10 avatars sont affichés verrouillés dans le sélecteur. L'achat est une présentation uniquement : **aucun paiement n'est prélevé**, aucun déblocage n'est simulé.
Pour commercialiser le pack : ajouter une authentification utilisateur, un prestataire de paiement (Stripe Checkout par exemple), un webhook de confirmation validé côté serveur, un stockage persistant des droits d'accès et mettre à jour la validation des avatars dans `server.js`. Ne pas utiliser localStorage comme preuve d'achat.


## Pack YouTubeurs FR (1,99 $)
10 images avatar-youtube01.webp à avatar-youtube10.webp, affichées assombries avec cadenas dans le sélecteur. Paiement non configuré, aucun déblocage fictif. Une authentification, une validation serveur et un webhook de paiement sont nécessaires avant commercialisation.


## V13 — Refonte visuelle premium
- Ambiance club nocturne violet / or avec halos et profondeur.
- Hero, vinyle, boutons, cartes et espaces de jeu modernisés.
- Sélecteur d’avatars et packs premium harmonisés.
- Responsive mobile, focus clavier et respect du mouvement réduit.
- Aucun changement au fonctionnement des salons, des packs ou des paiements (non intégrés).
