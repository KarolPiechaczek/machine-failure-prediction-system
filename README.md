# 🏭 System Przewidywania Awarii Maszyn / Predictive Maintenance System

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-EE4C2C)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Machine%20Learning-F7931E)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458)

[English version below]

## 🇵🇱 O Projekcie
**Predictive Maintenance System** to projekt z dziedziny Machine Learning i Deep Learning, którego celem jest przewidywanie awarii maszyn przemysłowych na podstawie danych z czujników (zbiór danych AI4I 2020). Projekt skupia się na rozwiązaniu klasycznego problemu przemysłowego: pracy z mocno niezbalansowanym zbiorem danych (awarie stanowią zaledwie 3.39% przypadków) oraz optymalizacji modelu pod kątem realnych kosztów biznesowych.

Rozwiązanie przeprowadza użytkownika przez pełen cykl życia modelu (ML Lifecycle): od analizy i inżynierii cech, przez budowę modelu bazowego (Baseline), aż po wdrożenie i ewaluację własnej sieci neuronowej.

### Główne etapy i funkcjonalności
* **Inżynieria Cech (Feature Engineering):** Zapobieganie wyciekowi danych (Data Leakage) oraz tworzenie nowych, fizycznie sensownych cech z perspektywy inżyniera (Różnica temperatur, Szacowana generowana moc).
* **Model Bazowy (Scikit-Learn):** Wdrożenie klasyfikatora `RandomForest` wewnątrz profesjonalnego obiektu `Pipeline` (ze skalowaniem danych) jako punktu odniesienia.
* **Deep Learning (PyTorch):** Zbudowanie sieci neuronowej (Multi-Layer Perceptron) wykorzystującej architekturę w pełni połączonych warstw (Fully Connected Layers).
* **Obsługa Niezbalansowanych Danych:** Zastosowanie wag klas (`class_weight='balanced'` w ML oraz `pos_weight` w algorytmie funkcji straty `BCEWithLogitsLoss` w DL).

### Wyniki i Wnioski Biznesowe (Precision-Recall Tradeoff)
Zamiast ślepo optymalizować dokładność (Accuracy), która przy niezbalansowanych danych bywa myląca, projekt skupia się na biznesowych kosztach błędów:

1. **Random Forest (Baseline):** Osiągnął wysoką precyzję (**94%**), ale przepuścił część awarii (Czułość/Recall: **74%**).
2. **PyTorch Neural Network:** Został celowo "ukarany" za przeoczenia za pomocą parametru `pos_weight`. Skutkowało to drastycznym wzrostem Czułości (Recall: **90% - 93%**) kosztem spadku precyzji (**32%**). 

**Wniosek:** W fabryce (Predictive Maintenance) przeoczenie awarii (False Negative) oznacza zepsutą maszynę, wstrzymanie linii produkcyjnej i ogromne straty finansowe. Fałszywy alarm (False Positive) oznacza jedynie konieczność taniej, rutynowej inspekcji przez technika. Dlatego model PyTorch, mimo niższej ogólnej precyzji, jest rozwiązaniem znacznie bezpieczniejszym i tańszym we wdrożeniu komercyjnym.

---

### Instalacja i Uruchomienie

1.  **Wymagania:** Python 3.8+ oraz biblioteki z pliku `requirements.txt`.
    ```bash
    pip install -r requirements.txt
    ```

2.  **Uruchomienie:**
    Uruchom środowisko Jupyter i otwórz główny notatnik projektu:
    ```bash
    jupyter notebook machine_failure_prediction.ipynb
    ```

### Struktura Projektu

```text
├── machine_failure_prediction.ipynb  # Główny notatnik z EDA, modelem RF i PyTorch
├── predictive_maintenance_model.pth  # Zapisane wagi wytrenowanej sieci neuronowej
└── requirements.txt                  # Lista zależności (Pandas, Scikit-Learn, PyTorch itp.)
```

---

## 🇬🇧 About the Project
**Predictive Maintenance System** is a Machine Learning and Deep Learning project aimed at predicting industrial machine failures based on sensor data (AI4I 2020 dataset). The project focuses on solving a classic industrial challenge: working with a highly imbalanced dataset (failures account for only 3.39% of cases) and optimizing the model for real-world business costs.

The solution walks through the entire ML Lifecycle: from Exploratory Data Analysis (EDA) and Feature Engineering, through building a Baseline model, to implementing and evaluating a custom Neural Network.

### Key Features
* **Feature Engineering:** Preventing Data Leakage and engineering new, physically meaningful features from an engineering perspective (Temperature difference, Estimated generated power).
* **Baseline Model (Scikit-Learn):** Implementing a `RandomForest` classifier within a professional `Pipeline` object (including data scaling) as a benchmark.
* **Deep Learning (PyTorch):** Building a Neural Network (Multi-Layer Perceptron) utilizing a Fully Connected Layers architecture.
* **Imbalanced Data Handling:** Applying class weights (`class_weight='balanced'` in ML and `pos_weight` in the `BCEWithLogitsLoss` function in DL).

### Results & Business Conclusions (Precision-Recall Tradeoff)
Instead of blindly optimizing Accuracy, which is misleading with imbalanced data, the project focuses on the business costs of model errors:

1. **Random Forest (Baseline):** Achieved high precision (**94%**) but missed a portion of failures (Recall: **74%**).
2. **PyTorch Neural Network:** Was deliberately penalized for misses using the `pos_weight` parameter. This resulted in a drastic increase in Recall (**90% - 93%**) at the cost of a drop in Precision (**32%**).

**Conclusion:** In a factory setting (Predictive Maintenance), missing a failure (False Negative) means a broken machine, halted production lines, and massive financial losses. A false alarm (False Positive) only requires a cheap, routine inspection by a technician. Therefore, the PyTorch model, despite its lower overall precision, represents a significantly safer and more cost-effective solution for commercial deployment.

---

### Installation and Usage

1.  **Requirements:** Python 3.8+ and the libraries listed in `requirements.txt`.
    ```bash
    pip install -r requirements.txt
    ```

2.  **Execution:**
    Launch the Jupyter environment and open the main project notebook:
    ```bash
    jupyter notebook machine_failure_prediction.ipynb
    ```

### Project Structure

```text
├── machine_failure_prediction.ipynb  # Main notebook with EDA, RF and PyTorch models
├── predictive_maintenance_model.pth  # Saved weights of the trained Neural Network
└── requirements.txt                  # Dependencies (Pandas, Scikit-Learn, PyTorch, etc.)
```
