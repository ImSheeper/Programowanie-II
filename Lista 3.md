# Zadanie 1

# Zadanie 2
```cpp
#include <iostream>

using namespace std;

int minimum(int size, int *tab) {

    int min = 0, minI = 0;

    for(int i = 0; i < size; i++) {
        if(i == 0) min = tab[i];

        if(min > tab[i]) {
            min = tab[i];
            minI = i;
        }
    }

    cout << "Najmniejsza liczba wynosi: " << min << endl;
    return minI;
}

int maksimum(int size, int *tab) {

    int max = 0, maxI = 0;

    for(int i = 0; i < size; i++) {
        if(i == 0) max = tab[i];

        if(max< tab[i]) {
            max = tab[i];
            maxI = i;
        }
    }

    cout << "Najmniejsza liczba wynosi: " << max << endl;
    return maxI;
}

int srednia(int size, int *tab) {

    int sr = 0;

    for(int i = 0; i < size; i++) {
        sr += tab[i];
    }

    return sr / size;
}

int znajdz(int wartosc, int *tab, int size) {

    for(int i = 0; i < 15; i++) {
        if(wartosc == tab[i]) wartosc = i;
    }

    return wartosc;
}

int main() {

    int tab[15], min, max, sr;

    cout << "Podaj 15 liczb (oddzielane enterem)" << endl;
    for(int i = 0; i < 15; i++) {
        cin >> tab[i];
    }

    min = minimum(15, tab);
    max = maksimum(15, tab);
    sr = srednia(15, tab);

    cout << "Pozycja najmniejszej liczby to: " << min << endl;
    cout << "Pozycja najwiekszej liczby to: " << max << endl;
    cout << "Srednia wynosi: " << sr << endl;

    int wartosc, n;

    cout << "Podaj wartosc do znalezienia: " << endl;
    cin >> wartosc;

    n = znajdz(wartosc, tab, 15);

    cout << "Pozycja wartosci wynosi: " << n << endl;

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
