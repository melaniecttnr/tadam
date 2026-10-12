# Tadam, dossier projet

Mis à jour le 29 septembre 2026. Ce fichier contient tout ce qui a été décidé et construit. La conversation d'origine a été supprimée, c'est la seule référence.

## Pour reprendre le projet

- Dans une nouvelle conversation, dire à Claude : « Lis `~/Desktop/Tadam/Tadam - Récap du projet.md`, c'est mon projet Tadam, on continue. »
- Le fichier de référence est `Site Tadam.html`. Il n'y a plus de version en ligne : l'artefact claude.ai a été supprimé le 29 septembre 2026, on travaille uniquement sur les fichiers du bureau.
- Avant chaque modification du site, copier la version actuelle dans `Archives/` (`Site Tadam V8.html`, puis V9, etc.).
- Pour vérifier le site après une modification : `cd ~/Desktop/Tadam/Outils && npm install jsdom && node verifier.js`. Le script simule un parcours complet, contrôle 1 440 profils (budget jamais dépassé, aucun animal supposé à tort) et mesure la couverture de la base.
- Pour voir le rendu réel : capture Chrome sans interface, par exemple `"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --window-size=1400,2000 --virtual-time-budget=4000 --screenshot=capture.png "file://$HOME/Desktop/Tadam/Site%20Tadam.html"`. Les captures figent parfois les animations en cours de route, ce n'est pas un bug du site. Chrome ne descend pas sous 500 px de large dans ce mode.
- Pour exporter la base vers Airtable : `node exporter-airtable.js` (même dossier). Il écrit `Base Airtable/Tadam - N idées.csv`.
- Le site est un fichier autonome : il a son propre doctype et la règle `[hidden]{display:none!important}`. Sans elle, la fenêtre du kit s'affiche vide par-dessus la page.
- Règles d'écriture : tutoiement, ton simple et chaleureux, français avec accents, jamais de tiret cadratin ni demi-cadratin, pas d'emoji, pas de tournures du type « pas X, mais Y ».

## Contenu du dossier

- `Site Tadam.html` : le prototype complet. Double-clic pour l'ouvrir (Internet nécessaire pour les polices).
- `mentions-legales.html`, `confidentialite.html`, `cgv.html` : les pages légales, à compléter (passages surlignés en jaune) et à faire relire par un professionnel du droit.
- `Base Airtable/Tadam - 195 idées.xlsx` et `.csv` : la base d'idées, 29 colonnes, prête à importer dans Airtable. L'Excel est la version conseillée.
- `Outils/verifier.js` et `Outils/exporter-airtable.js` : les outils de contrôle et d'export.
- `Archives/` : les versions V3 à V7 du site et l'ancienne base de 138 idées.
- Ce récap.

## Le concept

Un site qui trouve une idée cadeau pour un proche en 5 questions. Les idées viennent d'une base choisie et relue par un humain, pas d'une génération IA en direct. Trois types de résultats :

- **Achat** : un produit Amazon en lien partenaire.
- **Personnalisé** : une création sur mesure (gravure, illustration, photo) via Etsy en lien partenaire.
- **DIY** : une idée à faire soi-même, avec 3 étapes gratuites, une liste de matériel en liens Amazon, et un kit clé en main payant, généré par l'IA à partir des réponses.

## Décisions prises

- **Français uniquement pour le lancement.** L'anglais viendra après les premières ventes. Raisons : produits Amazon différents par pays, un programme Partenaires par pays, occasions et budgets différents, marché anglophone très encombré (Pickify, GiftX, Giftruly, Giftfeels, Bondlyfe), alors qu'en français il n'existe que des quiz de marques et des articles. À prévoir le moment venu : textes du site dans un fichier par langue, colonnes Airtable par langue, liens affiliés par pays, occasions et tranches de budget par pays.
- **Pas de prénom demandé** dans le quiz.
- **Le budget est une tranche à respecter, pas un plafond.** Jamais d'idée au-dessus. On ne descend d'une tranche que s'il manque des idées sur les thèmes choisis, avec l'étiquette « Sous ton budget ».
- **Types de résultats retenus** : Amazon, personnalisé Etsy, DIY avec kit. Consigne : prendre tout ce qui peut rapporter, sans que la monétisation soit trop visible.
- **Kits DIY** : format selon l'idée, dossier PDF, modèles Canva, ou les deux, « le plus complet possible ».
- **Résultat** : une idée forte et deux idées de secours derrière un bouton « Cette idée ne me plaît pas, une autre ».
- **Base d'idées** : Airtable, un produit précis par idée (lien Amazon affilié), objectif de 500 idées et plus au lancement, lots préparés par Claude puis relus par Mélanie.
- **Proches retenus** : amis, amour, famille (dont grands-parents et beaux-parents), travail (collègues, boss). Enfants et ados écartés pour l'instant.

