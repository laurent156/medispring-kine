# Medispring · page kinésithérapeutes

Nouvelle version de la page [medispring.be/kinesitherapeutes](https://www.medispring.be/kinesitherapeutes), construite avec le design system Medispring, prête à intégrer dans Odoo.

## Contenu

| Fichier | Rôle |
| --- | --- |
| `kine-odoo.html` | Version FR : le code à coller dans un bloc « Code intégré » d'Odoo. Ne charge pas de police : Omnes Pro et Asap viennent du site. |
| `kine-odoo-nl.html` | Version NL (textes relus par Medispring) : même page, à coller dans un second bloc « Code intégré ». |
| `kine-apercu.html`, `kine-apercu-nl.html` | Aperçus FR et NL hors d'Odoo, avec les polices et les images. À ne pas coller dans Odoo. |
| `images/` | Les 7 images de la page (originaux). Elles sont déjà dans la médiathèque d'Odoo : les codes `kine-odoo*.html` pointent vers les adresses `/web/image/…` ; les aperçus utilisent ces fichiers. |
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

1. Les images sont déjà dans la médiathèque d'Odoo (liste en bas de `kine-odoo.html`) : rien à faire.
2. Coller `kine-odoo.html` dans un bloc « Code intégré » réglé sur **pleine largeur**.
3. Ajouter un second bloc « Code intégré » avec `kine-odoo-nl.html`, juste en dessous. Chaque bloc se masque tout seul dans l'autre langue : aucun réglage de visibilité à faire. Mettre les marges des deux blocs à 0.
4. Tester les formulaires avec un faux lead, en FR et en NL (voir ci-dessous).

Le menu et le pied de page restent ceux d'Odoo.

## Formulaires et CRM

Deux options pour relier le formulaire du hero au CRM Odoo :

- **Bloc « Formulaire » natif d'Odoo** (recommandé) : réglé sur « Créer une opportunité », placé dans une colonne à droite du hero. Pas de développement, Odoo gère l'envoi et la sécurité.
- **Formulaire codé dans la page** : il reprend la structure du formulaire Odoo actuel (envoi vers `/website/form/`, lead dans le CRM). À tester : selon la version d'Odoo, le code intégré peut empêcher l'envoi. Les champs personnalisés (N° INAMI) doivent être autorisés pour les formulaires du site.

Le calculateur de prix est le Typeform « Calculateur web Medispring - kinés » (intégration live) ; ses réponses arrivent par e-mail dans le CRM. Le guide « Cap sur 2027 » reprend le formulaire e-mail existant. La section vidéo intègre la vidéo YouTube « Découvrez Medispring Physio » (FR ; la version NL utilise provisoirement « Eén patiëntendossier, één multidisciplinair team ») (lecteur youtube-nocookie, sans cookie avant la lecture).

Formulaire du hero : après l'envoi, Odoo remplace le formulaire par un message de confirmation (pas de page de remerciement à créer). Formulaire du guide : redirection vers la page existante `/merci-guide-kine-2027`.

## Français et néerlandais

Odoo ne traduit pas le contenu d'un bloc « Code intégré » : la page contient donc deux blocs, chacun visible dans une seule langue. Le masquage est dans le code (règle CSS sur la langue de la page, comme l'option Visibilité > Langues d'Odoo) ; en mode édition, les deux blocs restent visibles. Les ancres et les identifiants de la version NL finissent par `-nl` pour éviter les doublons. Les points marqués « NL À CONFIRMER » dans `kine-odoo-nl.html` attendent une réponse de Medispring (Typeform, lien Q&A, page de remerciement du guide, vidéo kiné NL). La vidéo NL est intégrée..

## Suivi des conversions (Plausible)

Le site utilise Plausible. Quand le message de confirmation d'un formulaire s'affiche, le code envoie l'événement **« Lead kiné »**, avec trois détails : `formulaire` (conseiller ou guide), `demande` (rappel ou demo) et `langue` (fr ou nl). Dans Plausible, créer un objectif de type *Custom event* nommé exactement `Lead kiné`. Pour filtrer par détail, les propriétés personnalisées doivent être disponibles dans l'abonnement Plausible. Le formulaire du guide redirige vers une page : tant qu'il n'est pas passé en message, on le suit par la visite de cette page.

## Animations

Fondu discret à l'apparition des sections (petit script en bas de `kine-odoo.html`). Sans le script, tout reste visible. Désactivé si le visiteur a choisi de réduire les animations.
