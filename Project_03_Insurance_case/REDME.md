                                                                📊 Analiza Danych Szkodowych – README
📌 Opis projektu

Celem projektu jest przeprowadzenie kompleksowej analizy danych dotyczących szkód ubezpieczeniowych z pierwszego kwartału 2023 roku. Projekt obejmuje:

eksplorację i czyszczenie danych,
tworzenie zmiennych pochodnych,
analizę braków danych,
analizę statystyczną i wizualizacje,
przygotowanie danych do modelowania,
segmentację klientów metodą K-Means.
Dane wejściowe pochodzą z pliku claims_q12023.csv.


📁 Zawartość projektu
EDA – wstępna analiza danych Feature engineering – tworzenie zmiennych pochodnych Analiza braków danych i ich imputacja Wizualizacje danych (Seaborn, Matplotlib) Macierz korelacji Segmentacja klientów (K-Means) Normalizacja danych (StandardScaler)


🛠️ Wykorzystywane technologie i biblioteki
Python, pandas, numpy, matplotlib, seaborn, scikit-learn, StandardScaler, KMeans


📝 Wnioski z analizy

Brakujące wartości w kluczowych zmiennych wykazują pattern zależny od charakteru szkody.
Wiek pojazdu oraz czas od rozpoczęcia polisy mają logiczne rozkłady.
Dane numeryczne są silnie powiązane (total_claim_amount vs vehicle_claim/injury_claim).
Klasteryzacja K-Means pozwala na identyfikację trzech segmentów szkód/klientów.


📌 Możliwe dalsze kroki

Model predykcyjny (np. XGBoost / Random Forest) 
Redukcja wymiarowości PCA przed klasteryzacją
Dashboard (Plotly / Power BI)
Analiza anomalii szkód (fraud detection)
