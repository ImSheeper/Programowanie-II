# Zadanie 1
```cpp
#include <iostream>

using namespace std;

int main()
{
    int w;
    float obj, pp;

    cout << "1. Kula" << endl << "2. Prostopadloscian" << endl << "3. Stozek" << endl;
    cin >> w;

    if(w == 1) {

        float r;

        cout << "Podaj promien r: " << endl;
        cin >> r;

        obj = (4/3.0)*3.14*(r*r*r);
        pp = 4*3.14*(r*r);

        cout << "Objetosc kuli wynosi: " << obj << endl;
        cout << "Pole powierzchni kuli wynosi: " << pp << endl;
    }

    if(w == 2) {

        float a, b, c;

        cout << "Podaj a: " << endl;
        cin >> a;

        cout << "Podaj b: " << endl;
        cin >> b;

        cout << "Podaj c: " << endl;
        cin >> c;

        obj = a*b*c;
        pp = 2*(a*b+a*c+b*c);

        cout << "Objetosc prostopadloscianu wynosi: " << obj << endl;
        cout << "Pole powierzchni prostopadloscianu wynosi: " << pp << endl;
    }

    if(w == 3) {

        float l, h, r;

        cout << "Podaj r: " << endl;
        cin >> r;

        cout << "Podaj h: " << endl;
        cin >> h;

        cout << "Podaj l: " << endl;
        cin >> h;

        obj = (3.14*(r*r)*h)/3.0;
        pp = 3.14*r*(r+l);

        cout << "Objetosc stozka wynosi: " << obj << endl;
        cout << "Pole powierzchni stozka wynosi: " << pp << endl;
    }

    return 0;
}
```

# Zadanie 2

```cpp
#include <iostream>

using namespace std;

int main() {

    int n;
    float srednia = 0;

    cout << "Ile ocen chcesz wprowadzic?" << endl;
    cin >> n;

    int tab[n];

    cout << "Podaj " << n << " ocen: " << endl;

    for(int i = 0; i < n; i++) {
        m:cin >> tab[i];

        if(tab[i] < 2 || tab[i] > 5) {
            cout << "Prosze wprowadzic ocene jeszcze raz." << endl;
            goto m;
        }
    }

    for(int i = 0;  i < n; i++) {
        srednia += tab[i];
        if(i == n - 1) srednia /= n;
    }

    cout << "Srednia wynosi: " << srednia << endl;

    if(srednia > 4.1) cout << "Przysluguje ci stypendium naukowe." << endl;
    else cout << "Niestety nie przysluguje ci stypendium naukowe." << endl;

    return 0;
}
```

# Zadanie 3
```cpp
#include <iostream>

using namespace std;

int main()
{
    int n;

    cout << "Podaj n: " << endl;
    cin >> n;

    for(int i = 1; i <= n; i++) {

        for(int j = i; j <= n; j++) {
            cout << " ";
        }

        for(int g = 1; g <= (2 * i - 1); g++) {
            if(i == n && g % 2 == 1 || g == 1 || g == 2 * i - 1) cout << "*";
            else cout << " ";
        }

        cout << endl;
    }

    return 0;
}
```

# Zadanie 4 (Nie jest dobrze)
```c++
#include <iostream>
#include <string>

using namespace std;

int main()
{
    string zdanie;
    int all = 0, bezSpacji = 0, wyk = 0;
    char znak;

    cout << "Podaj zdanie: " << endl;
    getline(cin, zdanie);

    cout << "Podaj znak do wykluczenia: " << endl;
    cin >> znak;

    cout << "Zdanie: " << zdanie << endl;
    for(int i = 0; i < zdanie.length(); i++) {

        if(zdanie[i] >= 32 && zdanie[i] <= 126) all++;

        if(zdanie[i] >= 33 && zdanie[i] <= 126) bezSpacji++;

        if(zdanie[i] >= 32 && zdanie[i] <= 126 && znak != zdanie[i]) wyk++;
    }

    cout << endl << "Liczba liter: " << all << endl;
    cout << "Liczba liter z pominieciem spacji: " << bezSpacji << endl;
    cout << "Liczba liter z wykluczeniem znaku: " << wyk << endl;

    string *arr;
    arr = new string[zdanie.length()];

    cout << endl << "Podaj znak do podzielenia zdania: " << endl;
    cin >> znak;

        for(int i = 0; i < zdanie.length(); i++) {

        cout << zdanie[i];

        if(zdanie[i] == znak) {
            cout << endl;
        }
    }

    return 0;
}```
