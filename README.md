# Analyser le taux de churn

## Contexte général 📌

Author: Hang NGUYEN  
Tool Used: SQL, PowerBi

Ce jeu de données contient des informations détaillées sur les clients d’une entreprise de services de télécommunications. L’objectif principal est d’analyser le taux de churn 
(attrition client), c’est-à-dire la proportion de clients ayant quitté l’entreprise sur une période donnée, et d’identifier les facteurs explicatifs de ce départ.

Chaque ligne du tableau représente un client unique, identifié par Customer_ID, et décrit son profil démographique, son niveau d’engagement, les services souscrits,
ainsi que les aspects contractuels et financiers liés à sa relation avec l’entreprise.

🧾 Description des dimensions du jeu de données
1. Profil démographique et géographique

Gender, Age, Married, State
Ces variables permettent d’analyser si le churn varie selon l’âge, le genre, la situation familiale ou la localisation géographique.

2. Relation client et ancienneté

Tenure_in_Months : durée de la relation client

Number_of_Referrals : nombre de recommandations effectuées

Ces indicateurs mesurent la fidélité et l’engagement du client, souvent fortement corrélés au churn.

3. Services souscrits

Services télécom : Phone_Service, Multiple_Lines, Internet_Service, Internet_Type

Services additionnels : Online_Security, Online_Backup, Device_Protection_Plan, Premium_Support

Divertissement et data : Streaming_TV, Streaming_Movies, Streaming_Music, Unlimited_Data

Ces colonnes permettent d’identifier quels services ou combinaisons de services sont associés à un risque de churn plus élevé.

4. Conditions contractuelles et facturation

Contract : type de contrat (mensuel, annuel, etc.)

Paperless_Billing, Payment_Method

Ces variables sont clés pour comprendre l’impact des modalités contractuelles et de paiement sur la rétention client.

5. Données financières

Monthly_Charge, Total_Charges

Total_Refunds, Total_Extra_Data_Charges, Total_Long_Distance_Charges

Total_Revenue

Elles permettent d’évaluer la relation entre valeur financière du client, coûts supplémentaires et probabilité de churn.

6. Indicateurs de churn

Customer_Status : client actif ou churné

Churn_Category : type de churn (concurrent, prix, service, etc.)

Churn_Reason : raison précise du départ

Ces champs constituent la variable cible de l’analyse et permettent une approche à la fois quantitative (taux de churn) et qualitative (causes du churn).

#### ❓ Enjeux métiers :

1 / Calculer le taux global de churn

2 / Identifier les segments clients à fort risque

3 / Comprendre les principales causes du churn

4 / Déterminer les leviers d’action pour améliorer la rétention client

