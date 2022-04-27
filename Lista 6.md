# To trochę podjeżdża też pod listę 7
# Pola.h
```cpp
#include <string>
#include "bank.h"
#include "pionek.h"

using namespace std;

class info {

private:
	int cena;
	int idWlasciciela;
	string nazwa;
	int czynsz;
	friend class Bank;
};

class Miasto : info {

private:
	int domki;
	int cenaD;
	int iloscD;

public:
	void pobierzWlasciciela(); //po zakupie przypisuje wlasciciela do danego pola
	void ustawWlasciciela(pionek p);
	void ustawDomek();
	void pobierzCzynsz(pionek p);
	void pobierzCeneDomku();
};

class Wodociagi : info {

private:
	int iloscPol;

public:
	void pobierzMnoznik(); //mnoznik z jakim pobiera pieniadze
	void pobierzPieniadze(); //pobiera pieniadze uzywajac mnoznika
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
