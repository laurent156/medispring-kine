# Medispring · page kinésithérapeutes

Nouvelle version de la page [medispring.be/kinesitherapeutes](https://www.medispring.be/kinesitherapeutes), construite avec le design system Medispring, prête à intégrer dans Odoo.

## Contenu

| Fichier | Rôle |
| --- | --- |
| `kine-odoo.html` | Le code à coller dans un bloc « Code intégré » d'Odoo. Ne charge pas de police : Omnes Pro et Asap viennent du site. |
| `kine-apercu.html` | Aperçu de la page hors d'Odoo, avec les polices et les images. À ne pas coller dans Odoo. |
| `images/` | Les 7 images de la page, à importer dans la médiathèque d'Odoo. |
| `fonts/` | Omnes Pro Bold et Medium, utilisées uniquement par l'aperçu. |

## Voir l'aperçu

Le dépôt est privé : GitHub n'affiche pas la page, seulement son code. Pour la voir :

1. Télécharger le dépôt (bouton **Code**, puis **Download ZIP**) et le décompresser.
2. Dans le dossier, lancer un petit serveur local, puis ouvrir `http://localhost:8765/kine-apercu.html` :

```bash
python3 -m http.server 8765
```

Ouvrir `kine-apercu.html` par un double-clic marche aussi, mais certains navigateurs bloquent alors les polices.

## Intégrer dans Odoo

1. Importer les 7 fichiers de `images/` dans la médiathèque d'Odoo, puis remplacer chaque `images/xxx` de `kine-odoo.html` par l'URL Odoo.
2. Coller `kine-odoo.html` dans un bloc « Code intégré » réglé sur **pleine largeur**.
3. Créer la page de remerciement `/merci-demande-kine`.
4. Tester les deux formulaires avec un faux lead (voir ci-dessous).

Le menu et le pied de page restent ceux d'Odoo.

## Formulaires et CRM

Deux options pour relier le formulaire du hero au CRM Odoo :

- **Bloc « Formulaire » natif d'Odoo** (recommandé) : réglé sur « Créer une opportunité », placé dans une colonne à droite du hero. Pas de développement, Odoo gère l'envoi et la sécurité.
- **Formulaire codé dans la page** : il reprend la structure du formulaire Odoo actuel (envoi vers `/website/form/`, lead dans le CRM). À tester : selon la version d'Odoo, le code intégré peut empêcher l'envoi. Les champs personnalisés (N° INAMI) doivent être autorisés pour les formulaires du site.

Le calculateur de prix reste le Typeform existant ; ses réponses arrivent par e-mail dans le CRM.

## Animations

Fondu discret à l'apparition des sections (petit script en bas de `kine-odoo.html`). Sans le script, tout reste visible. Désactivé si le visiteur a choisi de réduire les animations.
