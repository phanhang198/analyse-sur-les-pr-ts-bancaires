# ANALYSE SUR LES PRÊTS BANCAIRES

## 1. Contexte

Les prêts bancaires permettent aux particuliers et entreprises d’atteindre leurs objectifs financiers. Pour une gestion efficace, il est essentiel de comprendre les conditions, coûts et responsabilités liés aux prêts.

---

## 2. Sources de données

* **Demandes de prêt** : Informations personnelles et financières fournies par l’emprunteur.
* **Rapports de crédit** : Historique et solvabilité de l’emprunteur.
* **Registres internes** : Décaissements, remboursements, statut des prêts.
* **Portails en ligne** : Demandes et paiements effectués via les plateformes digitales.
* **Sources externes** : Vérification des revenus ou données additionnelles.

---

## 3. Processus d’octroi d’un prêt

1. **Demande** : Soumission en ligne ou en agence.
2. **Examen** : Vérification des documents et informations.
3. **Vérification identité** : Prévenir le vol d’identité.
4. **Vérification crédit** : Évaluation de l’historique et du score de crédit.
5. **Vérification revenus** : Analyse de la capacité de remboursement.
6. **Ratio dette/revenu (DTI)** : Ratio des dettes mensuelles sur revenus mensuels.
7. **Vérification emploi** : Stabilité de l’emploi.
8. **Évaluation garanties** (si applicable) : Valeur et état des collatéraux.
9. **Évaluation du risque** : Crédit, revenus et objectif du prêt.
10. **Décision** : Approbation ou refus, définition du montant, taux et conditions.
11. **Contrat de prêt** : Conditions détaillées et calendrier de remboursement.
12. **Décaissement** : Fonds versés à l’emprunteur.
13. **Remboursement** : Paiements réguliers du principal et des intérêts.
14. **Suivi continu** : Surveillance des paiements et gestion des défauts.

---

## 4.Appliquer Le Design Thinking au risque crédit avec ce dataset.

---
# 🎯 1️⃣ EMPATHIZE — Comprendre le problème réel

### 👥 Les utilisateurs finaux :

* Analystes crédit
* Comité risque
* Direction financière

### ❓ Les vraies questions :

* Pourquoi certains prêts deviennent **Charged Off** ?
* Peut-on détecter le risque AVANT l’octroi ?
* Quelles variables discriminent le plus ?
* Où perd-on le plus d’argent ?
---

# 🧠 2️⃣ DEFINE — Définir le vrai problème
 “Réduire le taux de Charged Off tout en maintenant la rentabilité.”

Donc on dois analyser :

* Taux de défaut par grade
* Rentabilité par segment
* Perte moyenne par défaut (LGD approximée)
---

# 💡 3️⃣ IDEATE — Générer des solutions

À partir du dataset, on peut créer :

### 📊 A. Segmentation Risque

* Par grade                    * Par DTI bucket
* Par revenu                   * Par durée (36 vs 60 months)

Exemple d’insight possible :

* Grade C + DTI > 0.30 → défaut x3
* 60 months → plus risqué que 36 months

---

### 📈 B. Construire un score interne

Créer un score basé sur :

* DTI
* Grade
* Income
* Loan_amount / income ratio

Puis classer :

* Low risk
* Medium risk
* High risk

---

### 💰 C. Ajuster la politique crédit

Par exemple :

| Segment     | Action            |
| ----------- | ----------------- |
| High risk   | Refus             |
| Medium risk | Taux plus élevé   |
| Low risk    | Validation rapide |

---

# 🧪 4️⃣ PROTOTYPE — Tester une solution

Tu peux :

* Construire un modèle logistique
* Tester un cut-off score
* Simuler l’impact :

Exemple :

> Si on refuse les scores > 6 → combien de pertes évitées ?
> Quel impact sur le volume business ?

---

# 📊 5️⃣ TEST — Mesurer l’impact réel

