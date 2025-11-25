                                                                        Dokumentacja techniczna – Symulacja protokołu BB84 w Qiskit
                        Spis treści

                          1. Opis projektu

                          2. Wymagania

                          3. Struktura projektu

                          4. Opis działania systemu

                          5.  Opis funkcji
                              
                          6. Przepływ programu
                              
                          7. Uruchamianie
                              
                          8. Możliwe rozszerzenia
                              
                            
                              
**1. Opis projektu**

Projekt przedstawia symulację protokołu BB84, jednego z fundamentalnych protokołów kwantowej dystrybucji klucza (QKD).
W BB84 nadawca (Anna) przygotowuje qubity w losowych bazach, odbiorca (Bartek) je mierzy, a podsłuchiwacz (Eryk) próbuje wykonać pomiary, co wprowadza błędy wykrywalne w końcowym kluczu.

W projekcie zastosowano symulator kwantowy Qiskit Aer.


**2. Wymagania**

Do uruchomienia projektu potrzebne są: Python 3.8+, Qiskit, NumPy


**3. Struktura projektu**
📁 projekt-bb84
│── main.py                 # główny plik programu
│── README.md               # dokumentacja


Opis działania systemu
1. Anna (nadawca), generuje losowy zestaw baz 0 / 1

0 → baza Z (standardowa)

1 → baza X (Hadamard)

przygotowuje qubity zgodnie z tymi bazami, zapisuje swoje bazy w zmiennej środowiskowej

2. Eryk (podsłuchiwacz)

generuje własne losowe bazy, mierzy qubity i zapisuje wynik

jego pomiary wprowadzają błędy w systemie, próbuje „przywrócić” stany kwantowe, stosując ponownie swoje bramki (co w realnym świecie byłoby niewykonalne)

3. Bartek (odbiorca)

generuje własne losowe bazy, mierzy qubity, zapisuje zarówno: swoje bazy, otrzymany klucz

4. Porównanie baz (klasyczny kanał)

Anna i Bartek porównują bazy, by określić, które bity można uznać za wspólny klucz.
W tym projekcie wypisywane są tylko bazy, ale można łatwo rozszerzyć kod o analizę błędów.



Przykładowy wynik:

Pełny klucz, który podsłuchał Eryk to: 01011010101
Bazy, których użyła Anna:    0110100110010
Bazy, których użył Bartek:   1001001100101



Projekt można rozbudować o:

✅ wykrywanie podsłuchu (QBER – Quantum Bit Error Rate)
✅ generowanie wspólnego klucza po odfiltrowaniu niezgodnych baz
✅ wizualizację obwodów Qiskit
✅ komunikację klasyczną (symulowaną) między Anną i Bartkiem
✅ obsługę większej liczby uczestników
