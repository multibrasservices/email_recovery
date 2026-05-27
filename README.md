*version 27.05.26-1*

# Custom Recovery Page for Supabase

Ce projet héberge une page de récupération de mot de passe personnalisée pour Supabase, hébergée via GitHub Pages.

## URLs

| Template | URL | Usage |
|----------|-----|-------|
| Hardcodé (`saas.zoomali.io`) | `https://multibrasservices.github.io/email_recovery/` | Ancien projet — ne pas modifier |
| Dynamique (`{{ .RedirectTo }}`) | `https://multibrasservices.github.io/email_recovery/dynamic/` | Nouvelle infra multi-sites |

## Configuration Supabase (sur Coolify)

Pour une infra multi-sites, utiliser le template dynamique :

```env
MAILER_TEMPLATES_RECOVERY=https://multibrasservices.github.io/email_recovery/dynamic/
MAILER_TEMPLATES_CONFIRMATION=https://multibrasservices.github.io/email_recovery/dynamic/
MAILER_TEMPLATES_MAGIC_LINK=https://multibrasservices.github.io/email_recovery/dynamic/
MAILER_TEMPLATES_INVITE=https://multibrasservices.github.io/email_recovery/dynamic/
MAILER_TEMPLATES_EMAIL_CHANGE=https://multibrasservices.github.io/email_recovery/dynamic/
ADDITIONAL_REDIRECT_URLS=https://*.zoomali.io/**,https://*.zoomali.fr/**,https://*.multibrasservices.com/**
```

Chaque app doit passer `redirectTo` lors de l'appel SDK :

```ts
await supabase.auth.resetPasswordForEmail(email, {
  redirectTo: `${window.location.origin}/reset-password`,
})
```

### Notes
- Le template `/dynamic/` utilise `{{ .RedirectTo }}` — l'URL est injectée dynamiquement par GoTrue depuis le paramètre `redirectTo` de l'appel SDK.
- Le template `/` (racine) reste hardcodé sur `saas.zoomali.io` pour ne pas casser l'ancien projet.
