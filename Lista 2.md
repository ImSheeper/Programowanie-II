# Zadanie 1

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
