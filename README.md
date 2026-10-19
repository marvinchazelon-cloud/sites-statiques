# Sites vitrines (monorepo)

Sites vitrines statiques — HTML/CSS pur, déployés automatiquement vers LWS (France) via GitHub Actions.

## Structure

- `sites/<nom-site>/` : 1 dossier = 1 site = 1 domaine (`index.html`, `style.css`, assets)
- `sites.json` : config de déploiement par site (host, port, user SSH LWS, deploy_dir)
- `.github/workflows/deploy.yml` : à chaque push sur `main`, déploie uniquement les sites modifiés

## Secret GitHub requis (un seul)

- `LWS_SSH_KEY` : clé privée de déploiement (sa clé publique est ajoutée au `authorized_keys` de chaque compte SSH LWS)

## Ajouter un site

1. Créer `sites/<nom-site>/` avec `index.html` + `style.css`
2. Ajouter l'entrée dans `sites.json`
3. Ajouter la clé publique de déploiement au `authorized_keys` du compte SSH LWS du domaine
4. Vérifier : domaine rattaché à son dossier chez LWS + SSL Let's Encrypt activé

## Déploiement manuel

Onglet Actions → "Deploy vitrines to LWS" → Run workflow → nom du site (ou vide pour détection auto).
