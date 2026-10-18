# Site de l'AE-ECS : aeecs.ci (nom de domaine à confirmer)

Site de l'Association des Étudiants des Études Comptables Supérieures (ESCAE / INP-HB), construit sur la même base que le site de J-ECS. Les deux sites se renvoient l'un vers l'autre. Le site J-ECS est actuellement en ligne sur https://juniorecs.juniorecsentreprise.workers.dev/ ; une fois le site AE-ECS publié, renseigner son adresse dans l'admin de J-ECS (Informations générales > Adresse du site AE-ECS) pour afficher les liens.

## Ce que l'administrateur peut modifier (aeecs.ci/admin)

- **Nos activités** : les activités annuelles, chacune avec sa photo de couverture, ses photos et ses vidéos (liens YouTube ou Facebook). Un clic ouvre la galerie en plein écran. Photos : moins de 1 Mo chacune ; vidéos : passer par YouTube ou Facebook plutôt que d'envoyer des fichiers.
- **Agenda** : les événements datés. Ceux en cours ou à venir défilent dans la bannière « À l'affiche » en haut du site ; un événement en cours s'affiche aussi en « En ce moment ». Ils passent seuls dans « Passés » après leur date de fin.
- **Nos alumni** : diplômés mis en avant (photo, promotion, poste, message aux étudiants), avec leur accord.
- **Bureau** : mandat, membres, photos. La section reste masquée tant qu'elle est vide.
- **Formation ECS** : présentation, informations clés (durée, admission, diplôme), domaines, débouchés.
- **Nos partenaires** : logo, type de partenariat, description, site. Uniquement avec l'accord des structures.
- **Informations générales** : textes, e-mail, téléphone, réseaux sociaux, lien vers J-ECS.

## Formulaires

- `contact` : message à l'association, avec un objet (partenariat, stage, ancien, candidat, autre).
- `anciens` : inscription au réseau des anciens de l'ECS.

## Mise en ligne sur Cloudflare (hébergement actuel)

Le site est un site statique, sans compilation. Les fichiers `wrangler.jsonc` et `.assetsignore` indiquent à Cloudflare quoi publier.

1. **GitHub** : créer un dépôt `aeecs-site` sur le compte GitHub de la structure et y déposer tout le contenu de ce dossier (fichiers cachés compris : `.assetsignore`).
2. **admin/config.yml** : remplacer (déjà fait : `J-ECS/aeecs-site`).
3. **Cloudflare** : Workers & Pages → ouvrir le projet → Settings → Builds → *Connect* le dépôt GitHub `aeecs-site`, branche `main`. Laisser la commande de build vide ; la commande de déploiement est `npx wrangler deploy`. Chaque modification publiée depuis l'admin redéploie alors le site automatiquement.

## Accès à l'administration (AE-ECS)

L'administration utilise Sveltia CMS. Chaque administrateur a besoin d'un compte GitHub invité sur le dépôt (Settings → Collaborators, rôle Write).

1. Aller sur `/admin` du site, cliquer sur **Sign In with Token**.
2. Suivre le lien proposé pour créer un jeton GitHub (fine-grained, limité au dépôt `aeecs-site`, permission **Contents : Read and write**), puis le coller.
3. Le jeton reste dans le navigateur. À ne jamais partager ; le révoquer sur GitHub en fin de mandat.

Option plus confortable plus tard : un bouton « Sign In with GitHub » via le service gratuit *sveltia-cms-auth* déployé sur Cloudflare, puis `base_url` dans `admin/config.yml`.

## Formulaires

Les formulaires sont prévus pour Netlify Forms et ne transmettent rien sur Cloudflare tant qu'ils n'ont pas été adaptés.

## À compléter

- Durée, admission et diplôme du cycle ECS (Formation > Informations clés).
- Vérifier les domaines étudiés et les débouchés proposés.
- E-mail, téléphone et réseaux sociaux de l'association.
