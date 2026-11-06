# Grayali up

Ton repas de midi, livré à ta salle. Site : https://fadi2811.github.io/UPBchop-/

Site statique hébergé sur GitHub Pages. Les commandes partent sur WhatsApp, le paiement se fait par Wave, et le stock, les commandes et les points sont gérés dans un Google Sheet via Google Apps Script.

## Fichiers

| Fichier | Rôle |
|---|---|
| `index.html` | Le site client : plats, panier, commande WhatsApp, points, boutique |
| `admin.html` | Tableau de bord (mot de passe) : commandes, stock, plat du jour, points, cadeaux |
| `mentions.html` | Mentions et données personnelles |
| `images/` | Photos des plats (WebP, 480 px) |
| `icon*.png`, `icon.svg`, `apple-touch-icon.png`, `manifest.webmanifest` | Icônes et installation sur l’écran d’accueil |
| `preview.png` | Image affichée quand on partage le lien (WhatsApp, Facebook…) |

## Réglages rapides (en haut du `<script>` de `index.html`)

- `WA` : ton numéro WhatsApp au format international, sans `+`.
- `STOCK_URL` : adresse du Google Apps Script.
- `LIV_OPEN` : `false` pour fermer la livraison.
- `SHOP_OPEN` : `true` pour ouvrir la boutique.
- `THEME_PICKER` : `false` pour cacher le choix de couleur une fois ta couleur choisie.
- `TODAY_END` : heure limite des commandes du jour (en minutes, `11*60+30` = 11h30).
- `TODAY_ON` : `false` pour n’accepter que les commandes pour le lendemain.
- `CLOSED_DAYS` : jours sans livraison, ex. `["2026-12-25","2027-01-01"]`.
- `PJ_NAME` : plat du jour par défaut (le tableau de bord peut le changer).

## Ajouter ou changer un plat

1. Mets la photo (carrée, environ 480 × 480) dans `images/`, de préférence en `.webp`.
2. Ajoute-la dans `PH` : `nom:"images/nom.webp"`.
3. Ajoute le plat dans `PLACES` : `{n:"Nom du plat",p:1100,st:15,e:"",img:PH.nom}`.

Attention : le stock en direct utilise la **position** du plat dans la liste (`t0`, `t1`… et `d0`, `d1`…). Ajoute les nouveaux plats **à la fin** pour ne pas mélanger les stocks du tableau Google.

## Numéros de téléphone

Le site envoie toujours le numéro au format `0500000000` (10 chiffres, sans espace ni `+225`), pour que les points d’un même client soient toujours comptés ensemble.
