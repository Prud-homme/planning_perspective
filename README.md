# Module Planning
  
## Utilisation

Pour utiliser le module Planning il faut importer les scripts, styles et views contenu dans le fichier *.zip* avec le Designer d'Ignition.
Il faudra également importer le template *Flex_Button*.

## Description

Le module Planning est composé de trois parties:

* Scripting: contient les scripts utilisés dans les Views
* Perspective Style: contient des paramètres de style associé aux boutons, tableau et taille du texte
* Perspective Views: 
  - A_Venir: View qui affiche la liste des dérogations à partir de la date du jour et permet de les modifier.
  - Annuel: View qui affiche le planning d'un équipement en prenant en compte le planning hebdomaire ainsi que les dérogations. L'ajout ou la modification de dérogations est possible.
  - Day_Embed: View qui affiche les plages actives lors d'une journée pour un équipement.
  - Delete_Confirm: View utilisée en pop-up qui permet de confirmer la suppression d'une période hebdomadaire ou une dérogation.
  - Duplicate: View utilisée en pop-up qui affiche un message lorsqu'une dérogation est déjà en place sur une période.
  - Exception: View qui permet de visualiser, d'ajouter ou modifier des dérogations à un équipement.
  - Hebdo: View qui permet de visualiser et paramétrer les périodes classiques d'activités pour un équipement
  - Hours_embed: View qui sert à afficher les heures à coté de l'affichage des jours (Day_Embed)
  - Plannings: View globale qui reprend l'ensemble des éléments à travers un tableau
  - Popup_Edition: View qui est utilisé pour le paramétrage des périodes hebdomadaire ou dérogatoire
  - _Plannings: View qui reprend la View planning en mode EmbedView. C'est cet view qui faudra dupliquer et adapter en fonction du site.
  - Utils/SQL_Equipements: View qui sert à créer les tables nécessaires au module et ajouter des équipements à la base de données.
  - Utils/SQL_Rename: View qui permet de renommer un site, groupe ou équipement.
