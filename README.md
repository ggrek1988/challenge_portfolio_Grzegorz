
# Task 1


## Subtask 1
`8/10`

## Subtask 3
`1. Chęć poszerzania wiedzy w zakresie testowania.`

`2. Chęć poznania różnego podejścia do testów, co za tym idzie wykrywanie innego rodzaju błędów.`

## Subtask 4
`* Na czym polega ta aplikacja? Do czego służy?`
`* Jakie funkcjonalności znajdują się w aplikacji? Do czego służą. Czy są intuicyjne, czy może byś coś zmienił?`
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
- strona odwołuje się do zasobu jakie nie istnieje, metoda GET https://scouts-test.futbolkolektyw.pl/pl/favicon.ico, odpowiedz
404 Not Found

