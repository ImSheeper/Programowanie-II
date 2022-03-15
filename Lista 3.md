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
```cpp
#include <iostream>
#include <time.h>

using namespace std;

int main() {
    char tn;
    do {

        int size, suma = 0, suma2 = 0;
        srand(time(NULL));

        m:cout << "Podaj rozmiar macierzy od 2-10: " << endl;
        cin >> size;

        if (size > 10 || size < 2) {
            cout << "Podaj wartosc od 2-10!" << endl;
            goto m;
        }

        int tab[size][size];

        for (int i = 0; i < size; i++) {
            for (int j = 0; j < size; j++) {
                tab[i][j] = rand() % 10;
                cout << tab[i][j] << " ";
                //cout << i << j << " ";
                if (i == j + 1) suma += tab[i][j];
                if (i + 1 == j) suma2 += tab[i][j];
            }
            cout << endl;
        }

        cout << "Suma ponizej przekatnej: " << suma << endl;
        cout << "Suma powyzej przekatnej: " << suma2 << endl << endl;

        int kol, suma3 = 0;

        cout << "Podaj kolumne: " << endl;
        cin >> kol;

        for (int i = 0; i < size; i++) {
            for (int j = 0; j < size; j++) {
                cout << tab[i][j] << " ";
                //cout << i << j << " ";
                if (j == kol - 1) suma3 += tab[i][j];
            }
            cout << endl;
        }

        cout << "Suma kolumny numer " << kol << " wynosi: " << suma3 << endl << endl;

        cout << "Kontynuowac? t/n" << endl;
        cin >> tn;
    }while(tn != 'n');

    return 0;
}```
