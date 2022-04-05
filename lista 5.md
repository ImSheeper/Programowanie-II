# Wybierzcie sobie jakąś wersję. Jak dobrze pamiętam, to wszystkie działają
# Pierwsza wersja
```cpp
#include <iostream>

using namespace std;

int tab[3][3], posx[3][3], posy[3][3];

void budowanie() {

    int iteracja = 0;

    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            posx[i][j] = iteracja;
            tab[i][j] = iteracja;
            iteracja++;
        }
    }
}

void rysowanie() {

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(tab[i][j] == 'X') printf("    x");
            else if(tab[i][j] == 'O') printf("    o");
            else printf("%5d", tab[i][j]);
        }
        cout << endl;
    }
}

void wpisywanie(int pole) {

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(pole == tab[i][j]) {
                posx[i][j] = 10;
                tab[i][j] = 'X';
            }
        }
    }
    rysowanie();
}

void wpisywanie2(int pole) {

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(pole == tab[i][j]) {
                posy[i][j] = 20;
                tab[i][j] = 'O';
            }
        }
    }
    rysowanie();
}

int sprawdzanie() {

    int l1 = 0, sr1 = 0, pr1 = 0, lprz1 = 0, pprz1 = 0, y0 = 0, y1 = 0, y2 = 0;

    cout << endl;
    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            //printf("%5d%d", i,j);
            //printf("%5d", posx[i][j]);
            if(j == 0 && posx[i][j] == 10) l1++;
            if(j == 1 && posx[i][j] == 10) sr1++;
            if(j == 2 && posx[i][j] == 10) pr1++;
            if(i == j && posx[i][j] == 10) lprz1++;
            if(j + i == 2 && posx[i][j] == 10) pprz1++;
            if(i == 0 && posx[i][j] == 10) y0++;
            if(i == 1 && posx[i][j] == 10) y1++;
            if(i == 2 && posx[i][j] == 10) y2++;
        }
    }

    int sprawdzanie = 0;

    if(l1 >= 3 || sr1 >= 3 || pr1 >= 3 || lprz1 >= 3 || pprz1 >= 3 || y0 >= 3 || y1 >= 3 || y2 >= 3) sprawdzanie = 1;

    return sprawdzanie;
}

int sprawdzanie2() {

    int l2 = 0, sr2 = 0, pr2 = 0, lprz2 = 0, pprz2 = 0, y02 = 0, y12 = 0, y22 = 0;

    cout << endl;
    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            //printf("%5d%d", i,j);
            //printf("%5d", posy[i][j]);
            //Sprawdzanie gracza2
            if(j == 0 && posy[i][j] == 20) l2++;
            if(j == 1 && posy[i][j] == 20) sr2++;
            if(j == 2 && posy[i][j] == 20) pr2++;
            if(i == j && posy[i][j] == 20) lprz2++;
            if(j + i == 2 && posy[i][j] == 20) pprz2++;
            if(i == 0 && posy[i][j] == 20) y02++;
            if(i == 1 && posy[i][j] == 20) y12++;
            if(i == 2 && posy[i][j] == 20) y22++;
        }
    }

    int sprawdzanie2 = 0;

    if(l2 >= 3 || sr2 >= 3 || pr2 >= 3 || lprz2 >= 3 || pprz2 >= 3 || y02 >= 3 || y12 >= 3 || y22 >= 3) sprawdzanie2 = 1;

    return sprawdzanie2;
}

int main() {

    int pole = 10, ruchy = 0, sp, sp2;

    budowanie();

    cout << "Kolko i Krzyzyk" << endl;
    cout << "Rozgrywka z druga osoba" << endl;

    rysowanie();

    do {
        cout << "Gracz 1" << endl;
        cout << "Wybierz pole" << endl;
        cin >> pole;
        wpisywanie(pole);
        sp = sprawdzanie();

        if(sp == 1) break;

        cout << "Gracz 2" << endl;
        cout << "Wybierz pole" << endl;
        cin >> pole;
        wpisywanie2(pole);
        sp2 = sprawdzanie2();

        if(sp2 == 1) break;

        ruchy++;
    }while(ruchy < 9);

    if(sp == 1) cout << "Gracz 1 (x) wygral" << endl;
    else if(sp2 == 1) cout << "Gracz 2 (o) wygral" << endl;

    return 0;
}
```
# Bardziej zoptymalizowana wersja
# funkcje.cpp
```cpp
#include <iostream>
#include <windows.h>
#include <stdlib.h>
#include "header.h"

using namespace std;

int tab[3][3], posx[3][3], posy[3][3];

void budowanie() {

    int iteracja = 0;

    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            tab[i][j] = iteracja;
            iteracja++;
        }
    }
}

void rysowanie() {

    int l = 0;

    cout << "    0   1   2 -> X" << endl;

    for(int i = 0; i < 3; i++) {
        cout << l << " ";
        l += 3;
        for(int j = 0; j < 3; j++) {
            cout << "|";
            if(posx[i][j] == 10) printf(" x ");
            else if(posy[i][j] == 20) printf(" o ");
            else if(j < 3) cout << "___";
            if(j == 2) cout << "|";
        }
        cout << endl;
    }
    cout << "Y |" << endl;
}

void wpisywanie(int pole) {

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(pole == tab[i][j]) posx[i][j] = 10;
        }
    }
    rysowanie();
}

void wpisywanie2(int pole) {

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(pole == tab[i][j]) posy[i][j] = 20;
        }
    }
    rysowanie();
}

int sprawdzanie() {

    int l1 = 0, sr1 = 0, pr1 = 0, lprz1 = 0, pprz1 = 0, y0 = 0, y1 = 0, y2 = 0;

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(j == 0 && posx[i][j] == 10) l1++;
            if(j == 1 && posx[i][j] == 10) sr1++;
            if(j == 2 && posx[i][j] == 10) pr1++;
            if(i == j && posx[i][j] == 10) lprz1++;
            if(j + i == 2 && posx[i][j] == 10) pprz1++;
            if(i == 0 && posx[i][j] == 10) y0++;
            if(i == 1 && posx[i][j] == 10) y1++;
            if(i == 2 && posx[i][j] == 10) y2++;
        }
    }

    int sprawdzanie = 0;

    if(l1 >= 3 || sr1 >= 3 || pr1 >= 3 || lprz1 >= 3 || pprz1 >= 3 || y0 >= 3 || y1 >= 3 || y2 >= 3) sprawdzanie = 1;

    return sprawdzanie;
}

int sprawdzanie2() {

    int l2 = 0, sr2 = 0, pr2 = 0, lprz2 = 0, pprz2 = 0, y02 = 0, y12 = 0, y22 = 0;

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(j == 0 && posy[i][j] == 20) l2++;
            if(j == 1 && posy[i][j] == 20) sr2++;
            if(j == 2 && posy[i][j] == 20) pr2++;
            if(i == j && posy[i][j] == 20) lprz2++;
            if(j + i == 2 && posy[i][j] == 20) pprz2++;
            if(i == 0 && posy[i][j] == 20) y02++;
            if(i == 1 && posy[i][j] == 20) y12++;
            if(i == 2 && posy[i][j] == 20) y22++;
        }
    }

    int sprawdzanie2 = 0;

    if(l2 >= 3 || sr2 >= 3 || pr2 >= 3 || lprz2 >= 3 || pprz2 >= 3 || y02 >= 3 || y12 >= 3 || y22 >= 3) sprawdzanie2 = 1;

    return sprawdzanie2;
}
```
# header.h
```cpp
#ifndef HEADER_H_INCLUDED
#define HEADER_H_INCLUDED



#endif // HEADER_H_INCLUDED


void budowanie();

void rysowanie();

void wpisywanie(int pole);

void wpisywanie2(int pole);

int sprawdzanie();

int sprawdzanie2();
```
# main.cpp
```cpp
#include <iostream>
#include <windows.h>
#include <stdlib.h>
#include "header.h"
#include "funkcje.cpp"

using namespace std;

int main() {

    int pole = 10, ruchy, sp, sp2, wyb;

    m:cout << "Kolko i Krzyzyk" << endl;
    cout << "1. Rozgrywka z druga osoba" << endl;
    cout << "2. Rozgrywka z AI (NIEDOSTEPNE)" << endl;
    cin >> wyb;

    if(wyb == 1) {
        ruchy = 0;
        system("cls");
        budowanie(); //budowanie planszy/resetowanie
        rysowanie(); //rysowanie planszy

        do {
            cout << "Gracz 1 (x)" << endl;
            cout << "Wybierz pole (X + Y)" << endl;
            cin >> pole;
            system("cls");
            wpisywanie(pole);
            sp = sprawdzanie();
            ruchy++;

            if(sp == 1 || ruchy == 9) break;

            cout << "Gracz 2 (o)" << endl;
            cout << "Wybierz pole (X + Y)" << endl;
            cin >> pole;
            system("cls");
            wpisywanie2(pole);
            sp2 = sprawdzanie2();
            ruchy++;

            if(sp2 == 1 || ruchy == 9) break;
        }while(ruchy < 9);

        if(sp == 1) cout << endl << "Koniec gry!" << endl << "Gracz 1 (x) wygral" << endl << endl;
        else if(sp2 == 1) cout << endl << "Koniec gry!" << endl << "Gracz 2 (o) wygral" << endl << endl;
        else cout << endl << "Koniec gry!" << endl << "Remis!" << endl << endl;

        cout << "Zagrac jeszcze raz?" << endl;
        cout << "1.Tak" << endl;
        cout << "2.Nie" << endl;
        cin >> wyb;
        cout << endl;

        if(wyb == 1) {
            system("cls");
            cout << "Wczytywanie..." << endl;
            Sleep(1000);
            system("cls");
            goto m;
        }
        else return 0;
    }

    else if(wyb == 2) {
        system("cls");
        cout << "Ten tryb nie jest jeszcze gotowy!" << endl;
        Sleep(2000);
        system("cls");
        goto m;
    }

    else {
        system("cls");
        cout << "Bledna wartosc!" << endl;
        Sleep(2000);
        system("cls");
        goto m;
    }

    return 0;
}
```
# Najbardziej zoptymalizowana wersja!
# funkcje.cpp
```cpp
#include <iostream>
#include <windows.h>
#include <stdlib.h>
#include "header.h"

using namespace std;

int tab[3][3], posx[3][3], posy[3][3];

void budowanie() {

    int iteracja = 0;

    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            tab[i][j] = iteracja;
            posx[i][j] = iteracja;
            posy[i][j] = iteracja;
            iteracja++;
        }
    }
}

void rysowanie() {

    int l = 0;

    cout << "    0   1   2 -> X" << endl;

    for(int i = 0; i < 3; i++) {
        cout << l << " ";
        l += 3;
        for(int j = 0; j < 3; j++) {
            cout << "|";
            if(posx[i][j] == 10) printf(" x ");
            else if(posy[i][j] == 20) printf(" o ");
            else if(j < 3) cout << "___";
            if(j == 2) cout << "|";
        }
        cout << endl;
    }
    cout << "Y |" << endl;
}

void wpisywanie(int pole) {

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(pole == tab[i][j]) {
              tab[i][j] = 'X';
              posx[i][j] = 10;
            }
        }
    }
    rysowanie();
}

void wpisywanie2(int pole) {

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(pole == tab[i][j]) {
              tab[i][j] = 'O';
              posy[i][j] = 20;
            }
        }
    }
    rysowanie();
}

int sprawdzanie() {

        int sprawdzanie = 0;

    for(int i = 0; i < 3; i++) {
        if(tab[i][0] == tab[i][1] && tab[i][0] == tab[i][2] || tab[0][i] == tab[1][i] && tab[0][i] == tab[2][i]) {
            sprawdzanie = 1;
            return sprawdzanie;
        }
        if(tab[0][0] == tab[1][1] && tab[0][0] == tab[2][2] || tab[0][2] == tab[1][1] && tab[0][2] == tab[2][0]) {
            sprawdzanie = 1;
            return sprawdzanie;
        }
    }

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(tab[i][j] != 'X' && tab[i][j] != 'O') sprawdzanie = 0;
        }
    }

    return sprawdzanie;
}
```
# header.h
```cpp
#ifndef HEADER_H_INCLUDED
#define HEADER_H_INCLUDED



#endif // HEADER_H_INCLUDED


void budowanie();

void rysowanie();

void wpisywanie(int pole);

void wpisywanie2(int pole);

int sprawdzanie();

int sprawdzanie2();
```
# main.cpp
```cpp
#include <iostream>
#include <windows.h>
#include <stdlib.h>
#include "header.h"
#include "funkcje.cpp"

using namespace std;

int main() {

    int pole = 10, ruchy, sp, wyb;

    m:cout << "Kolko i Krzyzyk" << endl;
    cout << "1. Rozgrywka z druga osoba" << endl;
    cout << "2. Rozgrywka z AI (NIEDOSTEPNE)" << endl;
    cin >> wyb;

    if(wyb == 1) {
        ruchy = 0;
        system("cls");
        budowanie(); //budowanie planszy/resetowanie
        rysowanie(); //rysowanie planszy

        do {
            cout << "Gracz 1 (x)" << endl;
            cout << "Wybierz pole (X + Y)" << endl;
            cin >> pole;
            system("cls");
            wpisywanie(pole);
            sp = sprawdzanie();
            ruchy++;

            if(sp == 1 || ruchy == 9) break;

            cout << "Gracz 2 (o)" << endl;
            cout << "Wybierz pole (X + Y)" << endl;
            cin >> pole;
            system("cls");
            wpisywanie2(pole);
            sp = sprawdzanie();
            ruchy++;

            if(sp == 1 || ruchy == 9) break;
        }while(ruchy < 9);

        if(sp == 1 && ruchy % 2 == 1) cout << endl << "Koniec gry!" << endl << "Gracz 1 (x) wygral" << endl << endl;
        else if(sp == 1 && ruchy % 2 == 0) cout << endl << "Koniec gry!" << endl << "Gracz 2 (o) wygral" << endl << endl;
        else cout << endl << "Koniec gry!" << endl << "Remis!" << endl << endl;

        cout << "Zagrac jeszcze raz?" << endl;
        cout << "1.Tak" << endl;
        cout << "2.Nie" << endl;
        cin >> wyb;
        cout << endl;

        if(wyb == 1) {
            system("cls");
            cout << "Wczytywanie..." << endl;
            Sleep(1000);
            system("cls");
            goto m;
        }
        else return 0;
    }

    else if(wyb == 2) {
        system("cls");
        cout << "Ten tryb nie jest jeszcze gotowy!" << endl;
        Sleep(2000);
        system("cls");
        goto m;
    }

    else {
        system("cls");
        cout << "Bledna wartosc!" << endl;
        Sleep(2000);
        system("cls");
        goto m;
    }

    return 0;
}
```
# Wersja ostateczna (Bez wybierania wielkości planszy przez użytkownika)
# funkcje.cpp
```cpp
#include <iostream>
#include <windows.h>
#include <stdlib.h>
#include <time.h>
#include "header.h"

using namespace std;

int tab[3][3], posx[3][3], posy[3][3];

//budowanie resetuje plansze do wartosci domyslnych z kazdym restartem gry
void budowanie() {

    int iteracja = 0;

    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            tab[i][j] = iteracja;
            posx[i][j] = iteracja;
            posy[i][j] = iteracja;
            iteracja++;
        }
    }
}

void rysowanie() {

    int l = 0;

    cout << "    0   1   2 -> X" << endl;

    for(int i = 0; i < 3; i++) {
        cout << l << " ";
        l += 3;
        for(int j = 0; j < 3; j++) {
            cout << "|";
            if(posx[i][j] == 10) printf(" x ");
            else if(posy[i][j] == 20) printf(" o ");
            else if(j < 3) cout << "___";
            if(j == 2) cout << "|";
        }
        cout << endl;
    }
    cout << "Y |" << endl;
}

void wpisywanie() {

    int pole;

    cout << "Gracz 1 (x)" << endl;
    cout << "Wybierz pole (X + Y)" << endl;
    cin >> pole;
    system("cls");

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(pole == tab[i][j]) {
              tab[i][j] = 'X';
              posx[i][j] = 10;
            }
        }
    }

    rysowanie();
}

void wpisywanie2() {

    int pole;

    cout << "Gracz 2 (o)" << endl;
    cout << "Wybierz pole (X + Y)" << endl;
    cin >> pole;
    system("cls");

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(pole == tab[i][j]) {
              tab[i][j] = 'O';
              posy[i][j] = 20;
            }
        }
    }
    rysowanie();
}

int sprawdzanie() {

        int sprawdzanie = 0;

    for(int i = 0; i < 3; i++) {
        //sprawdzanie bokow
        if(tab[i][0] == tab[i][1] && tab[i][0] == tab[i][2] || tab[0][i] == tab[1][i] && tab[0][i] == tab[2][i]) {
            sprawdzanie = 1;
            return sprawdzanie;
        }

        //sprawdzanie przekatnych
        if(tab[0][0] == tab[1][1] && tab[0][0] == tab[2][2] || tab[0][2] == tab[1][1] && tab[0][2] == tab[2][0]) {
            sprawdzanie = 1;
            return sprawdzanie;
        }
    }

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(tab[i][j] != 'X' && tab[i][j] != 'O') sprawdzanie = 0;
        }
    }

    return sprawdzanie;
}

void AI() {

    srand(time(NULL));

    int a, pos = 0;

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(pos != 1 && posx[i][j] != 10 && posy[i][j] != 20) {
                a = rand() % 2;
                    if(a == 1) {
                        posy[i][j] = 20;
                        pos++;
                }
            }
        }
    }

    wpisywanieAI(a);
}

void wpisywanieAI(int a) {

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(posy[i][j] == 20) {
              tab[i][j] = 'O';
            }
        }
    }

    rysowanie();
}
```
# header.h
```cpp
#ifndef HEADER_H_INCLUDED
#define HEADER_H_INCLUDED



#endif // HEADER_H_INCLUDED


void budowanie();

void rysowanie();

void wpisywanie(int pole);

void wpisywanie2(int pole);

int sprawdzanie();

int sprawdzanie2();

void AI();

void wpisywanieAI(int a);
```
#main.cpp
```cpp
#include <iostream>
#include <windows.h>
#include <stdlib.h>
#include "header.h"

using namespace std;

int main() {

    int pole = 10, ruchy, sp, wyb;

m:cout << "Kolko i Krzyzyk" << endl;
    cout << "1. Rozgrywka z druga osoba" << endl;
    cout << "2. Rozgrywka z AI" << endl;
    cin >> wyb;

    if (wyb == 1) {
        ruchy = 0;
        system("cls");
        budowanie(); //budowanie planszy/resetowanie
        rysowanie(); //rysowanie planszy

        do {
            wpisywanie();
            sp = sprawdzanie();
            ruchy++;
            if (sp == 1 || ruchy == 9) break;

            wpisywanie2();
            sp = sprawdzanie();
            ruchy++;
            if (sp == 1 || ruchy == 9) break;

        } while (ruchy < 9);
    }

    else if (wyb == 2) {
        ruchy = 0;
        system("cls");
        budowanie();
        rysowanie();

        do {
            wpisywanie();
            sp = sprawdzanie();
            ruchy++;

            if (sp == 1 || ruchy == 9) break;

            //AI
            system("cls");
            AI();
            sp = sprawdzanie();
            ruchy++;

            if (sp == 1 || ruchy == 9) break;
        } while (ruchy < 9);
    }

    else {
        system("cls");
        cout << "Bledna wartosc!" << endl;
        Sleep(2000);
        system("cls");
        goto m;
    }

    if (sp == 1 && ruchy % 2 == 1) cout << endl << "Koniec gry!" << endl << "Gracz 1 (x) wygral" << endl << endl;
    else if (sp == 1 && ruchy % 2 == 0) cout << endl << "Koniec gry!" << endl << "Gracz 2 (o) wygral" << endl << endl;
    else cout << endl << "Koniec gry!" << endl << "Remis!" << endl << endl;

    cout << "Zagrac jeszcze raz?" << endl;
    cout << "1.Tak" << endl;
    cout << "2.Nie" << endl;
    cin >> wyb;
    cout << endl;

    if (wyb == 1) {
        system("cls");
        cout << "Wczytywanie..." << endl;
        Sleep(1000);
        system("cls");
        goto m;
    }
    else return 0;

    return 0;
}
```
# Wersja 05.04.2022
# header.h
```cpp
#ifndef HEADER_H_INCLUDED
#define HEADER_H_INCLUDED



#endif // HEADER_H_INCLUDED


void budowanie();

void rysowanie();

void wpisywanie();

void wpisywanie2();

int sprawdzanie();

int sprawdzanie2();

void AI();

void wpisywanieZAI();

```

