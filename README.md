# Custom Recovery Page for Supabase

Ce projet héberge une page de récupération de mot de passe personnalisée pour Supabase, hébergée via GitHub Pages.

## URL de la Page
**URL hébergée :** `https://multibrasservices.github.io/email_recovery/`

## Configuration Supabase (sur Coolify)

Pour configurer votre instance Supabase afin qu'elle utilise cette page personnalisée pour les emails de récupération, ajoutez la variable d'environnement suivante dans votre configuration Coolify :

```env
MAILER_TEMPLATES_RECOVERY=https://multibrasservices.github.io/email_recovery/
```

### Notes
- Cette configuration force Supabase à rediriger l'utilisateur vers cette URL spécifique lors du clic sur le lien de récupération dans l'email.
- Les fichiers `go_true.md` et `mdp_oublié.md` présents dans ce dossier contiennent des détails supplémentaires sur le fonctionnement interne et le débogage si nécessaire.