Indicateurs clés :

* Default Rate
* Expected Loss = PD × LGD × EAD
* Profit net
* Acceptance rate


Nous allons procéder l'analyse en fonction de ces 5 insights:
📊 1️⃣ Analyse du risque (Risk Analytics)
🔎 A. Taux de défaut par grade / sub_grade
Colonnes utilisées :
•	grade
•	sub_grade
•	loan_status
Insight :
•	Quel grade a le plus de Charged Off ?
•	Les sub_grades les plus risqués ?
👉 Permet d’identifier les profils à haut risque.
Requête SQL
<img width="861" height="202" alt="image" src="https://github.com/user-attachments/assets/5b85b27f-e39c-4d7b-81af-5beab2baf4dc" />
Résultat
<img width="821" height="244" alt="image" src="https://github.com/user-attachments/assets/07188ae1-a262-4430-b86a-2205088369eb" />



________________________________________
🔎 B. Défaut par DTI (Debt-to-Income)
Colonnes :
•	dti
•	loan_status
Insight :
•	Plus le DTI est élevé → plus le risque augmente ?
•	Déterminer un seuil critique (ex: DTI > 35%)
________________________________________
🔎 C. Défaut par revenu annuel
Colonnes :
•	annual_income
•	loan_status
Insight :
•	Les revenus faibles ont-ils un taux de défaut plus élevé ?
Requête SQL 
<img width="969" height="264" alt="image" src="https://github.com/user-attachments/assets/1aca7812-1ed3-4463-93a4-a9b316e475ba" />

Résultat
<img width="632" height="114" alt="image" src="https://github.com/user-attachments/assets/e9e44540-e78c-42db-910e-c51848a98132" />


________________________________________
💰 2️⃣ Performance financière
🔎 A. Rentabilité par grade
Colonnes :
•	int_rate
•	loan_amount
•	total_payment
•	loan_status
Insight :
•	Les prêts à taux élevé compensent-ils le risque ?
•	Quel grade génère le plus de profit ?
________________________________________
🔎 B. Montant total prêté par État
Colonnes :
•	address_state
•	loan_amount
Insight :
•	États avec plus forte activité
•	Concentration géographique du portefeuille
________________________________________
🏠 3️⃣ Profil client
🔎 A. Home Ownership vs Default
Colonnes :
•	home_ownership
•	loan_status
Insight :
•	Les propriétaires sont-ils moins risqués que les locataires ?
Requête SQL
<img width="610" height="166" alt="image" src="https://github.com/user-attachments/assets/d59e2af3-1681-4eb0-bd4c-cf796e9d7f23" />

Résultat
<img width="602" height="136" alt="image" src="https://github.com/user-attachments/assets/7da2d5d2-f7cc-4c99-a709-e9a641089e88" />


________________________________________
🔎 B. Type d’application
Colonnes :
•	application_type
Insight :
•	Joint Application vs Individual
•	Qui rembourse mieux ?
________________________________________
🔎 C. Ancienneté emploi vs risque
Colonnes :
•	emp_length
•	loan_status
Insight :
•	Plus d’années d’emploi = moins de défaut ?
________________________________________
📅 4️⃣ Analyse temporelle
🔎 A. Volume des prêts par date d’émission
Colonnes :
•	issue_date
•	loan_amount
Insight :
•	Croissance mensuelle (MTD, PMTD, YTD)
•	Saisonnalité
________________________________________
🔎 B. Retards de paiement
Colonnes :
•	last_payment_date
•	next_payment_date
•	loan_status
Insight :
•	Taux de retard
•	Détection des comptes à risque
________________________________________
🎯 5️⃣ Analyse par Purpose (objectif du prêt)
Colonne :
•	purpose
Insight :
•	Quel type de prêt a le plus de défaut ? (debt consolidation ? credit card ?)
•	Quel purpose génère le plus de revenus ?

