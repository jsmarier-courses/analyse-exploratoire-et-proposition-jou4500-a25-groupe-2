**Date**<br>
**Cote et nom du cours**<br>
**Prénom et nom de l'étudiant(e)**<br>
**Présenté à Jean-Sébastien Marier**<br>

# Analyse exploratoire de données (AED) et proposition

Utilisez un croisillon (`#`) pour créer un intertitre de niveau 1 comme celui-ci.

## Avant-propos

Pour ce travail, vous devez extraire des données d’un site Internet ou d’une base de données. Vous devez ensuite nettoyer et analyser votre jeu de données, trouver une histoire potentielle et créer une visualisation. Votre travail doit clairement expliquer votre processus. Vous devez écrire environ 1500 à 2000 mots et inclure des captures d’écran montrant les différentes étapes de votre analyse. Votre travail doit être rédigé avec le format Markdown et être publié sur GitHub.

J'assigne différentes versions de ce projet à mes étudiants en journalisme numérique et en « data storytelling » depuis déjà quelques années. La structure générale de ce travail est basée sur celle du [*Guide du datajournalisme*](http://jplusplus.github.io/guide-du-datajournalisme/index.html). La présente version est également inspirée du programme [Key Capabilities in Data Science](https://extendedlearning.ubc.ca/programs/key-capabilities-data-science) offert par l'Université de la Colombie-Britannique (UBC).

**Voici quelques ressources utiles pour ce travail :**

