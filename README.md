# Module Planning
  
## Utilisation

Pour utiliser le module Planning il faut importer les scripts, styles et views contenu dans le fichier *.zip* avec le Designer d'Ignition.
Il faudra également importer le template *Flex_Button*.

## Utilisation du Planning via Perspective



### Gestion des périodes hebdomadaire



### Gestion des périodes dérogatoires



### Affichage des dérogations à partir de la date du jour



### Calendrier d'un équipement hebdomaire et dérogations incluse



## Ajout d'équipement à la base de données via le designer



## Renommer un site, groupe ou equipement de la base de données



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

# Requetes SQL via le Data Query Browser

## Requêtes basiques

ℹ️ Il est possible d'entrer des requêtes SQL via la fonctionnalité **Database Query Browser** *(dans Tools)* d'Ignition. Afin d'executer une requête SQL, il faut entrer la commande dans la zone à gauche du bouton *Execute* puis cliquer sur ce même bouton.

Dans cette rubrique, les requêtes pourront être simplement copier-coller et executer.

### Creation des tables SQL

```
CREATE TABLE equipements
(
  site TEXT,
  groupe TEXT,
  equipement TEXT
)
```

```
CREATE TABLE plannings
(
  h_start TEXT,
  m_start TEXT,
  h_stop TEXT,
  m_stop TEXT,
  plage INT,
  jour INT,
  site TEXT,
  groupe TEXT,
  equipement TEXT
)
```

```
CREATE TABLE plannings_exception
(
  h_start TEXT,
  m_start TEXT,
  h_stop TEXT,
  m_stop TEXT,
  date_deb TEXT,
  date_fin TEXT,
  plage INT,
  site TEXT,
  groupe TEXT,
  equipement TEXT,
  commentaire TEXT
)
```

#### Utilisation de l'écriture des plannings en modbus

```
ALTER TABLE equipements
ADD COLUMN num_mb INT
```

#### Utilisation de l'écriture des plannings avec devIO

```
ALTER TABLE equipements
ADD COLUMN id_devio INT
```

### Vider une table SQL

Pour vider une table sql il faudra entrer la commande `TRUNCATE TABLE nom_table` où le nom_table correspond au nom de la table à vider.

🚨 Attention : les données seront supprimées.

### Supprimer une table SQL

Pour supprimer une table sql il faudra entrer la commande `DROP TABLE nom_table` où le nom_table correspond au nom de la table à vider.

🚨 Attention : les données seront supprimées.

## Requêtes avancées

⚠️ Dans cette rubrique, il sera nécessaire de modifier certaines informations avant d'executer la requête : numero_modbus, nom_site, nom_groupe, nom_equipement, numero_id_devio, nom_devio.

### Equipement déjà présent dans la base de données

#### Ajouter un numéro modbus 

```
UPDATE equipements 
SET 
  num_mb = numero_modbus
WHERE site = 'nom_site'
AND groupe = 'nom_groupe'
AND equipement = 'nom_equipement'
```

Si le site n'est pas présent dans la table devices, il faudra également entrer la commande suivante : 
```
Insert into devices (nom_device, nom_site) Values ('nom_device', 'nom_site')
```

#### Ajouter un id DevIO

```
UPDATE equipements 
SET 
  id_devio = numero_id_devio
WHERE site = 'nom site'
AND groupe = 'nom groupe'
AND equipement = 'non_equipement'
```
