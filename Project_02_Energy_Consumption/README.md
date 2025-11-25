                                                    Dokumentacja Techniczna — Model Prognozowania Zużycia Gazu
1. Cel analizy

Celem projektu było zbudowanie modeli predykcyjnych umożliwiających prognozowanie dziennej konsumpcji gazu w gospodarstwach domowych na podstawie danych meteorologicznych, wskaźników gospodarczych oraz dodatkowych zmiennych sezonowych. Kluczowym zadaniem było również przygotowanie danych do modelowania oraz porównanie dwóch metod: regresji liniowej (OLS) i modelu Random Forest.

2. Zestaw danych

W analizie wykorzystano dane dzienne i miesięczne zawierające:

Kolumna	Opis	Częstotliwość
Consumption	Dzienne zużycie gazu	dzienna
Temp_avg	Średnia temperatura dobowa, liczona jako (T_max + T_min)/2	dzienna
windspeed_10m_max	Maksymalna dzienna prędkość wiatru	dzienna
Employments_MoM	Miesięczna zmiana zatrudnienia	miesięczna
Winter_Clothes	Wolumen sprzedaży odzieży zimowej	miesięczna
dateCET	Data obserwacji	dzienna

Dane wejściowe zawierały wartości brakujące, różne częstotliwości pomiarów oraz wymagania dotyczące standaryzacji zmiennych.

3. Weryfikacja i przygotowanie danych
3.1. Analiza braków danych

Wykryto następujące problemy:

    - Kolumny Consumption, Temp_avg, windspeed_10m_max posiadały po 5 brakujących wartości.
    - Kolumny Employments_MoM i Winter_Clothes zawierały tylko 61 wartości, co potwierdza ich miesięczną częstotliwość.
    

3.2. Uzupełnianie braków danych
Dane miesięczne → dzienne

Aby umożliwić wspólne modelowanie, dane miesięczne zostały uzupełnione metodą: fillna(method='ffill')

Oznacza to, że pojedyncza wartość miesięczna została „rozciągnięta” na wszystkie dni danego miesiąca.




4. Przetwarzanie kolumn czasowych

Kolumna dateCET została przekonwertowana do formatu datetime oraz rozszerzona o:

Rok, Miesiąc, Dzień, Dzień tygodnia celem wzbogacenia danych o informacje sezonowe i cykliczne.



5. Standaryzacja zmiennych

Zmienne: Temp_avg, windspeed_10m_max, Employments_MoM, Winter_Clothes zostały poddane standaryzacji metodą StandardScaler w celu zachowania porównywalnych zakresów wartości i stabilności modeli.



6. Podział danych na zbiory treningowy i testowy

Dane zostały podzielone w oparciu o datę: 
          - Trening: wszystkie dane sprzed ostatniego roku
          - Test: ostatnie 12 miesięcy danych

Pozwoliło to ocenić zdolność modeli do generalizacji na nowszych okresach.


7. Modelowanie
   
7.1. Model 1 — Regresja liniowa (OLS)

Zalety: interpretowalność, niska złożoność

Wady: zakłada liniowość relacji, może nie uchwycić złożonych zależności


7.2. Model 2 — Random Forest Regressor

Zalety: potrafi modelować nieliniowości, odporny na szum i korelacje, lepsza jakość predykcji

Wady: brak prostych współczynników regresyjnych, wyższa złożoność obliczeniowa



8. Metryki oceny
   
Dla obu modeli wyliczono:
R² — wyjaśnienie wariancji
MAE — średni błąd bezwzględny
MAPE — błąd procentowy
RMSE — pierwiastek błędu średniokwadratowego

9. Wyniki modeli
R²	0.91
MAE	183.76
MAPE	36.07%
RMSE	218.27

Interpretacja:
model dobrze dopasowuje się do danych, ale ma wyższe błędy prognoz.

Random Forest
R²	0.95
MAE	117.78
MAPE	14.54%
RMSE	159.05

Interpretacja:
znacznie lepsza jakość predykcji niż w OLS, dobrze radzi sobie z nieliniowościami i interakcjami między zmiennymi.


10. Wizualizacja wyników

Na wykresie zestawiono: wartości rzeczywiste, predykcje regresji liniowej, predykcje Random Forest. Wizualizacja pokazała wyraźnie mniejsze odchylenia modelu Random Forest.



11. Wnioski

                  - Model Random Forest osiągnął najlepsze wyniki i skutecznie przewiduje zmiany w konsumpcji gazu.
                  - Regresja liniowa okazała się przydatna do interpretacji, ale niedostateczna w oddawaniu złożonych zależności.
                  - Włączenie zmiennych takich jak temperatura, prędkość wiatru oraz wskaźniki sezonowe istotnie poprawia jakość prognoz.
                  - Dane miesięczne wymagają dopasowania do dziennej częstotliwości — forward fill okazał się skuteczny, ale można rozważyć bardziej zaawansowane metody interpolacji.

W przyszłości warto rozważyć:
- optymalizację hiperparametrów Random Forest (GridSearchCV),
- zastosowanie Gradient Boosting, XGBoost, LightGBM,
- dodanie cech opóźnionych (lag features),
- wykorzystanie modeli czasowych (ARIMA, Prophet, LSTM).
