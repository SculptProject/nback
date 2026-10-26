# n-back quotidien

Une petite application web pour faire un peu de n-back chaque jour, sur téléphone. Elle s’installe sur l’écran d’accueil comme une vraie app et fonctionne hors connexion.

- 13 versions : Position, Lettres entendues, Lettres lues, Dual, Position et couleur, Position et forme, Double position, Triple, Quad, Combinaison, Variable, Crabe et Arithmétique.
- Niveau automatique dans chaque version : 80 % ou plus, il monte ; sous 50 %, il descend.
- Objectif quotidien réglable (en séances ou en minutes), série de jours d’affilée et historique sur 16 semaines.
- Proposition automatique de la version la moins jouée de la semaine, pour varier l’entraînement.
- Aucune dépendance, aucun compte, aucune donnée envoyée sur Internet.

## Mettre l’application en ligne avec GitHub Pages

1. Crée un nouveau dépôt sur GitHub (par exemple `nback`). Il peut être public ou privé, mais GitHub Pages n’est gratuit que pour les dépôts publics sur un compte gratuit.
2. Décompresse le zip sur ton ordinateur, ouvre le dossier, sélectionne **tous les fichiers qu’il contient** (il n’y a aucun sous-dossier) et glisse-les dans la page « Add file » puis « Upload files » du dépôt. Vérifie ensuite que la page d’accueil du dépôt liste bien `index.html`, `manifest.webmanifest`, `sw.js`, les cinq images `.png` et les quatre polices `.woff2`, directement à la racine.

   En ligne de commande, depuis le dossier décompressé :

   ```bash
   git init
   git add .
   git commit -m "Première version"
   git branch -M main
   git remote add origin https://github.com/TON-PSEUDO/nback.git
   git push -u origin main
   ```

3. Dans le dépôt, va dans **Settings**, puis **Pages**. Sous « Build and deployment », choisis **Deploy from a branch**, sélectionne la branche `main` et le dossier `/ (root)`, puis enregistre.
4. Après une minute environ, l’application est disponible à l’adresse `https://TON-PSEUDO.github.io/nback/`.

## L’installer sur ton téléphone

**iPhone (Safari)** : ouvre l’adresse dans Safari, touche le bouton de partage, puis « Sur l’écran d’accueil ». Lance ensuite l’app depuis son icône.

**Android (Chrome)** : ouvre l’adresse dans Chrome, touche le menu ⋮, puis « Installer l’application » ou « Ajouter à l’écran d’accueil ».

Une fois ouverte une première fois, l’application fonctionne sans connexion.

## Le son

Les versions avec son utilisent la voix de synthèse française du téléphone. Sur iPhone, désactive le mode silencieux, sinon les lettres ne sont pas prononcées. Le bouton « Tester la voix » dans les réglages permet de vérifier. Si tu préfères jouer sans son, désactive « Versions avec son » : il reste six versions silencieuses.

## Tes données

Ta progression est enregistrée uniquement dans le navigateur de ton téléphone. Elle n’est pas partagée entre appareils, et elle disparaît si tu effaces les données du navigateur ou supprimes l’app.

Pour la mettre à l’abri ou la transférer, utilise **Réglages > Exporter mes données**, puis **Importer une sauvegarde** sur l’autre appareil.

À noter : sur iPhone, l’app installée sur l’écran d’accueil et Safari ont des stockages séparés. Joue toujours depuis l’icône pour garder une seule progression.

## Faire une modification

1. Modifie les fichiers (tout le code de l’application est dans `index.html`).
2. Dans `sw.js`, change la valeur de `VERSION` (par exemple `nback-v2` devient `nback-v3`). Sans ça, les téléphones qui ont déjà l’app peuvent continuer à afficher l’ancienne version.
3. Envoie les changements sur GitHub. La mise à jour apparaît après une ou deux ouvertures de l’app.

Pour tester en local avant d’envoyer, lance un petit serveur dans le dossier (le service worker ne fonctionne pas en ouvrant directement le fichier) :

```bash
python3 -m http.server 8000
```

puis ouvre `http://localhost:8000`.

## Contenu du dossier

Tous les fichiers sont à la racine, sans sous-dossier, pour que l’envoi sur GitHub ne puisse rien oublier.

| Fichier | Rôle |
| --- | --- |
| `index.html` | L’application complète : interface, moteur de jeu, sauvegarde. L’icône d’onglet y est aussi intégrée directement. |
| `manifest.webmanifest` | Nom, couleurs et icônes utilisés à l’installation |
| `sw.js` | Service worker pour le fonctionnement hors connexion |
| `apple-touch-icon.png` | Icône de l’écran d’accueil sur iPhone |
| `icon-192.png`, `icon-512.png`, `icon-maskable-512.png` | Icônes de l’écran d’accueil sur Android |
| `favicon-32.png` | Icône d’onglet de secours pour les anciens navigateurs |
| `sora-400.woff2` à `sora-700.woff2` | Police Sora, sous licence SIL Open Font License (`sora-licence-OFL.txt`) |

## Raccourcis clavier

Sur ordinateur, les boutons de réponse correspondent aux touches A, L, S, K et D dans l’ordre affiché. En arithmétique, tape la réponse au clavier. Échap met la partie en pause.
