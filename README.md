
# Task 1


## Subtask 1
`8/10`

## Subtask 3
`1. Chęć poszerzania wiedzy w zakresie testowania.`

`2. Chęć poznania różnego podejścia do testów, co za tym idzie wykrywanie innego rodzaju błędów.`

## Subtask 4
`* Na czym polega ta aplikacja? Do czego służy?`<br/><br/>
Aplikacja dla Harcerzy, służąca do przechowywania informacji o graczach piłki nożnej wraz z dokładnymi statystykami rozegranych meczy.

`* Jakie funkcjonalności znajdują się w aplikacji? Do czego służą. Czy są intuicyjne, czy może byś coś zmienił?`<br/><br/>
Dostępne funkcje:
- zbiór statystyk dostępnych rekordów w bazie, podsumowanie takich danych jak Ilość graczy,Ilość meczy,Ilość raportów,Ilość akcji
- możliwość przetłumaczenia strony na dwa dostępne języki Angielski i Polski
- wyświetlanie listy graczy, wraz z filtrowaniem pojedynczych wartości
- możliwość exsportu danych do plików csv
- możliwość wydrukowania listy graczy
- dodawanie i edycja pojedynczego gracza
- dodanie meczu w którym uczestniczył gracz
- wygenerowanie raportów dotyczących pojedynczego gracza
- wizualizacja rozegranego meczu dla pojedynczego gracza.

Preferowane zmiany zostały opisane poniżej w punkcie "Appearance/pages design bugs"

`* Oceń interfejs aplikacji (wygląd) – czy Ci się podoba, czy nie?`
`* Czy aplikacja jest intuicyjna? (Intuicyjna, czyli np. nie masz problemu ze zrozumieniem, co należy kliknąć, żeby wejść do formularza dodawania nowego zawodnika piłki nożnej do systemu).`

`* Czy zauważasz jakieś błędy? Albo coś wydaje Ci się błędem?`

### 1) Podstrona logowania
#### 1.1) Bugs
- Pomimo wybranego tłumaczenia "Polski" , nie przetłumaczone są takie wyrazy jak "Scouts Panel", "Login", 
- można się tutaj również zastanawiać czy komunikaty błędów przy walidacji pól i login powinny być przetłumaczone na jezyk polski
#### 1.1) Appearance/pages design bugs
- Po wpisaniu nieprawidłowych danych, pojawiający się komunikat błędu przesuwa pole wyboru języka jak i przycisk "zaloguj", na dół co powoduje nałożenie się przycisku i listy rozwijanej na sekcje odpowiedzialną za pole panelu logowania.
- po wpisaniu nieprawidłowego loginu wyskakuje komunikat "Identifier or password invalid." co można byłoby zastąpić dokładniejszym komunikatem zamiast "Identifier" to "username or your e-mail" gdzie "username" możemy również zastąpić słowem "login".
- przy użyciu Devtools , zakładka "dostępność", przy użyciu znacznika przy opcji "Kolejność klawisza Tab", można się zastanowić czy przejście do pola wyboru języka przez klawisz "tab" powinien być dopiero po uzupełnieniu loginu i hasła, a nie jako pole ustawione jako pierwsze do wyboru. Aktualna kolejność(Login,Hasło,jezyk,przycik zaloguj)
- można byłoby również przemyśleć nad zmianą title(nazwy zakładki) "Scouts panel - zaloguj" 
#### 1.3) Differences between browsers Chrome 107.0.5304.88 (64 bity) and Firefox 105.0.3 (64 bity)
- przy pierwszym załadowaniu strony logowania na Chromie pola login i hasło posiadają ustawione "properties" background na wartość #E8F0FE, w Firefoxie wartość ustawiona jest na 'None'
#### 1.4) Bug REST API
- po wpisaniu prawidłowych danych i zalogowaniu się do systemu wysyłany jest endpoint POST https://api.scouts-test.futbolkolektyw.pl/auth/local ,w którym przekazywany jest json z podanym hasłem 
- po wpisaniu prawidłowych danych i zalogowaniu się do systemu wysyłane są endpointy GET które zwracają jedynie wartość text'ową, mozna tutaj sprawdzić czy nie lepiej jednak odpowiedz zmienić na jsona
- wysyłane są endpointy z metodą OPTIONS np https://api.scouts-test.futbolkolektyw.pl/auth/local , tutaj trzeba zadać pytanie programistom w jakim celu uzytyy jest taki request ponieważ metoda Http OPTIONS nie zwraca body odpowiedzi a tylko informacje o dostępnych metodach na wysłanym zasobie, taka informacja nie jest potrzebna użytkownikowi.

#### 1.5) Bugs in Console devtools
* W przeglądarce chrome przy przekierowaniu na stronę logowania wyskakuje komunikat błędu
<br/>-- Unchecked runtime.lastError: Could not establish connection. Receiving end does not exist.
* W przeglądarce Firefox przy przekierowaniu na stronę logowania wyskakuje komunikat błędu:
<br/>-- Nieznana własność „-moz-osx-font-smoothing”.  Deklaracja opuszczona.
<br/>-- Nieznana pseudoklasa lub pseudoelement „-ms-input-placeholder”.
<br/>-- Zbiór reguł zignorowany z powodu błędnego selektora. 
<br/>-- Nieznana pseudoklasa lub pseudoelement „-ms-expand”.  Zbiór reguł zignorowany z powodu błędnego selektora.
<br/>-- Błąd podczas przetwarzania wartości dla „animation”.  Deklaracja opuszczona.
<br/>-- Układ został wymuszony przed pełnym wczytaniem strony. Jeśli arkusze stylów nie są jeszcze wczytane, może spowodować to miganie treści bez nałożonych stylów. <br/>-- Niektóre ciasteczka niewłaściwie wykorzystują zalecany atrybut „SameSite” 2
<br/>-- Nieznana własność „-moz-osx-font-smoothing”.  Deklaracja opuszczona.

