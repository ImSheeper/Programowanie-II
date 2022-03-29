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