## Charte et design

- **Logo** : « Tadam » en rouge foncé, point d'exclamation en orange, Bricolage Grotesque en gras (800). Validé par Mélanie, à ne pas modifier.
- **Fond de page** : beige chaud `#F3E3CE`. Cartes : `#FCF4E8`. Fond secondaire : `#EAD4B8`.
- **Rouge foncé** `#8E1B14` : bloc des questions, boutons, titres. Rouge profond `#6C110B`, rouge survol `#A92A1F`.
- **Orange** `#F07A22` et **jaune** `#FFC53D` : petites touches uniquement (point d'exclamation, progression, puces).
- **Textes** : brun très foncé `#2A140E`, secondaire `#6B4A3C`, beige `#F7E6CF` sur le rouge. Traits `#DCC1A2`.
- **Typos** : Bricolage Grotesque pour les titres, Figtree pour le texte (Google Fonts). Ne pas changer la typo du logo ni du texte de présentation.
- Un seul thème clair, pas de mode sombre.
- Seul le bloc du quiz est rouge. Le grand bloc rouge du haut de page a été retiré à la demande de Mélanie.
- **Éviter l'allure « générée par IA »** : pas de sur-titre en petites capitales espacées, pas de liste de coches, pas de grille d'engagements, pas de pointillés, pas de pilules très arrondies partout, étiquettes en minuscules. La progression du quiz est nommée (Qui, Quand, Goûts, Style, Effet).
- La section « Comment ça marche » en 3 étapes numérotées est gardée : Mélanie l'aime.
- **Vitrine « Quelques exemples »** : 4 étiquettes cadeaux légèrement inclinées, avec un vrai profil et l'idée que le quiz lui donne réellement. Clic pour voir le résultat complet, bouton pour d'autres profils.
- **Paragraphe « Comment Tadam gagne sa vie »**, écrit simplement : commissions sans changement de prix, kits payants une fois, données.
- **Signature** : l'idée révélée a la forme d'une étiquette cadeau (trou perforé en haut à gauche), avec des confettis rouges, orange et jaunes.

## Le parcours en 5 étapes

Principes tirés du benchmark :

- chaque question doit changer la recommandation, sinon on la retire ;
- la première question pose l'intention (pour qui), c'est elle qui pèse le plus ;
- des réponses concrètes plutôt que des curseurs abstraits (question scénario) ;
- toujours une porte de sortie « je ne sais pas trop » ;
- des sous-questions qui n'apparaissent que si elles servent ;
- les réponses restent visibles et modifiables (étiquettes cliquables en haut du quiz) ;
- un seul résultat fort, qui explique pourquoi il a été choisi.

La suite de chaque étape s'affiche au fil des clics. On passe tout seul à l'étape suivante dès qu'elle est complète (étapes 1, 2, 4 et 5), sans bouton, y compris quand on revient modifier une réponse. Le bouton « Continuer » n'existe qu'à l'étape 3, la seule à choix multiples. Mélanie a demandé de ne pas afficher de bouton inutile.

1. **Pour qui**
   - D'abord le genre : une femme, un homme, ou autre ou non précisé (formulations neutres : mon parent, mon frère ou ma sœur, un ami ou une amie, etc.).
   - Puis le rôle, dans une seule liste dont les libellés s'adaptent au genre : meilleur(e) ami(e), ami(e), ami(e) d'enfance, ma moitié, parent, frère ou sœur, grand-parent, beau-parent, collègue, boss. Changer de genre convertit le rôle déjà choisi.
   - Pour le genre neutre, le matching s'appuie sur les groupes (amis, parents, fratrie, grands-parents, travail) : les idées prévues pour un seul genre (par exemple fête des mères) ne sont pas proposées.
   - Puis l'âge : moins de 18 ans, 18 à 30, 30 à 50, 50 à 70, plus de 70.
   - Puis, seulement pour une amie, un ami, les beaux-parents et le travail : « Tu le ou la connais très bien, plutôt bien, pas tant que ça ». Si c'est « pas tant que ça », on écarte les cadeaux trop intimes et on privilégie l'utile.
2. **L'occasion et le délai**
   - Anniversaire, Noël, Saint-Valentin (pour la moitié seulement), fête des mères, des pères, des grands-mères ou des grands-pères (selon la personne), départ et Secret Santa (travail), retraite, crémaillère, pour dire merci, juste comme ça.
   - C'est pour quand : moins de 3 jours, 1 à 2 semaines, plus de 2 semaines.
3. **Ses goûts**
   - Jusqu'à 3 thèmes parmi Cuisine, Voyage, Déco et maison, Sport, Bien-être, Jeux de société, Geek et tech, Lecture, Art et création, Musique, Mode et bijoux, Nature et jardin, Animaux, Apéro et fête, Ciné et séries. Ou « Je ne sais pas trop, vise une valeur sûre ».
   - Si Animaux est coché : « Il ou elle a un animal ? » (un chien, un chat, un autre animal, pas d'animal). Aimer les animaux ne veut pas dire en avoir un : les idées pour un animal précis ne sortent que si la personne en a un, et du bon type.
   - À éviter, facultatif : pas d'alcool, pas de déco, pas de vêtement, pas de gadget, a déjà tout.
4. **Son dimanche idéal** (une seule réponse)
   - Sortir découvrir un nouveau coin, rester bien au chaud, voir du monde, retrouver ses proches, avancer sur ses projets, je ne sais pas trop.
5. **L'effet tadam, le budget et le temps**
   - Quand il ou elle ouvrira son cadeau, tu veux : faire rire, émouvoir, épater, faire plaisir au quotidien.
   - Budget : moins de 20 €, 20 à 50 €, 50 à 100 €, 100 à 200 €, plus de 200 €.
   - Temps à y passer : aucun (achat uniquement), 1 à 2 heures, un après-midi, un week-end.

## Le résultat

- **Révélation** : le quiz disparaît et laisse place au résultat, en haut de page. Une couverture rouge « Tadam! » s'ouvre sur l'idée, avec les confettis. Sécurité : la couverture est retirée au bout de 1,8 seconde même si l'animation ne se termine pas.
- En tête : « Pour ta mère », le récap des réponses, « Modifier mes réponses » et « Nouveau quiz ».
- Une idée forte, avec une phrase qui explique le choix (par exemple : « Choisie pour ta mère, qui aime la cuisine, et qui tient aux moments partagés. Pour un vrai moment d'émotion. »). Deux idées de secours derrière « Cette idée ne me plaît pas, une autre ». Après la 3e, le bouton devient « Ajuster mes critères », avec un lien pour revenir à la première.
- **Ajuster sans tout refaire** : l'effet voulu, le budget et le temps se changent directement sur le résultat, qui propose aussitôt 3 nouvelles idées.
- Encadré « En bref » : budget, temps (DIY), délai.
- **Achat et personnalisé** : bouton « Voir les modèles » (Amazon) ou « Voir les créations » (Etsy), avec la mention « Lien partenaire ». Pour l'instant ce sont des liens de recherche par mot-clé.
- **DIY** : les 3 étapes, puis « Le matériel » avec un lien partenaire Amazon par élément, puis le kit clé en main (format, prix, contenu).
- **Aperçu du kit** : la fenêtre du kit montre la première page du dossier (titre, « préparé pour ta mère, pour la fête des mères », sommaire, première étape), la case de renonciation au droit de rétractation, et le paiement désactivé.
- **Rappel des dates** : date de l'occasion, e-mail et case de consentement, pour un e-mail deux semaines avant la prochaine occasion. Dans le prototype, rien n'est envoyé et le message le dit. En ligne : double confirmation par e-mail, désinscription en un clic.

## Règles de sélection

Ce qui retire une idée :

- une tranche de budget différente de celle choisie (voir la décision sur le budget) ;
- une idée qui suppose un animal que la personne n'a pas ;
- une exclusion cochée (alcool, déco, vêtement, gadget) ;
- l'âge hors de la tranche prévue pour l'idée ;
- un délai trop court : personnalisé et DIY d'un week-end retirés s'il reste moins de 3 jours, herbier seulement à plus de 2 semaines ;
- le temps : « aucun » retire tous les DIY, et un DIY plus long que le temps choisi est retiré.

Ordre de remplissage des 3 idées : d'abord la bonne tranche et les bons thèmes, puis les bons thèmes une tranche en dessous, puis la bonne tranche hors thèmes.

Ce qui classe les idées (points) :

- chaque thème en commun : +8 (idée universelle sans thème commun : +2) ;
- budget pile dans la tranche : +4 ;
- animal : +4 pour une idée pensée pour son chien ou son chat ;
- proche : prévu exactement +5, prévu pour son groupe +3, idée pour tous +1, pas prévu -7 ;
- occasion : prévue +3, ou +6 si l'idée est pensée pour peu d'occasions, pas prévue -7 ;
- effet voulu : +5 si l'idée le produit ;
- dimanche idéal : +3 si l'idée correspond au profil ;
- goûts « je ne sais pas trop » : +6 pour les idées universelles ;
- proximité « pas tant que ça » : -8 pour les idées intimes, +2 pour les idées utiles ; « très bien » : +2 pour les idées intimes ;
- « a déjà tout » : +3 pour le personnalisé et le DIY, -1 pour l'achat ;
- du temps disponible : +2 pour les DIY ;
- les idées de secours pénalisent de 2 points un type déjà proposé, pour varier.

## Kits DIY

- Formats selon l'idée : dossier PDF prêt à imprimer, modèles Canva modifiables, ou les deux.
- Prix provisoires, à valider par Mélanie : de 4,90 € à 14,90 € selon la complexité (escape game et livre de recettes à 14,90 €).
- Paiement unique, sans abonnement. Paiement prévu : Stripe, pas encore branché.
- Génération prévue : API Claude à partir des réponses du quiz, envoi du dossier par e-mail.
- Chaque DIY a sa liste de matériel (tableau `MAT` dans le code), transformée en liens partenaires Amazon.

## Monétisation et mentions obligatoires

- Liens partenaires Amazon (produits et matériel des DIY), liens Etsy, kits DIY payants.
- Pistes pour plus tard : expériences (ateliers, coffrets), emballage cadeau ou carte à message en option, version premium des kits.
- La mention « lien partenaire » reste obligatoire, discrète sous chaque bouton. Mention Amazon en pied de page : « En tant que Partenaire Amazon, Tadam réalise un bénéfice sur les achats remplissant les conditions requises. »
- Ne jamais afficher de prix Amazon sur le site : le contrat Partenaires l'interdit s'ils ne viennent pas de l'API officielle et ne sont pas à jour. La colonne « Prix indicatif » reste un repère interne.
- Le compte Partenaires Amazon doit faire 3 ventes dans les 180 jours après l'inscription, sinon il est fermé. L'API officielle (et donc les images et prix automatiques) n'est accessible qu'après des ventes réelles. Au début, liens et images se récupèrent à la main (barre SiteStripe d'Amazon).
- Identifiant Partenaire Amazon à renseigner dans le code : constante `AMAZON_TAG`. Etsy passe par son programme d'affiliation (via Awin), à brancher.

## Bases légales

- Pied de page : mentions légales, confidentialité, conditions de vente des kits, « Gérer les cookies », mention Partenaire Amazon.
- Bandeau cookies : « Refuser » et « Accepter » au même niveau, aucun traceur chargé sans accord, choix modifiable à tout moment. Le choix est gardé dans le navigateur.
- Conditions de vente : contenu numérique livré tout de suite, renonciation au droit de rétractation avec accord exprès (article L221-28 du Code de la consommation), garantie de conformité des contenus numériques, médiateur de la consommation, droit français.
- Confidentialité : le quiz ne transmet rien ; rappels par consentement ; achat de kit par contrat (Stripe pour le paiement, réponses envoyées au fournisseur d'IA sans nom ni e-mail) ; cookies de mesure seulement avec accord (13 mois maximum) ; droits RGPD et CNIL.
- À compléter : identité et statut de l'éditeur, SIREN, adresse, contact, directeur de la publication, hébergeur, prestataire d'e-mails, fournisseur de paiement, fournisseur d'IA, médiateur, mention TVA, dates de mise à jour.
- En production : héberger les polices sur le site plutôt que chez Google Fonts, pour ne pas envoyer l'adresse IP des visiteurs à Google.
- Ces pages sont des modèles : à faire relire par un professionnel du droit avant la mise en ligne.

## La base d'idées (Airtable)

Colonnes de la table « Idées » (29, déjà dans l'export) :

- Nom, Statut (Brouillon, À relire, En ligne), Type (Achat Amazon, Personnalisé Etsy, DIY avec kit), Accroche.
- Proches, Âges, Occasions, Thèmes, Exclusions : sélection multiple.
- Effets (Faire rire, Émouvoir, Épater, Faire plaisir au quotidien), Profils (dimanche idéal), Animal requis (Chien, Chat, N'importe lequel) : sélection multiple. Intime : case à cocher.
- Cocooning ou aventure, Utile ou symbole, Classique ou original : sélection unique. Le site s'en sert pour déduire les effets et profils quand ils ne sont pas renseignés.
- Budget (sélection unique), Prix indicatif (interne), Temps de réalisation, Délai minimum.
- Mot-clé de recherche, Lien affilié, ASIN, Lien vérifié le.
- Étapes, Matériel, Format du kit, Prix du kit, Contenu du kit (DIY).

Seules les idées « En ligne » s'afficheront sur le site. Les 84 premières idées sont en « À relire », les 111 suivantes (lots 1, animaux et 2) en « Brouillon ».

Import : dans Airtable, créer une nouvelle base à partir du fichier Excel, puis passer les colonnes en sélection multiple ou unique. Importer dans une table existante peut être bloqué sur le plan gratuit. Alternative plus propre : un jeton d'accès personnel Airtable (autorisations `data.records:read`, `data.records:write`, `schema.bases:read`, `schema.bases:write`, limité à la base Tadam), que Claude range dans `.claude/secrets/.env` de l'espace de travail, pour créer la table avec les bons types et envoyer les idées directement.

## État de la base

- **195 idées** : 140 achats, 25 personnalisées, 30 DIY.
- Par budget : moins de 20 € 54, 20 à 50 € 58, 50 à 100 € 34, 100 à 200 € 30, plus de 200 € 19.
- Par effet : utile 66, épater 66, émouvoir 65, faire rire 41, sans effet 19.
- Par profil : cocon 104, proches et souvenirs 64, projets 62, aventure 34, voir du monde 25.
- 16 idées demandent un animal, 37 sont marquées intimes.
- Historique :
  - 84 idées de départ ;
  - lot 1 (54 idées) : budgets de plus de 100 €, animaux, musique, ciné, nature, sport ;
  - 8 idées pour les amoureux des animaux sans animal ;
  - lot 2 (49 idées) : budgets de plus de 50 €, lecture, mode, ciné, fête, aventure, cuisine sans alcool pour le travail.
- Couverture mesurée (tous les proches x tous les thèmes x toutes les tranches) :
  - profils avec moins de 3 idées : 60 % au départ, 25 % après le lot 1 ;
  - idées proposées sous le budget : 20 % avant le lot 2, 10 % après. Aucune idée au-dessus du budget.
- **Manques restants** :
  - tranches 100 à 200 € et plus de 200 € (la majorité des idées « sous le budget » viennent de là) ;
  - thèmes les plus faibles : bien-être, jeux, lecture, animaux, puis voyage, art, musique, fête ;
  - effets et profils les plus faibles : faire rire, voir du monde, aventure.
- **Lot 3 à faire** : idées à 100 à 200 € et plus de 200 € sur ces thèmes.
- **À faire sur toutes les idées « Achat »** : choisir le produit précis sur Amazon, remplir l'ASIN et le lien affilié, vérifier que la tranche de budget correspond au vrai prix, récupérer une photo. Le site n'a pas encore de photos, c'est le prochain gros chantier après le lot 3.

## Relier Airtable au site

Ne jamais relier Airtable directement à la page : le jeton serait visible par n'importe quel visiteur, qui pourrait modifier ou effacer la base.

Montage recommandé :

1. Airtable reste l'outil de travail.
2. Un programme de synchronisation lit les idées « En ligne », les convertit au format du site et écrit un fichier `idees.json`. Le jeton, en lecture seule (`data.records:read`, `schema.bases:read`), reste caché dans les réglages de l'hébergeur.
3. Le site lit `idees.json` au lieu de la liste écrite dans le code.
4. Mise à jour chaque nuit, ou à la demande avec un bouton « republier ». Quelques appels à l'API par nuit ; le plan gratuit d'Airtable serait limité à 1 000 appels par mois, à vérifier.

Il faut : un hébergeur (Netlify recommandé : gratuit au départ, bouton de republication, synchronisation de nuit facile), un dépôt GitHub pour le code, le jeton Airtable en lecture seule, un nom de domaine si besoin (disponibilité de tadam.fr à vérifier chez un registrar). Mélanie crée elle-même les comptes.

## Acquisition et mesure

- Google Ads payant difficilement rentable : les commissions Amazon ne font que quelques pour cent du prix, et les mots-clés « idée cadeau » sont chers, surtout avant Noël.
- **Levier principal : le SEO.** La base permet de générer des pages par combinaison, par exemple « Idée cadeau belle-mère Noël 20 à 50 € » ou « Cadeau fête des mères qui aime la cuisine ».
- Pinterest et TikTok conviennent très bien aux cadeaux et au DIY. Les kits font du contenu tout trouvé.
- Calendrier : Noël, Saint-Valentin et fête des mères concentrent les recherches. Pour Noël, les pages doivent être en ligne dès octobre.
- Mesure à brancher dès le lancement (GA4, avec consentement) : un événement par étape du quiz, « une autre idée », ajustement, clic partenaire, ouverture du kit, demande de rappel. Objectif : voir où les visiteurs abandonnent et quelles idées ne plaisent jamais.

## Benchmark (29 septembre 2026)

Constats qui ont guidé le quiz :

- 5 à 8 questions, chacune doit changer la recommandation ;
- des questions guidées donnent de meilleurs résultats que du texte libre ;
- une mise en situation (« Son week-end parfait, c'est… », Bondlyfe) plutôt que des curseurs ;
- demander la réaction voulue (larmes de joie, fou rire, effet waouh, Giftfeels) ;
- peu de résultats, avec une explication (Pickify en propose 4 et note que 20 résultats paralysent les indécis) ;
- chez la marque JOTT, un quiz cadeaux de Noël a multiplié la conversion par 5, avec 74 % de visiteurs allant jusqu'au bout.

Sources : pickifyai.com/blog/best-ai-gift-finders-2026, giftfeels.com/tools/gift-finder-quiz, bondlyfe.com/gift-finder-quiz, zoovu.com/blog/interactive-gift-finder-best-practices, everydayindustries.com/product-recommendation-quiz-tips, quizell.com/case-studies/jott, beauxcadeaux.fr/comment-trouver-cadeau-parfait.

## En attente

- **Invitation Airtable** reçue le 29 septembre 2026 : à accepter par Mélanie avec son compte. Claude ne peut pas accepter une invitation ni se connecter à sa place.
- **Jeton Airtable** si Mélanie veut que Claude remplisse la base par l'API.
- **Choix de l'hébergeur** (Netlify recommandé) et création des comptes Netlify et GitHub.
- **Prix des kits** à valider.
- **Informations légales** à fournir pour compléter les pages.
- **Identifiant Partenaire Amazon** et inscription à l'affiliation Etsy.

## Prochaines étapes, dans l'ordre

1. Lot 3 d'idées : 100 à 200 € et plus de 200 €, bien-être, jeux, lecture, animaux, plus d'idées « faire rire », « voir du monde », « aventure ». Vérifier avec `verifier.js` que la part d'idées sous le budget baisse.
2. Importer la base dans Airtable et relire les idées (passer en « En ligne » celles qui sont validées).
3. Choisir les produits Amazon précis, les ASIN, les liens affiliés et les photos. Ajouter les photos au site.
4. Hébergement : Netlify et GitHub, site qui lit `idees.json`, synchronisation Airtable de nuit.
5. Compléter et faire relire les pages légales ; héberger les polices sur le site.
6. Brancher GA4 avec les événements, derrière le bandeau cookies.
7. Pages SEO générées à partir de la base, en priorité sur Noël (en ligne dès octobre).
8. Valider les prix, puis brancher Stripe, la génération des kits par l'API Claude et l'envoi par e-mail.
9. Brancher l'envoi réel des rappels (prestataire d'e-mails, double confirmation).
10. Plus tard : préparer le multilingue, puis la version anglaise.
