# Zadanie 1

# Zadanie 2 (BRAK FUNKCJI)
```cpp
#include <iostream>

using namespace std;

int minMax {

};

int main() {

    int tab[15];


    cout << "Podaj 15 liczb (oddzielane enterem)" << endl;
    for(int i = 0; i < 15; i++) {
        cin >> tab[i];
    }

    int min = 0, max = 0, srednia = 0, maxI, minI;

    for(int i = 0; i < 15; i++) {
        if(i == 0) {
            min = tab[i];
            max = tab[i];
        }

        if(min > tab[i]) {
            min = tab[i];
            minI = i;
        }

        if(max < tab[i]) {
            max = tab[i];
            maxI = i;
        }

        srednia += tab[i];
    }

    srednia /= 15;

    cout << "Najwieksza liczba wynosi: " << max << " jej pozycja to: " << maxI << endl;
    cout << "Najmniejsza liczba wynosi: " << min << " jej pozycja to: " << minI << endl;
    cout << "Srednia tych liczb wynosi: " << srednia << endl;

    int wartosc;

    cout << "Podaj wartosc do znalezienia: " << endl;
    cin >> wartosc;

    for(int i = 0; i < 15; i++) {
        if(wartosc == tab[i]) wartosc = i;
    }

    cout << "Pozycja wartosci wynosi: " << wartosc << endl;

    return 0;
}
```
# Zadanie 3
