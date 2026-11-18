# SONORIA V17 — Discord uniquement

1. Remplace les fichiers du dépôt GitHub par ceux du ZIP (sans effacer les assets).
2. Dans Render > SONORIA-NEW > Environment, renseigne PUBLIC_URL, DISCORD_CLIENT_ID, DISCORD_CLIENT_SECRET, SESSION_SECRET, DATABASE_URL, STRIPE_SECRET_KEY et STRIPE_WEBHOOK_SECRET. Ne publie jamais les secrets sur GitHub.
3. Dans Discord Developer Portal > ton application > OAuth2 > Redirects, ajoute exactement `https://sonoria-new.onrender.com/api/auth/discord/callback`.
4. Dans Stripe > Webhooks, conserve `https://sonoria-new.onrender.com/api/stripe/webhook` et les événements `checkout.session.completed` et `checkout.session.async_payment_succeeded`.
5. Dans Render, clique sur Save, rebuild and deploy. Le GOOGLE_CLIENT_ID n'est plus requis.
6. Les visiteurs peuvent se connecter gratuitement avec Discord. Ils choisissent ensuite un pseudo et un avatar et cliquent sur « Enregistrer mon profil ». Le profil et les achats sont persistants dans PostgreSQL.
7. Le paiement utilise un Checkout Stripe créé côté serveur et le pack est activé uniquement après validation du webhook. Les anciens liens Stripe directs ne peuvent pas attribuer automatiquement un pack au compte Discord.

**Important :** Sans `DATABASE_URL`, la connexion Discord fonctionne mais l'enregistrement du profil et la boutique sont indisponibles. Les données existantes dans une ancienne base Google ne sont pas automatiquement migrées vers les identifiants Discord.
