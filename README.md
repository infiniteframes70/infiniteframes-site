# Infiniteframes — site public

Site statique public pour `infiniteframes.fr`, destiné à présenter le projet Infiniteframes et l'outil privé Faceless Pipeline, ainsi qu'à publier les informations de confidentialité et les conditions d'utilisation liées à l'intégration YouTube.

## Fichiers

- `index.html` : page d'accueil et présentation de l'application.
- `privacy/index.html` : politique de confidentialité.
- `terms/index.html` : conditions d'utilisation.
- `assets/style.css` : styles responsives partagés.
- `CNAME` : domaine personnalisé GitHub Pages (`infiniteframes.fr`).
- `.nojekyll` : désactive le traitement Jekyll par défaut.

## Publication GitHub Pages

1. Dans les paramètres du dépôt, ouvrir **Pages**.
2. Choisir **Deploy from a branch**, branche `main`, dossier `/ (root)`.
3. Enregistrer et attendre que le site soit publié sur l'URL GitHub Pages.
4. Vérifier que le site est public et que les liens `/privacy/` et `/terms/` fonctionnent.
5. Ajouter `infiniteframes.fr` dans **Settings → Pages → Custom domain** si GitHub ne le détecte pas déjà depuis `CNAME`.
6. Configurer les enregistrements DNS GitHub Pages chez Infomaniak, après avoir enregistré le domaine personnalisé dans GitHub.
7. Activer **Enforce HTTPS** lorsque le certificat est disponible.

## Domaine personnalisé et DNS

Avant d'ajouter les enregistrements DNS :

1. Dans les paramètres du compte GitHub `infiniteframes70`, ouvrir **Settings → Pages → Add a domain** et vérifier le domaine. GitHub fournit un enregistrement TXT de vérification propre au compte ; l'ajouter dans Infomaniak avant d'utiliser le domaine sur GitHub Pages.
2. Dans les paramètres du dépôt, **Settings → Pages**, saisir `infiniteframes.fr` dans **Custom domain** et enregistrer.
3. Créer ensuite les enregistrements DNS de GitHub Pages ci-dessous.

À créer chez Infomaniak pour l'hôte `@` :

- `A` → `185.199.108.153`
- `A` → `185.199.109.153`
- `A` → `185.199.110.153`
- `A` → `185.199.111.153`

Un `CNAME` facultatif pour `www` peut pointer `www` vers `infiniteframes70.github.io.` si le sous-domaine `www.infiniteframes.fr` est également configuré dans GitHub Pages. Le site utilise pour l'instant le domaine racine uniquement. Ne pas créer de wildcard DNS.

Conserver les enregistrements NS et le TXT `google-site-verification` déjà en place. Ajouter également le TXT de vérification GitHub Pages fourni dans les paramètres du compte GitHub ; ne pas inventer sa valeur. Les enregistrements MX/SPF/DMARC existants ne sont pas modifiés par ces instructions.

## Vérifications avant demande de vérification Google

- Vérifier que l'adresse de contact `infiniteframes70@gmail.com` est bien l'adresse que l'éditeur souhaite rendre publique.
- Vérifier le contenu de la politique de confidentialité par rapport au fonctionnement réellement déployé de Faceless Pipeline et aux prestataires effectivement activés.
- Vérifier que la page d'accueil décrit bien l'application utilisée dans l'écran de consentement OAuth.
- Dans Google Auth Platform → Branding, utiliser exactement :
  - Homepage : `https://infiniteframes.fr/`
  - Privacy policy : `https://infiniteframes.fr/privacy/`
  - Terms of service : `https://infiniteframes.fr/terms/`
  - Authorized domain : `infiniteframes.fr`

## Sécurité

Ce dépôt ne doit contenir aucun jeton OAuth, fichier `client_secret*.json`, mot de passe, clé API, base de données, fichier `.env`, fichier média privé ou donnée issue du serveur de production.
