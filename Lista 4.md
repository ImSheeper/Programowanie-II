# Zadanie 1
```cpp
#include <iostream>
#include <vector>

using namespace std;

int min(vector<int> vec) {

    int min;

    for(int i = 0; i < vec.size(); i++) {
        if(i == 0) min = vec[i];
        if(min > vec[i]) min = vec[i];
    }

    return min;
}

int max(vector<int> vec) {

    int max;

    for(int i = 0; i < vec.size(); i++) {
        if(i == 0) max = vec[i];
        if(max < vec[i]) max = vec[i];
    }

    return max;
}

int srednia(vector<int> vec) {

    int srednia = 0;

    for(int i = 0; i < vec.size(); i++) {
        srednia += vec[i];
    }

    return srednia / vec.size();
}

int pozycja(vector<int> vec, int poz) {

    int wynik;

    for(int i = 0; i < vec.size(); i++) {
        if(i == poz - 1) wynik = vec[i];
    }

    return wynik;
}

int main() {

    int n;

    cout << "Podaj ile chcesz wprowadzic liczb" << endl;
    cin >> n;

    vector<int> vec(n);

    cout << "Podaj liczby" << endl;
    for(int i = 0; i < n; i++) {
        cin >> vec[i];
    }

    int poz;

    cout << "Najmniejsza liczba jest: " << min(vec) << endl;
    cout << "Najwieksza liczba jest: " << max(vec) << endl;

    cout << "Srednia liczb wynosi: " << srednia(vec) << endl;

    cout << endl << "Podaj pozycje jaka zwrocic" << endl;
    cin >> poz;

    cout << "Element na danej pozycji wynosi: " << pozycja(vec, poz) << endl;

    return 0;
}
```

# Zadanie 2 (MNOŻENIE NIE DZIAŁA)
```cpp
#include <iostream>
#include <vector>

using namespace std;

void dodawanie(vector<vector<int>> vec, vector<vector<int>> vec2) {

    int n, temp;

    cout << "Podaj wielkosc macierzy" << endl;
    cin >> n;

    vec.resize(n);
    vec2.resize(n);

    //Wprowadzanie liczb
    cout << "Wprowadz liczby " << n << "x" << n << " pierwszej macierzy" << endl;
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            cin >> temp;
            vec[i].push_back(temp);
        }
    }

    cout << "Wprowadz liczby " << n << "x" << n << " drugiej macierzy" << endl;
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            cin >> temp;
            vec2[i].push_back(temp);
        }
    }

    //Wyswietlanie dodawania
    cout << "Macierz 1:" << endl;
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            printf("%5d", vec[i][j]);
        }
        cout << endl;
    }

    cout << endl;
    cout << "Macierz 2:" << endl;
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            printf("%5d", vec2[i][j]);
        }
        cout << endl;
    }

    cout << endl;
    //Dodawanie
    cout << "Wynik:" << endl;
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            printf("%5d", vec[i][j] + vec2[i][j]);
        }
        cout << endl;
    }
}

void odejmowanie(vector<vector<int>> vec, vector<vector<int>> vec2) {

    int n, temp;

    cout << "Podaj wielkosc macierzy" << endl;
    cin >> n;

    vec.resize(n);
    vec2.resize(n);

    //Wprowadzanie liczb
    cout << "Wprowadz liczby " << n << "x" << n << " pierwszej macierzy" << endl;
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            cin >> temp;
            vec[i].push_back(temp);
        }
    }

    cout << "Wprowadz liczby " << n << "x" << n << " drugiej macierzy" << endl;
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            cin >> temp;
            vec2[i].push_back(temp);
        }
    }

    //Wyswietlanie odejmowania
    cout << "Macierz 1:" << endl;
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            printf("%5d", vec[i][j]);
        }
        cout << endl;
    }

    cout << endl;
    cout << "Macierz 2:" << endl;
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            printf("%5d", vec2[i][j]);
        }
        cout << endl;
    }

    cout << endl;
    //odejmowanie
    cout << "Wynik:" << endl;
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            printf("%5d", vec[i][j] - vec2[i][j]);
        }
        cout << endl;
    }
}

void mnozenie(vector<vector<int>> vec, vector<vector<int>> vec2) {

    int n, temp;

    cout << "Podaj wielkosc macierzy" << endl;
    cin >> n;

    vec.resize(n);
    vec2.resize(n);

    //Wprowadzanie liczb
    cout << "Wprowadz liczby " << n << "x" << n << " pierwszej macierzy" << endl;
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            cin >> temp;
            vec[i].push_back(temp);
        }
    }

    cout << "Wprowadz liczby " << n << "x" << n << " drugiej macierzy" << endl;
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            cin >> temp;
            vec2[i].push_back(temp);
        }
    }

    //Wyswietlanie mnozenia
    cout << "Macierz 1:" << endl;
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            printf("%5d", vec[i][j]);
        }
        cout << endl;
    }

    cout << endl;
    cout << "Macierz 2:" << endl;
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            printf("%5d", vec2[i][j]);
        }
        cout << endl;
    }

    vector<vector<int>> suma(n);

    cout << endl;
    //mnozenie
    cout << "Wynik:" << endl;
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            for(int k = 0; k < n; k++) {
                suma[i][j] += vec[i][k] * vec2[k][j];
            }
            printf("%5d", suma[i][j]);
        }
        cout << endl;
    }
}

int main() {

    int n;

    do {
        vector<vector<int>> vec;
        vector<vector<int>> vec2;

        cout << "Menu" << endl;
        cout << "1.Dodawanie" << endl;
        cout << "2.Odejmowanie" << endl;
        cout << "3.Mnozenie" << endl;
        cout << "4.Zakoncz" << endl;
        cin >> n;

        if (n == 1) dodawanie(vec, vec2);
        if (n == 2) odejmowanie(vec, vec2);
        if (n == 3) mnozenie(vec, vec2);
    }while(n != 4);

    return 0;
}
```
