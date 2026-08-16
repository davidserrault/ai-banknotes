---
name: billet-fictif
description: Générer un billet de banque imaginaire à partir d'un thème, d'une couleur dominante, d'une valeur faciale et d'un nom de devise fictive, en appliquant un zoning graphique cohérent. A utiliser pour créer une image, rédiger un prompt de génération d'image ou décrire la maquette d'une monnaie fictive destinée à une œuvre, un jeu, une illustration ou un univers narratif. Ne jamais reproduire ni imiter une monnaie réelle ayant cours légal.
---

# Générateur de Design de Billet de Banque

inputs:
* name: theme; type: string; description: Thème visuel de l'illustration centrale (ex : "faune sauvage", "architecture industrielle", "flore tropicale", "paysage désertique").
* name: primary_color; type: string; description: Couleur dominante du billet (ex : "bleu océan", "vert forêt", "rouge écarlate", "jaune ocre").
* name: denomination; type: string; description: Valeur faciale à afficher sur le billet (ex : "5", "10", "50", 100, "200").
* name: currency_name; type: string; description: Nom de l'unité monétaire à inscrire (ex : "Clochette", "Simflouz", " Crédit galactique", "Devise").

outputs:
* name: image; type: binary; description : Une image d'un billet de banque fictif au format horizontal paysage 2:1, conforme au layout, correspondant à la demande de l'utilisateur.
* name: image_generation_prompt; type: string; description: Un prompt technique prêt à être injecté dans un générateur d'images (DALL-E 3, Midjourney, Stable Diffusion) pour produire le billet.

tags:
* generation-image
* design-monétaire
* mise-en-page
* infographie
* template

## Objectif
Ce skill prend des caractéristiques visuelles de base (thème, couleur, valeur, nom) évoquées par l'utilisateur et construit un **prompt de génération d'image extrêmement détaillé**. Ce prompt respecte les normes d'un billet de banque moderne : organisation spatiale rigide, 9 zones distinctes avec des proportions fixes, et éléments de sécurité graphiques. Format horizontal paysage 2:1.

## ⚠️ Avertissement Légal et Artistique
Ce skill est strictement conçu pour la **génération d'œuvres d'art fictives et conceptuelles** (illustrations, design graphique, univers de jeu vidéo, ou projets artistiques).
**Il est formellement interdit d'utiliser ce skill pour tenter de générer des billets de banque réels, des contrefaçons, ou toute forme de monnaie ayant cours légal.** Le prompt généré inclut systématiquement des consignes artistiques pour éviter le réalisme photoréaliste des billets officiels.

## Schéma de Zoning Précise (Maquette du layout)
Pour garantir une précision de proportions lors de la génération, le skill intègre le schéma de répartition spatiale suivant dans ses instructions à l'IA génératrice :

+-----------------------------------------------------------------------+
| [Bande Gauche] [        HAUT (30% de la hauteur)         ][Bande Dte]|
|                +--------------+------------+------------+            |
| | Zone 1   |   |  Zone 2    |  Zone 4    |  Zone 6   | | Zone 7   |  |
| | (15% Lg) |   | (Chiffre)  | (Avant-Plan| (Second.) | | (10% Lg) |  |
| | Logo &   |   |  Gros      |  Central)  |           | | Sécurité |  |
| | Acronymes|   |  Format    |            |           | | Droite   |  |
| |          |   +------------+            |           | |          |  |
| |          |   |  Zone 3    |            |           | |          |  |
| |          |   | (Nom Devise|            |           | |          |  |
| |          |   |  Multiling)|            |           | |          |  |
| |          |   +------------+            +-----------+ |          |  |
| |          |   |  Zone 5 (Arrière-plan Central)      | |          |  |
| |          |   |   (Motif de fond répétitif)         | |          |  |
| |          |   |                                     | |          |  |
| |          |   |                                     | |          |  |
| |          |   +-----------------+-------------------+ |          |  |
| |          |                     | Zone 9 (Sceau      | | Zone 8  |  |
| |          |   Zone 4 (suite)    | Sécurité géomét.)  | | (Bas-   |  |
| |          |                     | (Bas milieu-droit) | | droite  |  |
| |          |                     |                    | | Valeur  |  |
| |          |                     |                    | | petit)  |  |
| +----------+---------------------+--------------------+----------+---+
|                            LARGEUR TOTALE = 100%                     |
+----------------------------------------------------------------------+