### 2) Panel użytkownika (podstrona strona główna)
#### 2.1) Bugs
- po użyciu działania tłumaczenia na "English" nie tłumaczy słowa "Polski" na "Polish"
- po użyciu działania tłumaczenia na "Polski" nie tłumaczy słowa "Scouts Panel" oraz "Dev team contact" 
- podczas nie zapisania meczu, na samym dole strony pojawia się informacja przy której nie działa przekierowanie przez link "Wróć do raportu"

#### 2.2) Bug REST API
- strona odwołuje się do zasobu który nie istnieje, metoda GET https://scouts-test.futbolkolektyw.pl/pl/favicon.ico, odpowiedz
404 Not Found

### 3) Strona z Listą Graczy
#### 3.1) Bugs
- brak tłumaczenia słowa "search" na język polski
- brak tłumaczenia słowa "download csv","print","view columns", "Filter table" na język polski
- brak tłumaczenia słowa "Age", "Rate", "FILTERS", 'RESET' na język polski w działaniu filtrowania pozycji "view columns"
- brak sortowania przy kolumnie Mecze i Raport.
- brak tłumaczenia "Sorry, no matching records found" na jezyk polski przy pustej liscie graczy
- wyszukiwarka "search" powinna działać dynamicznie, wyszukując pozycję juz po wpisaniu pierwszego ciągu znaków
- Po wyszukaniu gracza przy użyciu wyszukiwarki "Search", i chęci zwrócenia całej listy graczy należy ustawić pole puste i użyć przycisku "enter". 
- Użycie działania "download csv", powoduje zapisanie tylko 11 aktualnie widocznych pozycji z listy
- Po edycji pliku csv w edytorze exel lub notepad ++ , widoczne są źle przenoszone dodatkowe kolumny zawierające treść "[object Object]" 
- Pomimo wyłączenia widoczności kolumn poprzez działanie "view columns", wszystkie kolumny przenoszone są do pliku csv poprzez działanie "download csv" 
- w działaniu "Filter table" brak walidacji pola Age(min i max) możliwość wpisania wartości alfabetycznych , taka sama sytuacja jest w polu Rate(min, max)
- w działaniu "Filter table" , przycisk "RESET" powoduje wyczyszczenie wprowadzonych wartości do wyszukiwania ale nie czysci listy graczy do pierwotnych ustawień, wyświetlając cała listę graczy.
- W pojawiającym sie popupie działania "Filter table", wyświetlone pola nie są poprawnie sformatowane, rozmiar i ułożenie jest chaotyczne. 
#### 3.2) Appearance/pages design bugs
- nieczytelna tabelka z listą wszystkich graczy, konieczna byłaby zmiana formatowania danych
- po najechaniu na nazwę kolumny pojawia się dymek ze słowem "sort", mozna było by przemyśleć zmianę nazwy, tutaj również nie tłumaczy się słowo przy wybraniu tłumaczenia na Polski
- tabelka z graczami nie skaluje się wraz z zmniejszającą się rozdzielczością
- Po użyciu działania "Print", forma wydruku jest nieczytelna.
#### 3.3) Differences between browsers Chrome 107.0.5304.88 (64 bity) and Firefox 105.0.3 (64 bity)
- W przeglądarce Firefox kolor zaznaczenia/nakierowania na danego gracza z listy jest niewidoczny, jednak w obu przeglądarkach konieczna byłaby zmiana na ciemniejszy kolor. 

### 4) Strona Edycji Gracza
#### 4.1) Bugs
- brak walidacji pola "E-mail", możliwe wpisanie niepoprawnego emaila.
- brak walidacji pola "Imie", możliwość wpisania danych liczbowych
- brak walidacji pola "Nazwisko", możliwość wpisania danych liczbowych
- brak walidacji pola "telefon", możliwość wpisania danych alfabetycznych
- brak walidacji pola "data urodzenia", możliwość wpisania niestandardowej daty np: 11.11.23443, nie powoduje natychmiastowej informacji o błędnej dacie.
- Brak dokładnej informacji o przyczynach błędu przy zapisaniu gracza, wyskakuje komunikat "Nie udało się zaktualizować gracza", co nie daje jasnej informacji do błędnie uzupełnionego pola
- Brak blokady wpisania dużej ilości znaków w poszczególnych polach, np. w polu "Klub" wpisanie dużej liczby znaków bez użycia białych znaków (spacja), powoduje rozjechanie się tabelki z listą graczy
- Brak tłumaczenia słowa "Łączy nas piłka" na język Angielski
- Brak tłumaczenia słowa "90 minut" na język Angielski
- Brak tłumaczenia przycisków "SUBMIT" i "CLEAR "na język Polski
- Przez edycje możliwość dodania dwa razy takiego samego gracza z takim samym e-mailem.
#### 4.2) Differences between browsers Chrome 107.0.5304.88 (64 bity) and Firefox 105.0.3 (64 bity)
- Po wpisaniu w Chromie adresu email w polu E-mail , pole podświetla się na niebiesko, w firefoxie brak takiego efektu