# funkcje.cpp
```cpp
#include <iostream>
#include <windows.h>
#include <stdlib.h>
#include <time.h>
#include "header.h"

using namespace std;

int tab[3][3], mod;

//budowanie resetuje plansze do wartosci domyslnych z kazdym restartem gry
void budowanie() {

    int iteracja = 0;
    mod = 1;

    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            tab[i][j] = iteracja;
            iteracja++;
        }
    }
}

void rysowanie() {

    int l = 0;

    cout << "    0   1   2 -> X" << endl;

    for(int i = 0; i < 3; i++) {
        cout << l << " ";
        l += 3;
        for(int j = 0; j < 3; j++) {
            cout << "|";
            if(tab[i][j] == 'X') printf(" x ");
            else if(tab[i][j] == 'O') printf(" o ");
            else if(j < 3) cout << "___";
            if(j == 2) cout << "|";
        }
        cout << endl;
    }
    cout << "Y |" << endl;
}

void wpisywanie() {

    int pole;
    mod %= 2;

    if (mod == 1) cout << "Gracz 1 (x)" << endl;
    if (mod == 0) cout << "Gracz 2 (o)" << endl;

    cout << "Wybierz pole (X + Y)" << endl;
    cin >> pole;
    system("cls");

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if (pole == tab[i][j]) {
                if (mod == 1) tab[i][j] = 'X';
                if (mod == 0) tab[i][j] = 'O';
            }
        }
    }

    mod++;

    rysowanie();
}

void wpisywanieZAI() {
    int pole;

    cout << "Gracz 1 (x)" << endl;
    cout << "Wybierz pole (X + Y)" << endl;
    cin >> pole;
    system("cls");

    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            if (pole == tab[i][j]) {
                tab[i][j] = 'X';
            }
        }
    }
    rysowanie();
}

int sprawdzanie() {

        int sprawdzanie = 0;

    for(int i = 0; i < 3; i++) {
        //sprawdzanie bokow
        if(tab[i][0] == tab[i][1] && tab[i][0] == tab[i][2] || tab[0][i] == tab[1][i] && tab[0][i] == tab[2][i]) {
            sprawdzanie = 1;
            return sprawdzanie;
        }

        //sprawdzanie przekatnych
        if(tab[0][0] == tab[1][1] && tab[0][0] == tab[2][2] || tab[0][2] == tab[1][1] && tab[0][2] == tab[2][0]) {
            sprawdzanie = 1;
            return sprawdzanie;
        }
    }

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(tab[i][j] != 'X' && tab[i][j] != 'O') sprawdzanie = 0;
        }
    }

    return sprawdzanie;
}

void AI() {

    srand(time(NULL));

    int a, pos = 0;

    m:for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            if(pos != 1 && tab[i][j] != 'X' && tab[i][j] != 'O') {
                a = rand() % 2;
                if(a == 1) {
                    tab[i][j] = 'O';
                    pos++;
                }
            }
        }
    }

    if (a == 0) goto m;

    rysowanie();
}
```
# main.cpp
```cpp
#include <iostream>
#include <windows.h>
#include <stdlib.h>
#include "header.h"

using namespace std;

int main() {

    int pole = 10, ruchy, sp, wyb;

m:cout << "Kolko i Krzyzyk" << endl;
    cout << "1. Rozgrywka z druga osoba" << endl;
    cout << "2. Rozgrywka z AI" << endl;
    cin >> wyb;

    if (wyb == 1) {
        ruchy = 0;
        system("cls");
        budowanie(); //budowanie planszy/resetowanie
        rysowanie(); //rysowanie planszy

        do {

            wpisywanie();
            sp = sprawdzanie();
            ruchy++;
            if (sp == 1 || ruchy == 9) break;

        } while (ruchy < 9);
    }

    else if (wyb == 2) {
        ruchy = 0;
        system("cls");
        budowanie();
        rysowanie();

        do {
            wpisywanieZAI();
            sp = sprawdzanie();
            ruchy++;

            if (sp == 1 || ruchy == 9) break;

            //AI
            system("cls");
            AI();
            sp = sprawdzanie();
            ruchy++;

            if (sp == 1 || ruchy == 9) break;
        } while (ruchy < 9);
    }

    else {
        system("cls");
        cout << "Bledna wartosc!" << endl;
        Sleep(2000);
        system("cls");
        goto m;
    }

    if (sp == 1 && ruchy % 2 == 1) cout << endl << "Koniec gry!" << endl << "Gracz 1 (x) wygral" << endl << endl;
    else if (sp == 1 && ruchy % 2 == 0) cout << endl << "Koniec gry!" << endl << "Gracz 2 (o) wygral" << endl << endl;
    else cout << endl << "Koniec gry!" << endl << "Remis!" << endl << endl;

    cout << "Zagrac jeszcze raz?" << endl;
    cout << "1.Tak" << endl;
    cout << "2.Nie" << endl;
    cin >> wyb;
    cout << endl;

    if (wyb == 1) {
        system("cls");
        cout << "Wczytywanie..." << endl;
        Sleep(1000);
        system("cls");
        goto m;
    }
    else return 0;

    return 0;
}
```
