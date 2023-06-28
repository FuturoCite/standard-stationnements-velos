# Schéma des stationnements vélos
Ce schéma permet de modéliser les différents attributs des stationnements vélos 

## Contexte

Il existe un besoin d'harmonisation de la publication en open data de données essentielles produites par les administrations publiques wallonnes. En octobre 2022, plus de 660 jeux de données sont publiés sur le portail [Open Data Wallonie Bruxelles (ODWB)](https://www.odwb.be/explore/?sort=modified), qui sont très hétérogènes. 

Constatant la production de jeux de données disparates à l'échelle de la fédération Wallonie-Bruxelles, FuturoCité a réuni, dans le cadre d'un groupe de travail sollicité depuis mai 2021, une vingtaine de collectivités. La concertation de celles-ci a permis 1) d'identifier collectivement des jeux de données jugés prioritaires et 2) de s'accorder sur des spécifications des modèles de données. 
La standardisation de ces données prioritaires est en effet essentielle pour s'assurer de leur publication homogène et de faciliter leur exploitation (notamment leur agrégation) par les réutilisateurs. Elle facilitent l'exploitation des données publiées par les réutilisateurs (agrégation, consolidation et traitements automatiques).

## Construction du schéma de données 

Les membres du groupe de travail ont défini un schéma de données qui décrit le format des fichiers, les différents champs, les valeurs possibles… Ils se sont appuyés sur un état des lieux du patrimoine de données des collectivités wallonnes et sur une étude des modèles utilisés par des collectivités déjà productrices de ces données (notamment Liège et Namur), en prenant en compte les retours faits par les réutilisateurs de données. 


## Description du schéma