## Règles de Construction du Prompt
Pour garantir l'universalité du design, le skill génère le prompt en respectant les zones et proportions suivantes (base du layout) :

### Description du Layout Standard (Inchangé dans le prompt)
*   **Format général** : Billet de banque rectangulaire horizontal, style aquarelle vectorielle et sérigraphie offset, papier texturé, avec bandes de sécurité visuelles.
*   **Zone 1 (15% Gauche)** : Bande verticale sur le bord gauche. Inclure des `[ACRONYMES_INSTITUTIONS]` stylisés et un emplacement vide pour le logo de banque.
*   **Zone 2 (Haut-Gauche)** : La valeur `[DENOMINATION]` en très gros chiffres, typographie sans-serif grasse et moderne.
*   **Zone 3 (Milieu-Gauche)** : Le nom de la devise `[CURRENCY_NAME]` écrit en 3 alphabets différents juste sous le gros chiffre.
*   **Zone 4 (Centre - Avant-plan, 60% largeur x 70% hauteur)** : L'illustration principale, basée sur le thème `[THEME]`, détaillée et occupant le centre en avant-plan.
*   **Zone 5 (Arrière-plan)** : Un motif de fond stylisé et répétitif (vagues, montagnes, lignes géométriques) en teintes légères, se fondant avec la `[PRIMARY_COLOR]`.
*   **Zone 6 (Haut-droit)** : Une version miniature ou un détail secondaire du `[THEME]` (ex: petite silhouette en arrière-plan).
*   **Zone 7 (10% Droite)** : Bande verticale de sécurité (effet holographique ou filigrane) sur le bord droit.
*   **Zone 8 (Bas-droit)** : La valeur `[DENOMINATION]` en petit format, en surimpression claire.
*   **Zone 9 (Bas-milieu-droit)** : Sceau de sécurité géométrique (ex : un losange avec des cercles concentriques) intégré au design.

## Méthodologie d'Exécution
Le skill remplace les crochets `[...]` par les valeurs fournies en entrée (`inputs`) et assemble le prompt final en langage naturel orienté générateur d'image.

### Exemple de Prompt Généré (Pattern)
> *"Crée un billet de banque rectangulaire horizontal au style illustration vectorielle aquarellée. Utilise le jaune ocre comme couleur dominante. Le layout respecte le zoning suivant :
> 1. À gauche, une bande verticale de 15% de largeur contenant des acronymes bancaires stylisés et un logo d'institution.
> 2. En haut à gauche, le chiffre '50' écrit en très gros caractères gras.
> 3. Au milieu-gauche, le nom 'Euro' écrit en alphabet latin, cyrillique et grec.
> 4. Au centre (occupant 60% de la largeur), dessine une illustration détaillée d'une faune sauvage (exemple : un oiseau aquatique) en avant-plan.
> 5. En arrière-plan, un motif géométrique de vagues et de montagnes en teintes jaune pâle.
> 6. En haut à droite, ajoute une petite silhouette secondaire du même oiseau en vol.
> 7. Sur le bord droit, une bande holographique de sécurité de 10% de largeur.
> 8. En bas à droite, le chiffre '50' en petit format.
> 9. Intègre un sceau de sécurité géométrique (losange) entre l'illustration centrale et la bande de sécurité.
> Assure-toi que l'image est haute résolution, avec des mentions lisibles, et qu'elle respecte les proportions de mise en page d'un billet de banque physique. telle que décrite dan le Layout"*

## Format de Sortie (Output)
Le skill retourne une `image`  du billet ou si la fonction de génération d'image n'est pas disponible l'objet `image_generation_prompt` contenant le bloc texte formaté prêt à être passé à un outil de génération d'images (ex: Midjourney, Stable Diffusion, ou appel d'API DALL-E).
