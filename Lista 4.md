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

    int minimum, maksimum, sr, poz, wynik;

    minimum = min(vec);
    maksimum = max(vec);

    cout << "Najmniejsza liczba jest: " << minimum << endl;
    cout << "Najwieksza liczba jest: " << maksimum << endl;

    sr = srednia(vec);

    cout << "Srednia liczb wynosi: " << sr << endl;

    cout << endl << "Podaj pozycje jaka zwrocic" << endl;
    cin >> poz;

    wynik = pozycja(vec, poz);

    cout << "Element na danej pozycji wynosi: " << wynik << endl;

    return 0;
}
```

# Zadanie 2
