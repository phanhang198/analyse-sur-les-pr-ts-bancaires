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

Donc, on doit analyser le taux de défaut en fonction des éléments principaux comme le grade, le revenu, le terme du prêt et le statut de propriété.

* 📊 Quick analytic :
Quel est le taux de "Charged Off"?<br>

Requête SQL<br>
<img width="621" height="87" alt="image" src="https://github.com/user-attachments/assets/4e129921-30cc-4904-b67d-053575f09fe0" /><br>

Résultat<br>
<img width="405" height="94" alt="image" src="https://github.com/user-attachments/assets/32d63830-43f6-4d7c-8993-59b9eb2669c1" /><br>

Donc,ici le taux de défaut est presque 14%, assez élevé dans la gestion de crédit. Notre objectif est de baisser au 8-10%.


* 📊 1️⃣ Analyse du risque (Risk Analytics)
🔎 A. Taux de défaut par grade / sub_grade
Colonnes utilisées :
•	grade
•	sub_grade
•	loan_status
Insight :
•	Quel grade a le plus de Charged Off ?
•	Les sub_grades les plus risqués ?
👉 Permet d’identifier les profils à haut risque.
  
Requête SQL<br>  
<img width="861" height="202" alt="image" src="https://github.com/user-attachments/assets/5b85b27f-e39c-4d7b-81af-5beab2baf4dc" /><br>

Résultat<br>
<img width="821" height="244" alt="image" src="https://github.com/user-attachments/assets/07188ae1-a262-4430-b86a-2205088369eb" /><br>

---
🔎 B. Défaut par revenu annuel
Colonnes :
•	annual_income
•	loan_status
Insight :
•	Les revenus faibles ont-ils un taux de défaut plus élevé ?
Requête SQL<br> 
<img width="969" height="264" alt="image" src="https://github.com/user-attachments/assets/1aca7812-1ed3-4463-93a4-a9b316e475ba" /><br>

Résultat<br>
<img width="632" height="114" alt="image" src="https://github.com/user-attachments/assets/e9e44540-e78c-42db-910e-c51848a98132" /><br>

🔎 C. Home Ownership vs Default
Colonnes :
•	home_ownership
•	loan_status
Insight :
•	Les propriétaires sont-ils moins risqués que les locataires ?
Requête SQL<br>
<img width="610" height="166" alt="image" src="https://github.com/user-attachments/assets/d59e2af3-1681-4eb0-bd4c-cf796e9d7f23" /><br>

Résultat<br>
<img width="602" height="136" alt="image" src="https://github.com/user-attachments/assets/7da2d5d2-f7cc-4c99-a709-e9a641089e88" /><br>

🔎 D. Term vs Default
Colonnes :
• term
•	loan_status
Insight :
•	Les prêts à long terme présentent un risque plus élevé que les prêts à court terme.
Requête SQL<br>
<img width="777" height="164" alt="image" src="https://github.com/user-attachments/assets/a71aa542-6f34-43aa-9099-2ccb77ea9f27" /><br>

Résultat<br>
<img width="958" height="87" alt="image" src="https://github.com/user-attachments/assets/6ac747e2-e950-4958-a91d-29bb770de93d" />

🔎 E. DTI vs Default
Colonnes :
• dti
•	loan_status
Insight :
•	Les dti élevé présentent un risque plus élevé que les dti bas.
Requête SQL<br>
<img width="717" height="457" alt="image" src="https://github.com/user-attachments/assets/3ac250e2-182e-44d2-a2ae-cd634a412848" /><br>

Résultat<br>
<img width="840" height="111" alt="image" src="https://github.com/user-attachments/assets/54758f06-3965-41af-86f3-4ac9450a9744" /><br>

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
* Puis classer :

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

Requête SQL <br>
```sql
with scoring as (
select id, grade, fl.annual_income, fl.home_ownership,fl.term ,dti,
		case 
			when grade = 'A' then 1
			when grade = 'B' then 2
			when grade = 'C' then 3
			when grade = 'D' then 4
			when grade = 'E' then 5
			when grade = 'F' then 6
			when grade = 'G' then 7
		end as score_grade,
		case 
			when annual_income < 50000 then 4
			when annual_income between 50000 and 100000 then 3
			when annual_income between 100000 and 1000000 then 2
			when annual_income > 1000000 then 1
		end as score_income,
		case
			when home_ownership = 'MORTGAGE' or home_ownership = 'OWN'  then 1
			when fl.home_ownership = 'RENT' then 2
			when home_ownership = 'OTHER' or home_ownership = 'NONE'  then 3
		end as score_homeowner,
		case
			when dti > 0.27 or dti < 0.07 then 1
			when dti between 0.20 and 0.27 then 2
			when dti between 0.07 and 0.13 then 3
			when dti between 0.13 and 0.20 then 4		
		end as score_dti		
from finance.financial_loan fl
		),
seg_scoring as 
(select *, (score_grade + score_income + score_homeowner + score_dti) as score_total from scoring)

select id,grade, annual_income, home_ownership,dti,score_total,
		case 
			when score_total <=5 then 'Low risk -> Validation rapide'
			when score_total between 5 and 10 then 'Medium risk -> Taux plus élevé'
			else 'High risk -> Potential refus'
		end		
from seg_scoring;
```

Résultat<br>
<img width="971" height="334" alt="image" src="https://github.com/user-attachments/assets/ed56895c-d5c5-494b-b467-41124aeed05e" /><br>


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
