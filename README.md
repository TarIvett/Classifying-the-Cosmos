# Classifying the Cosmos: Identificarea Obiectelor Cerești din Date Spectrale

## Autor
- **Nume:** Tar Ivett-Dora  
- **Sursă Date:** Sloan Digital Sky Survey (SDSS DR17) via Kaggle  

---

## Descriere proiect

Acest proiect investighează dacă profilul luminos al unui obiect ceresc, măsurat prin filtre fotometrice:

- ultraviolet (u)
- verde (g)
- roșu (r)
- infraroșu (i, z)

poate fi utilizat pentru a clasifica obiectul în una dintre următoarele categorii:

- Stea (STAR)
- Galaxie (GALAXY)
- Quasar (QSO)

Studiul utilizează date din **SDSS DR17** și analizează performanța mai multor algoritmi de Machine Learning pe un set de date complex și dezechilibrat.

---

## Structura pipeline-ului

Fluxul de lucru este organizat riguros, de la date brute la evaluare finală:

### 1. Exploratory Data Analysis (EDA)
- Analiza distribuțiilor și corelațiilor
- Identificarea valorilor „sentinel” (-9999) în filtrele fotometrice

### 2. Data Cleaning
- Eliminarea identificatorilor unici (ID-uri)
- Filtrarea valorilor fizic eronate

### 3. Feature Engineering
- Crearea indicilor de culoare:
  - $u - g$
  - $g - r$
- Capturarea formei spectrale a obiectelor, nu doar a luminozității brute

### 4. Preprocessing
- Imputare cu mediană
- Scalare standard (Standard Scaling)
- Codificarea etichetelor (Label Encoding)

### 5. Data Splitting
- Împărțire stratificată:
  - Train: 60%
  - Validation: 20%
  - Test: 20%
- Menținerea proporțiilor claselor

---

## Stack Tehnologic

- **Limbaj:** Python 3.15 
- **Manipulare date:** pandas, numpy  
- **Vizualizare:** matplotlib, seaborn  
- **Machine Learning:** scikit-learn  

### Algoritmi utilizați:
- Logistic Regression
- Decision Trees
- Random Forest
- AdaBoost
- Gradient Boosting
- Stacking Classifier

---

## Modele analizate și performanță

| Model | Caracteristici cheie |
|------|----------------------|
| Logistic Regression | Baseline liniar; regularizare L1 (Lasso) și L2 (Ridge) |
| Decision Trees | Pre-pruning (depth) și post-pruning (ccp_alpha) |
| Random Forest | Ensemble robust bazat pe bootstrap și selecție aleatoare de features |
| Gradient Boosting | Învățare iterativă a erorilor reziduale; eficient pentru separarea Galaxy–Quasar |
| Stacking Classifier | Meta-model ce combină Logistic Regression, Random Forest și Gradient Boosting |

---

## Concluzii științifice

- **Dominanța Redshift-ului**
  - Redshift-ul este cea mai puternică variabilă
  - Separă eficient:
    - stelele locale ($z \approx 0$)
    - galaxiile și quasarii îndepărtați

- **Valoarea indicilor de culoare**
  - Diferențele între filtre (ex: $u - g$) sunt esențiale
  - Ajută la identificarea quasarilor cu emisii UV atipice

- **Provocarea clasificării**
  - Suprapunerea fotometrică între:
    - galaxii îndepărtate
    - quasari
  - reprezintă cea mai dificilă frontieră pentru modele

---