Un [gabarit au format tableur](https://github.com/FuturoCite/standard-stationnements-velos/blob/main/Schema_stationnements_velos_gabarit.xlsx) est également prévu pour faciliter la publication d'un jeu de données conforme au format du schéma.

Un exemple valide au format CSV est consultable [ici](https://github.com/FuturoCite/standard-stationnements-velos/blob/main/exemple-valide.csv).  

Le tableau ci-dessous donne un aperçu des champs du schéma. 

<table>
  <tr>
   <td><strong>Nom</strong>
   </td>
   <td><strong>Remplissage obligatoire/optionnel</strong>
   </td>
   <td><strong>Description</strong>
   </td>
  </tr>
  <tr>
   <td>Identifiant 
   <br>(id) 
   </td>
   <td>Obligatoire
   </td>
   <td>Ce champ contient un identifiant unique local. Le producteur de données le génère en associant le code INS de la commune dans laquelle se situe l'emplacement vélos à un nombre. Ce champ permet d'éviter localement les doublons. Le code INS de la commune est accessible ici : https://statbel.fgov.be/fr/open-data/code-refnis
   </td>
  </tr>
  <tr>
   <td>Nom de la commune 
   <br>(municipality)
   </td>
   <td>Obligatoire
   </td>
   <td>Ce champ contient le nom de la commune dans laquelle se situe l'emplacement vélo. Le nom de la commune provient de la base de données BeST Address : https://opendata.bosa.be/index.fr.html ou de la liste des codes INS : https://statbel.fgov.be/fr/open-data/code-refnis
   </td>
  </tr>
  <tr>
   <td>Code INS 
   <br>(ins_code)
   </td>
   <td>Obligatoire
   </td>
   <td>Ce champ contient le code INS de la commune où se situe le sationnement vélo. Il est accessible ici : https://statbel.fgov.be/fr/open-data/code-refnis
   </td>
  </tr>
  <tr>
   <td>Partie de commune 
   <br>(zone_address)
   </td>
   <td>Optionnel
   </td>
   <td>Ce champ continent le nom de la partie de commune où se situe le stationnement vélos, conforme à l'appelation dans StatBel : https://statbel.fgov.be/fr/propos-de-statbel/methodologie/classifications/geographie
   </td>
  </tr>
  <tr>
   <td>Code INS de la partie de commune 
   <br>(ins_zone_address)
   </td>
   <td>Optionnel
   </td>
   <td>Ce champ contient le code INS de la partie de commune où se situe l'emplacement vélos. La découpe géographique de StatBel Level 5 (NIS6) liste ces codes : https://statbel.fgov.be/fr/propos-de-statbel/methodologie/classifications/geographie
   </td>
  </tr>
  <tr>
   <td>Nom de rue 
   <br>(street_name)
   </td>
   <td>Obligatoire
   </td>
   <td>Ce champ indique le nom de la voirie où se situe le stationnement vélo (ou de la voirie la plus proche du stationnement vélo si l'emplacement n'est pas en voirie)
   </td>
  </tr>
  <tr>
   <td>Code rue BeSTAddress 
   <br>(street_number)
   </td>
   <td>Obligatoire
   </td>
   <td>Ce champ contient le code de la voirie où se situe l'emplacement dans la base de données BeSTAdress (ou de la voirie la plus proche du stationnement s'il n'est pas en voirie) :<a href="https://opendata.bosa.be/index.fr.html"> https://opendata.bosa.be/index.fr.html</a>
   </td>
  </tr>
  <tr>
   <td>Code rue national 
   <br>(street_number_rrn)
   </td>
   <td>Optionnel
   </td>
   <td>Code de la voirie où se situe le sationnement dans le registre national (ou de la voirie la plus proche si l'emplacement n'est pas en voirie)
   </td>
  </tr>
  <tr>
   <td>Numéro de police le plus proche 
   <br>(house_number)
   </td>
   <td>Optionnel (recommandé)
   </td>
   <td>Ce champ est recommandé. Il contient le numéro de police (numéro de maison) le plus proche du stationnement.
   </td>
  </tr>
  <tr>
   <td>Distance au point d'adresse 
   <br>(distance)
   </td>
   <td>Optionnel
   </td>
   <td>Ce champ indique la distance, en mètres, entre le stationnement vélo et le point d'adresse le plus proche introduit via les autres champs (code_rue_bestadress, num_police, …). En cas de décimale, le séparateur est le point.
   </td>
  </tr>
  <tr>
   <td>Coordonnées 
   <br>(coordinates)
   </td>
   <td>Obligatoire
   </td>
   <td>Ce champ indique les coordonnées de l'emplacement vélos. Il est au format GeoJSON (se référer au fichier csv d'exemple et/ou à la documentation pour un exemple de valeur bien formatée). S'il est impossible d'exporter la donnée depuis un logiciel métier, les coordonnées d'un lieu peuvent être générées ici : https://www.coordonnees-gps.fr/carte/pays/BE
   </td>
  </tr>
  <tr>
   <td>Précisions sur la localisation 
   <br>(location_details)
   </td>
   <td>Optionnel
   </td>
   <td>Ce champ précise tout information jugée utile sur l'emplacement du stationnement vélo.
   </td>
  </tr>
  <tr>
   <td>Type de stationnement 
   <br>(parking_type)
   </td>
   <td>Obligatoire
   </td>
   <td>Ce champ indique le type de stationnement. Les valeurs possibles sont : Arceau ; Rack ; Box ; Autre
   </td>
  </tr>
  <tr>
   <td>Précisions sur le type de stationnement 
   <br>(parking_type_details)
   </td>
   <td>Optionnel
   </td>
   <td>Ce champ donne des précisions relatives au type de stationnement.
   </td>
  </tr>
  <tr>
   <td>Couvert 
   <br>(covered)
   </td>
   <td>Obligatoire
   </td>
   <td>Ce champ indique si l'emplacement du stationnement vélo est couvert (true) ou non (false). Si non applicable/non connu : ne pas renseigner ce champ.
   </td>
  </tr>
  <tr>
   <td>Sécurisé 
   <br>(secured)
   </td>
   <td>Optionnel
   </td>
   <td>Ce champ indique si l'emplacement du stationnement vélo est sécurisé (true) ou non (false). Un emplacement sécurisé est par exemple surveillé par une caméra, ou cadenassé. Si non applicable/non connu : ne pas renseigner ce champ.
   </td>
  </tr>
  <tr>
   <td>Type de sécurité 
   <br>(security_type)
   </td>
   <td>Optionnel
   </td>
   <td>Ce champ décrit le type de sécurité du stationnement.
   </td>
  </tr>
  <tr>
   <td>Nombre de places 
   <br>(available_places)
   </td>
   <td>Obligatoire
   </td>
   <td>Ce champ indique le nombre de places présentes sur l'emplacement de stationnement vélo.
   </td>
  </tr>
  <tr>
   <td>Nombre de supports 
   <br>(available_bicycle_racks)
   </td>
   <td>Optionnel
   </td>
   <td>Ce champ précise le nombre de supports présents sur l'emplacement de stationnement vélo.
   </td>
  </tr>
  <tr>
   <td>Année d'installation 
   <br>(installation_year)
   </td>
   <td>Optionnel
   </td>
   <td>Ce champ indique l'année d'installation du stationnement vélo.
   </td>
  </tr>
  <tr>
   <td>Gestionnaire 
   <br>(provider)
   </td>
   <td>Optionnel
   </td>
   <td>Ce champ indique le nom du gestionnaire du stationnement vélo.
   </td>
  </tr>
  <tr>
   <td>Photo 
   <br>(picture)
   </td>
   <td>Optionnel
   </td>
   <td>Ce champ contient une url renvoyant à une photo du stationnement vélo
   </td>
  </tr>
  <tr>
   <td>Borne de recharge 
   <br>(charging_station)
   </td>
   <td>Obligatoire
   </td>
   <td>Ce champ indique la présence (true) ou non (false) d'une borne de rechargement de vélos électriques. Si non applicable/non connu : ne pas renseigner ce champ.
   </td>
  </tr>
  <tr>
   <td>Matériel de réparation 
   <br>(repair_equipment)
   </td>
   <td>Optionnel
   </td>
   <td>Ce champ indique la présence (true) ou non (false) de matériel de réparation. Si non applicable/non connu : ne pas renseigner ce champ.
   </td>
  </tr>
  <tr>
   <td>Date de création de la donnée 
   <br>(created_date)
   </td>
   <td>Optionnel (recommandé)
   </td>
   <td>Ce champ indique la date de création de la donnée dans le jeu. Il respecte le format ISO 8601 : année-mois-jour (YYYY-MM-DD)
   </td>
  </tr>
  <tr>
   <td>Date de dernière modification de la donnée 
   <br>(last_modified_date)
   </td>
   <td>Optionnel (recommandé)
   </td>
   <td>Ce champ indique la date de la dernière modification de la donnée dans le jeu. Il respecte le format ISO 8601 : année-mois-jour (YYYY-MM-DD).
   </td>
  </tr>
</table>

## Format de fichier 

Le format de fichier retenu pour la publication des données est le CSV (Comma Separated Values, valeurs séparées par des virgules).

Les fichiers doivent, sauf exception et autant que possible, respecter les règles de formatage suivantes :

* l’encodage des caractères est UTF-8,
* le séparateur des colonnes est la virgule,
* le séparateur des nombres décimaux est le point,
* le séparateur de valeurs multiples dans un champ est le point-virgule,
* si un champ contient une virgule, il doit être entouré de guillemets doubles,
* chaque ligne doit avoir le même nombre de champs,
* le type MIME ou Content-Type est text/csv.

### Recommandation pour le nommage des fichiers 

Les fichiers doivent, sauf exception et autant que possible, respecter les règles de nommage suivantes :

* YYYY-MM-DD : Date de création du fichier
* idProducteur : code INS unique de la commune pour identifier le producteur
* stationnement-velos : nom du fichier, en minuscules non accentuées
* territoire : Nom du territoire concerné, non accentué (exemple : Liege)
* extension : Si les règles de formatage sont respectées, l'extension est .csv

Exemple : 2022-10-25_62063_stationnement-velos_Liege.csv

### Recommandation pour la mise en conformité 

Ces conseils reprennent ceux des schémas standards de données français publié par [l'initiative de data.gouv.fr](https://schema.data.gouv.fr/).

Les fichiers doivent comporter :

* Toutes les colonnes, y compris celles dont les cellules ne sont pas renseignées, dans le bon ordre, et avec des en-têtes correctement nommées sur la première ligne (nom correspondant strictement au schéma)
* Autant de lignes que nécessaire comprenant des cellules dont les valeurs peuvent être obligatoires (elles doivent être impérativement renseignées) ou optionnelles (elles sont seulement recommandées ou soumises à condition de disponibilité / pertinence)

