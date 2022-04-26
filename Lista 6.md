# Pola.h
```cpp
#include <string>
#include "Bank.h"
#include "Pionek.h"

using namespace std;

class Miasto {

private:
	int cena;
	int domki;
	int czynsz;

public:
	void pobierzWlasciciela(); //po zakupie przypisuje wlasciciela do danego pola
	void pobierzCzynsz();
	void pobierzCeneDomku();
};

class Wodociagi {

private:
	int cena;
	int czynsz;

public:
	void pobierzWlasciciela();
	void ulepszenia();
	void pobierzCzynsz();
};

class Szansa {

public:
	void losowanie(); //po najechaniu na to pole zaczyna sie losowanie szansy
	void wykonaj(); //w zaleznosci od typu karty wykonuje rozne operacje
};

class Wiezienie {

public:
	void idzDoWiezienia();
};
```

# Bank.h
```cpp
#include <string>
#include "Pionek.h"
#include "Pola.h"

using namespace std;

class Bank {

private:
	int saldo; //bankier ma co prawda nieskończone saldo, ale przydałoby się taką zmienną mieć
	int wymiana; //przechowuje wartość pobranych pieniędzy, żeby je przekazać innemu graczowi

public:
	void wyplacStart(); //Przekazuje graczowi pieniadze po przekroczeniu pola START
	void wykup(); //pobiera pieniadze po zakupie nieruchomosci nienalezacej do zadnego gracza
	void ulepszanie(); //doklada domki do zakupionej nieruchomosci oraz pobiera pieniadze
	void zabierzPieniadze();
	void dajPieniadze();
	void odkupianie(); //jezeli gracz bedzie chcial wykupic od kogos posiadlosc to nastepuje wymiana domkow oraz pieniedzy
};
```

# Pionek.h
```cpp
#include <string>
#include "Pola.h"
#include "Bank.h"

using namespace std;

class Pionek {

private:
	int id;
	string nazwa;
	int hajs;

public:
	void pole(); //sprawdza na ktorym polu stoi gracz
	void rzutKostka(); //losuje liczbe z zakresu 1-6
	void poruszanieSie(); //przyjmuje wartosc kostki i rusza sie na podstawie wylosowanych oczek
	void kupowanie(); //jezeli gracz stoi na polu mozliwym do kupna to sprawdza czy posiada wystarczajaca ilosc pieniedzy
	void placenie(); //jezeli gracz wyladuje na nieruchomosci nalezacej do innego gracza to placi mu czynsz
	void szansa(); //gdy gracz wyladuje na polu szansa to zaczyna sie losowanie kart
};
```

# Monopoly.cpp
```cpp
#include <iostream>

using namespace std;

int main() {
    cout << "Gra Monopoly" << endl;
    return 0;
}
```
