# Source.cpp
```cpp
#include <iostream>

using namespace std;

class samochodMechanik {
    
public:
    string marka;
    string silnik;
    int pojemnoscSilnika;
    string karoseria;
    string niezawodnosc;

    samochodMechanik() {
        cout << "Konstruktor" << endl;
    }
};

class samochodRodzina : public samochodMechanik {
    
public:
    float spalanie;
    int liczbaMiejsc;
    float pojemnoscBagaznika;
    int pojemnoscBaku;
    string kolor;

    samochodRodzina() {
        cout << "Konstruktor" << endl;
    }
};

class samochodUrzednik : public samochodRodzina {

public:
    string rejestracja;
    string dokumentacja;

    samochodUrzednik() {
        cout << "Konstruktor" << endl;
    }
};

    // zaproponuj hierarchię klas, w której klasą podstawową będzie samochód z punktu widzenia mechanika,
    // następnie samochód z punktu widzenia rodziny, który będzie opisany przez klasę dziedziczącą od klasy podstawowej
    // Ostatecznie zdefiniuj klasę opisującą samochód z punktu widzenia urzędnika, jako dziedziczącą po tej ostatniej.
    // Skorzystaj również z dziedziczenia implementując metody wypełniające i wyświetlające dane.
```

# main.cpp
```cpp
#include <iostream>
#include "Source.cpp"

using namespace std;

int main() {

    cout << "Hello World!" << endl;

    return 0;
}
```
