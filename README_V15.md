# SONOR V15 — Google + achats automatiques

## Installation Render
1. Déployer ce ZIP sur le service web Node existant (commande `npm start`).
2. Créer une base PostgreSQL persistante (Render Postgres ou autre), copier son URL dans `DATABASE_URL`.
3. Google Cloud Console > APIs et services > Identifiants > Créer ID client OAuth (application Web). Ajouter `https://sonoria-zmho.onrender.com` aux **origines JavaScript autorisées**. Copier l'ID dans `GOOGLE_CLIENT_ID`.
4. Stripe > Développeurs > Webhooks : ajouter `https://sonoria-zmho.onrender.com/api/stripe/webhook` avec événements `checkout.session.completed` et `checkout.session.async_payment_succeeded`. Copier le secret de signature `whsec_...` dans `STRIPE_WEBHOOK_SECRET`.
5. Dans Render > Environment, renseigner les six variables de `.env.example` et redéployer. Ne jamais mettre `sk_live_` ou `whsec_` dans les fichiers publics.
6. Tester d'abord avec les clés Stripe TEST et les cartes de test. Puis basculer ensemble clés et webhook en LIVE.

## Fonctionnement
Connexion Google vérifiée côté serveur, cookie HttpOnly signé. L'achat ouvre une session Stripe Checkout créée par le serveur avec l'identifiant du compte Google dans les métadonnées. Le webhook vérifie la signature Stripe et la somme payée avant d'enregistrer le pack en PostgreSQL. Les droits sont chargés par `/api/me` et revérifiés côté serveur au moment de rejoindre un salon. La confirmation affichée dans l'URL ne débloque rien.

## Important
Les anciens liens de paiement Stripe créés manuellement ne sont pas utilisés par cette version : ils n'associent pas automatiquement le paiement au compte Google. Un achat réalisé via ces anciens liens ne sera pas attribué automatiquement. L'URL `PUBLIC_URL` doit correspondre au domaine réel.

## Sécurité et limites
Le pseudo en salon reste libre; l'authentification Google n'est requise que pour les achats. Les sessions signées expirent après 7 jours; changer `SESSION_SECRET` déconnecte les joueurs. Ne pas supprimer la base PostgreSQL. Prévoir une politique de confidentialité, les informations légales de vente et le traitement des remboursements avant commercialisation. Le code ne révoque pas encore automatiquement les packs après remboursement.