* [Page *Syntaxe de base pour l’écriture et la mise en forme* de GitHub](https://docs.github.com/fr/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
* [Le répertoire modèle pour ce projet au cas où vous effaceriez quelque chose par accident](https://github.com/jsmarier/jou4100_jou4500_mpad2003_project2_template)

Avez-vous remarqué comment créer un hyperlien? En langage Markdown, on met le texte cliquable entre une paire de crochets et l'adresse URL entre parenthèses.

Pour créer une liste non ordonnée, il suffit de mettre une étoile (`*`) devant chaque item.

## 1. Introduction

Dans le cadre de ce travail, nous analyserons un jeu de données de la Ville d’Ottawa portant sur l’enjeu suivant : l’état matrimonial de la population âgée de 15 ans et plus, selon les différents quartiers de la ville. L’objectif est d’observer comment les situations matrimoniales (célibataire, marié(e), séparé(e), divorcé(e), veuf/veuve) varient d’un quartier à l’autre et d’identifier des tendances démographiques ou des disparités territoriales.
Le jeu de données utilisé s’intitule Questionnaire détaillé du recensement de 2021 – Données par quartier. Il s’agit d’un ensemble de données dérivé du Recensement de Statistique Canada, obtenu à partir du questionnaire détaillé complété par un échantillon approximatif de 25 % des ménages.
Ce jeu de données :
* a été collecté dans le cadre du Recensement de la population 2021 réalisé par Statistique Canada ;
* *ventile les résultats par quartier municipal, permettant de comparer les réalités démographiques entre zones géographiques ;
* inclut des indicateurs sociodémographiques détaillés, dont l’état matrimonial, le niveau de scolarité, le revenu, les caractéristiques du logement et d’autres variables liées à la composition des ménages ;
* est fourni en format CSV via le portail de données ouvertes, ce qui permet d’effectuer des analyses statistiques et visuelles.

Liens
Jeu de données original (Ville d’Ottawa) : https://ouverte.ottawa.ca/datasets/ottawa::questionnaire-détaillé-du-recensement-de-2021-données-par-quartier/about  
CSV sur GitHub: https://raw.githubusercontent.com/jsmarier/files-for-course-assignments/refs/heads/main/Questionnaire_détaillé_du_recensement_de_2021_Données_par_quartier.csv 

Ce travail sera structuré en plusieurs étapes. Dans un premier temps, nous expliquerons le processus d’obtention des données, incluant l’accès au jeu de données de la Ville d’Ottawa et sa source (le recensement de 2021 de Statistique Canada). Ensuite, nous procéderons au nettoyage et à la préparation des données, ce qui comprend la sélection des variables liées à l’état matrimonial, l’organisation des valeurs et la vérification de la qualité des données. Une troisième section sera consacrée à l’analyse descriptive, où nous analyserons la distribution des différents états matrimoniaux pour la population âgée de 15 ans et plus selon les quartiers. Finalement, nous présenterons les résultats et leur interprétation, en soulignant les variations observées entre les quartiers et les pistes de réflexion que ces différences permettent d’envisager.

## 2. Obtenir les données

Utilisez deux croisillons (`##`) pour créer un intertitre de niveau 2 comme celui-ci.

Pour cette activité, on a choisi d'utiliser le fichier CSV intitulé « Questionnaire détaillé du recensement de 2021 - Données par quartier. », qui présente des statistiques de la Ville d'Ottawa, classées par quartier.

Importation des données dans Google Feuilles de calcul :

On a d'abord ouvert Google Feuilles de calcul et créé une nouvelle feuille. Dans le menu principal, on a sélectionné : 1- Fichier, 2- Importer, 3- on a sélectionné le fichier CSV depuis le bureau de l’appareil. 4 - enfin, on a importé le fichier CSV fourni.

Une fenêtre d'options s'est indiquée : on a choisi Remplacer la feuille actuelle, le séparateur automatique (virgule), et cocher Convertir les nombres et dates. Après avoir cliqué sur Importer les données, le jeu de données est apparu corrigé.


Utilisez le modèle de code ci-dessous pour insérer une capture d'écran. Vos images doivent être sauvegardées dans le même dossier que votre fichier `.md`.

![alt text](<Screenshot 2025-11-11 at 5.37.04 AM.png>)


![](import-screen-capture.png)<br>
*Figure 1 : La fenêtre d'importation d'un fichier de Google Feuilles de calcul.*

**Voici quelques exemples de fonctions et de lignes de code mises dans des boîtes grises :**

Lien vers le document CSV :
https://raw.githubusercontent.com/jsmarier/files-for-course-assignments/refs/heads/main/Questionnaire_détaillé_du_recensement_de_2021_Données_par_quartier.csv 


1. Si vous nommez une fonction, mettez là à l'intérieur de guillemets « inclinés » comme ceci : `IMPORTHTML`.
1. Si vous voulez inclure une ligne de code complète, faites la même chose, mais avec tout le code : `=IMPORTHTML("https://en.wikipedia.org/wiki/China"; "table", 5)`.
1. Alternativement, vous pouvez mettre le code dans une boîte indépendante en utilisant le modèle de code ci-dessous :

Observations générales :

Le fichier contient environ 26 colonnes et 2603 lignes. Les données semblent généralement propres, bien structurées et sans cellules vides majeures. Chaque colonne correspond à un quartier de la Ville d'Ottawa et chaque ligne contient une variable spécifique provenant du recensement (ex. population, âge médian, revenu, langue, etc).


Observations spécifiques : 

Colonne A : Nom du quartier : variable nominal représentant le nom administratif de chaque secteur. Aucune valeur manquante n'est observée.

Colonne B : Population totale : variable discrète quantitative (valeurs entières). On remarque des écarts importants entre les quartiers centraux et périphériques.

Colonne C : Revenu médian : variable quantitatif poursuivre. Certaines vailleurs paraissant élevées ou faibles, ce qui reflète probablement la diversité socioéconomique des quartiers.


Question ou hypothèse : 

Les quartiers centraux présentent une proportion plus élevée de personnes non mariées (jeunes professionnels, étudiants, locataires), tandis que les quartiers périphériques affichent une proportion plus élevée de personnes mariées (familles, propriétaires).

``` r
=IMPORTHTML("https://en.wikipedia.org/wiki/China"; "table", 5)
```
C'est aussi comme ça qu'on crée une liste ordonnée. Il suffit de mettre `1.` devant chaque item.

## 3. Comprendre les données

### 3.1. Analyse VIMA

Utilisez trois croisillons (`###`) pour créer un intertitre de niveau 3 comme celui-ci. Je vous prie de suivre ce modèle en ce qui a trait aux intertitres de niveaux 1 et 2. Toutefois, je vous laisse le loisir d'utiliser les intertitres de niveau 3 comme bon vous semble.

Insérez votre texte ici.

Appuyez vos affirmations en citant les sources appropriées. Veuillez suivre les [normes APA en matière d'attribution dans le corps du texte](https://apastyle.apa.org/style-grammar-guidelines/citations).

**Par exemple :**

Comme l'affirme Cairo (2016), une visualisation de données doit être véridique...

### 3.2. Nettoyage des données

Insérez votre texte ici.

### 3.3. Analyse exploratoire des données (AED)

Insérez votre texte ici.

**Cette section doit inclure une capture d'écran de votre tableau croisé dynamique, comme ceci :**

![](pivot-table-screen-capture.png)<br>
*Figure 2 : Ce tableau croisé dynamique montre...*

**Cette section doit aussi inclure une capture d'écran de votre graphique exploratoire, comme ceci :**

![](chart-screen-capture.png)<br>
*Figure 3 : Ce graphique exploratoire montre...*

## 4. Récit potentiel

Insérez votre texte ici.

## 5. Conclusion

Insérez votre texte ici.

## 6. Références

Veuillez inclure une liste de vos références ici. Assurez-vous de suivre les [normes APA pour les références](https://apastyle.apa.org/style-grammar-guidelines/references). Les retraits négatifs (*hanging paragraphs*) ne sont pas nécessaires. Le [guide sur l'adaptation APA](https://arts.uottawa.ca/lettres/sites/arts.uottawa.ca.lettres/files/cartu-outils-de-redaction-adaptation-apa.pdf) de l'Université d'Ottawa pourrait également vous être utile.

**Voici un exemple :**

Bounegru, L., & Gray, J. (Eds.). (2021). *The Data Journalism Handbook 2: Towards A Critical Data Practice*. Amsterdam University Press. [https://ocul-crl.primo.exlibrisgroup.com/permalink/01OCUL_CRL/hgdufh/alma991022890087305153](https://ocul-crl.primo.exlibrisgroup.com/permalink/01OCUL_CRL/hgdufh/alma991022890087305153)
