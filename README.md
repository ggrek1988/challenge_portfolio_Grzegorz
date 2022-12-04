# Task 6

## Subtask 1

`11. Popełniłam błąd wpisując nazwisko Ani Miler – wpisałam Muler. Znajdź i zastosuj funkcję, która poprawi mój karkołomny błąd`

#### `UPDATE customers set surname = 'Miler' where customer_id = 3;`
#### `SELECT * FROM customers`

![obraz](https://user-images.githubusercontent.com/93194238/205487302-40a3425d-dcee-4f73-8e0b-1ef30026f7dd.png)

`12. Pobrałam za dużo pieniędzy od klienta, który kupił w ostatnim czasie film o id 4. Korzystając z funkcji join sprawdź, jak ma na imię klient i jakiego ma maila. W celu napisania mu wiadomości o pomyłce fantastycznej szefowej.`

#### `SELECT customers.name,customers.surname,customers.email FROM sale INNER JOIN customers on sale.customer_id = customers.customer_id where sale.movie_id = 4;`

![obraz](https://user-images.githubusercontent.com/93194238/205487627-61a0c60d-7903-4f53-bcc1-6c16ce02f772.png)

`13. Na pewno zauważył_ś, że sprzedawca zapomniał wpisać emaila klientce Patrycji. Uzupełnij ten brak wpisując: pati@mail.com`

#### `UPDATE customers set email = 'pati@mail.com' where customer_id = 4;`
#### `SELECT * FROM customers`

![obraz](https://user-images.githubusercontent.com/93194238/205487700-d569d3cd-3c79-4c2a-af5b-06c4c3145ff6.png)

`14. Dla każdego zakupu wyświetl, imię i nazwisko klienta, który dokonał wypożyczenia oraz tytuł wypożyczonego filmu. (wykorzystaj do tego funkcję inner join, zastanów się wcześniej, które tabele Ci się przydadzą do wykonania ćwiczenia).`

#### `SELECT customers.name, customers.surname , movies.title FROM sale INNER JOIN customers on sale.customer_id = customers.customer_id INNER JOIN movies on sale.movie_id = movies.movie_id;`

![obraz](https://user-images.githubusercontent.com/93194238/205487915-32bfe5f2-5bfd-4b8d-8f99-46bb74de5822.png)

`15. W celu anonimizacji danych, chcesz stworzyć pseudonimy swoich klientów. - Dodaj kolumnę o nazwie ‘pseudonym’ do tabeli customer,- Wypełnij kolumnę w taki sposób, aby pseudonim stworzył się z dwóch pierwszych liter imienia i ostatniej litery nazwiska. Np. Natalie Pilling → Nag`

#### `ALTER TABLE customers ADD pseudonym VARCHAR(15) NOT NULL;`
#### `UPDATE customers set pseudonym =CONCAT(LEFT(name,2),RIGHT(surname,1))`

![obraz](https://user-images.githubusercontent.com/93194238/205489895-5d6ec112-adb0-4190-90c2-3d776e6375c1.png)

`16. Wyświetl tytuły filmów, które zostały zakupione, wyświetl tabelę w taki sposób, aby tytuły się nie powtarzały.`

#### `SELECT DISTINCT movies.title FROM sale INNER JOIN movies on sale.movie_id = movies.movie_id`

![obraz](https://user-images.githubusercontent.com/93194238/205489988-76d269cc-1145-41ca-be90-28bd27078509.png)

`17. Wyświetl wspólną listę imion wszystkich aktorów i klientów, a wynik uporządkuj alfabetycznie. (Wykorzystaj do tego funkcji UNION)`

#### `SELECT actors.name, actors.surname FROM actors UNION SELECT customers.name,customers.surname FROM customers ORDER by 1 ASC;`

![obraz](https://user-images.githubusercontent.com/93194238/205490278-a4fd733a-02b8-4cee-872b-2ccadea7da55.png)

`18. Polskę opanowała inflacja i nasz sklepik z filmami również dotknął ten problem. Podnieś cenę wszystkich filmów wyprodukowanych po 2000 roku o 2,5 $ (Pamiętaj, że dolar to domyślna jednostka- nie używaj jej nigdzie).`

#### `UPDATE movies set price = price + 2.5 where year_of_production > '2000'`
#### `SELECT * FROM `movies` where year_of_production > '2000'`

![obraz](https://user-images.githubusercontent.com/93194238/205490486-622219fa-0f79-483a-86de-27ed0753440b.png)

`19. Wyświetl imię i nazwisko aktora o id 4 i tytuł filmu, w którym zagrał`

#### `SELECT actors.name, actors.surname, movies.title FROM cast INNER JOIN actors on cast.actor_id = actors.actor_id INNER JOIN movies on cast.movie_id - movies.movie_id where actors.actor_id = 4`

![obraz](https://user-images.githubusercontent.com/93194238/205490617-bf919f20-b08c-4624-88c8-132a4ed3b7b3.png)

`20. A gdzie nasza HONIA!? Dodaj do tabeli customers nową krotkę, gdzie customer_id = 7, name = Honia, surname = Stuczka-Kucharska, email = honia@mail.com oraz pseudonym = Hoa`

#### `INSERT INTO `customers` (`customer_id`, `name`, `surname`, `email`, `pseudonym`) VALUES ('7', 'Honia', 'Stuczka-Kucharska', 'honia@mail.com', 'Hoa')`

![obraz](https://user-images.githubusercontent.com/93194238/205490693-f5097681-1df4-445e-bd82-17facb99549a.png)


# Task 5

## Subtask 3

`1. Wyświetl tabelę actors w kolejności alfabetycznej sortując po kolumnie surname.`

#### `SELECT * FROM actors ORDER BY surname ASC; `

![obraz](https://user-images.githubusercontent.com/93194238/204133397-b8ffeeb2-ddeb-4837-b540-e45488133b5a.png)

`2. Wyświetl film, który powstał w 2019 roku.`

#### `SELECT * FROM movies where year_of_production = '2019';`

![obraz](https://user-images.githubusercontent.com/93194238/204133626-39aabb82-a4b6-4511-8aec-849ee5860faf.png)

`3. Wyświetl wszystkie filmy, które powstały między 1900, a 1999 rokiem.`

#### `SELECT * FROM movies where year_of_production BETWEEN '1999' and '2019';`

![obraz](https://user-images.githubusercontent.com/93194238/204134132-340442cb-c107-4dfe-a988-d782ef65f93a.png)

`4. Wyświetl JEDYNIE tytuł i cenę filmów, które kosztują poniżej 7$ `

#### `SELECT title, price FROM movies where price < '7'; `

![obraz](https://user-images.githubusercontent.com/93194238/204134316-a80474ea-566f-4943-a3ad-ef890b7e4864.png)

`5. Użyj operatora logicznego AND, aby wyświetlić aktorów o actor_id pomiędzy 4-7 (4 i 7 powinny się wyświetlać). NIE UŻYWAJ operatora BETWEEN.`

#### `SELECT * FROM actors where actor_id >= '4' and actor_id <= '7'; `

![obraz](https://user-images.githubusercontent.com/93194238/204134387-1a6aab3e-97cc-4277-81f6-182efcb0ca93.png)

`6. Wyświetl klientów o id 2,4,6 wykorzystaj do tego warunek logiczny. `

#### `SELECT * FROM actors where actor_id = '2' or actor_id = '4' or actor_id = '6'; `

![obraz](https://user-images.githubusercontent.com/93194238/204134502-3c044550-6405-4405-a7f6-cc646c3aad56.png)

`7. Wyświetl klientów o id 1,3,5 wykorzystaj do tego operator IN.`

#### `SELECT * FROM actors where actor_id in ('1','3','5');`

![obraz](https://user-images.githubusercontent.com/93194238/204134547-0297cca4-e5d9-4f70-aef8-8a4ef605873b.png)

`8. Wyświetl dane wszystkich osób z tabeli ‘actors’, których imię zaczyna się od ciągu “An”.`

#### `SELECT * FROM actors where name like 'An%';`

![obraz](https://user-images.githubusercontent.com/93194238/204134652-ee3c0552-ba23-49e1-9c85-f80c2d4866be.png)

`9. Wyświetl dane klienta, który nie ma podanego adresu email.`

#### `SELECT * FROM customers where email IS NULL;`

![obraz](https://user-images.githubusercontent.com/93194238/204134720-b7ab357e-a1c2-46af-b7f3-1dfaccd07057.png)

`10. Wyświetl wszystkie filmy, których cena wynosi powyżej 9$ oraz ich ID mieści się pomiędzy 2 i 8 movie_id.`

#### `SELECT * FROM movies where price > '9' and movie_id BETWEEN '2' and '8';`

![obraz](https://user-images.githubusercontent.com/93194238/204134874-d6efa7e6-aa6b-41dd-84c4-7f20667c8cf5.png)


# Task 4

## Subtask 2 (Testowanie eksploracyjne i raportowanie błędów)

`https://drive.google.com/drive/folders/1P6r504LB1sd5TKnNrj1OtVEKkvSZB9tb?usp=share_link`

## Subtask 3 (Do czego służy ta aplikacja?)

`* Do czego służy ta aplikacja? Jaki jest cel tej aplikacji?`<br/><br/>

Focusly to aplikacja w której znaleźć można ponad 1000 nagrań, które stworzone zostały przez ekspertów z różnych dziedzin, aby umożliwić rozwój na wielu płaszczyznach. Wśród dostepnych treści znleźć mozna między innymi cele rozwojowe, które pomogą w pracy nad różnymi sferami życia – zbudować odporność mentalną, zadbać o lepszy sen.
Co znajdziemy w aplikacji:
- Codziennie rekomendacje medytacji
- Cele rozwojowe (psychoedukacja)
- Kursy wprowadzające
- Medytacje różnych nurtów
- Medytacje mindfulness
- Wyzwania wspierające budowanie nawyków
- Ćwiczenia oddechowe
- Muzykę relaksacyjną i dźwięki natury
- Sylwetki ekspertów


`* Kto ma być użytkownikiem końcowym aplikacji?`<br/><br/>

Alikacja odpowiada na potrzeby pracodawców i pracowników, zarówno w obszarze zdrowia fizycznego, w tym odpowiednio dobranych aktywności życiowych, jak i kondycji psychicznej.  


`* Jakie dostrzegasz różnice pomiędzy testowaniem aplikacji internetowej, a natywnej?`<br/><br/>

Aplikacje natywne:
- dostęp do sprzętu urządzenia (geolokalizacja, kamera, mikrofon, akcelerometr, czujniki światła, kalendarz, powiadomienia push) i szeroka funkcjonalność dzięki temu;
- możliwość zaspokojenia większej ilości różnych żądań klientów i użytkowników;
- dane o użytkownikach mogą być łatwo gromadzone i analizowane;
- zazwyczaj stabilniej i wydajniej współpracują z dowolnymi urządzeniami używanymi na ich OS;
- nie ma ograniczenia funkcjonalności szybkością i jakością połączenia internetowego - aplikacja może działać bez dostępu do sieci;
- lepiej nadają się do aplikacji z niestandardowymi interfejsami i złożoną logiką biznesową.

Aplikacje internetowe:
- aplikacje webowe mogą działać na platformie z dowolnym systemem operacyjnym;
- deweloperzy nie muszą zatwierdzać aplikacji w sklepach;
- cykl rozwoju CSS, HTML i JavaScript przebiega wielokrotnie szybciej.




# Task 3
## Subtask 1 (Utworzenie formatki do zgłaszania błędów systemu)

`https://drive.google.com/drive/folders/1wn0Ow2HviSK05VomGGkcO7yDNOgVp1bz?usp=share_link`

## Subtask 2 (Testowanie według planów testów i raportowanie błędów)

`https://drive.google.com/drive/folders/1dBDP2RO2vElTxbAmz5yy8busaGQ38ZBE?usp=share_link`

## Subtask 3 (Raport z wykonanych testów)

`https://drive.google.com/drive/folders/1Fez0Xc6YDqSBjTJLItIFjg0kWe0rjDkE?usp=share_link`

# Task 2

## Subtask 1 (Pisanie przypadków testowych na podstawie User Story.)

`https://drive.google.com/file/d/1UihBlMBSMOpnD0O0XvJQnXg5LJA5bhJS/view?usp=share_link`

## Subtask 2 (Pisanie przypadków testowych na podstawie “własnych doświadczeń.)

`https://drive.google.com/file/d/1I9qsKkDP84IEZ0WHDNdfOVt5KG4T8mK4/view?usp=share_link`

## Subtask 3 (Po co piszemy test case’y?)

`Przypadki testowe piszemy, aby udokumentować w przejrzysty sposób różne możliwości obsłużenia modułów w ramach danej aplikacji. Dobre pokrycie przypadkami testowymi oprogramowania daje nam pewność podczas testów, że nie pominęliśmy żadnej ważnej funkcjonalności.`

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

`* Oceń interfejs aplikacji (wygląd) – czy Ci się podoba, czy nie? Czy aplikacja jest intuicyjna? (Intuicyjna, czyli np. nie masz problemu ze zrozumieniem, co należy kliknąć, żeby wejść do formularza dodawania nowego zawodnika piłki nożnej do systemu).`

Po zalogowaniu się do platformy, może rzucić się w oczy dość ubogi interfejs graficzny z mała ilością dostępnych funkcji. W każdej dostępnej podstronie konieczne byłoby poprawne sformatowanie wyświetlanych danych jak ich ułożenie oraz wyrównanie. Na sam początek platforma intuicyjna, przy zagłębieniu się w dodatkowe funkcje aplikacja nie posiada opisu dostępnych działań. Brak opisu działań, jak i brak opisu  poszczególnych podstron czyni platformę coraz mniej intuicyjną. W dostępnych formularzach edycji, dodawania zarówno gracza jak i spotkań brak jasnych komunikatów błędów, co nie daje jasnej informacji i konkretnym błędnie uzupełnionym pól. Dostępne elementy nie skalują się wraz ze zmianą rozmiaru przeglądarki lub rozdzielczości  ekranu/monitora.


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
- zastąpienie wyswietlanych pustych danych w tabeli na znak "-"
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
- Przycisk "CLEAR", nie powoduje wyczyszczenia danych z formularza
#### 4.2) Appearance/pages design bugs
- pola do wprowadzenia nie mają ściśle zachowanego porządku, możliwa byłaby zmiana ułożenia poszczególnych pól według konkretnego schematu danych miedzy, danymi wymaganymi a danymi dodatkowymi.

#### 4.3) Differences between browsers Chrome 107.0.5304.88 (64 bity) and Firefox 105.0.3 (64 bity)
- Po wpisaniu w Chromie adresu email w polu E-mail , pole podświetla się na niebiesko, w firefoxie brak takiego efektu

### 5) Podstrona Dodawanie meczu dla gracza
#### 5.1) Bugs
- brak tłumaczenia na język polski przycisków "SUBMIT" i "CLEAR"
- brak tłumaczenia na język komunikatu o nieuzupełnionym polu "Required"
- brak walidacji pola Data, można wpisać wartości poza zakresem prawidłowej daty np. 01.01.275324
- brak walidacji przed zapisem pola Numer, Recenzja, Czas gry, Stracone gole, Zdobyte gole, można wpisać wartości float , liczby zmiennoprzecinkowe
- brak tłumaczenia na język polski "Web match", "General"
#### 5.2) Appearance/pages design bugs
- brak zachowanej logiki umieszczenia pól na formularzu
- przy wartościach liczbowych brak informacji o zakresie wprowadzania danych ,jak i informacji o możliwości użycia wartości(zmiennoprzecinkowych, całkowitych)

### 6) Podstrona Edycja meczu dla gracza
#### 6.1) Bugs
- podczas edycji meczu, i zaktualizowaniu danych, przycisk "Clear" zamiast czyścić pola cofa wartość do wartość przed zmianą.
- w polu Numer, możliwe wpisanie wartość e(potęgi 10), brak walidacji
- brak tłumaczenia na język polski przycisków "SUBMIT" i "CLEAR"
- brak tłumaczenia na język polski przycisków "Meta dane"
- w polach liczbowych mozliwośc wprowadzenia wartości mniejszych od zera
#### 6.2) Appearance/pages design bugs
- brak zachowanej logiki umieszczenia pól na formularzu
- przy wartościach liczbowych brak informacji o zakresie wprowadzania danych ,jak i informacji o możliwości użycia wartości(zmiennoprzecinkowych, całkowitych)


### 7) Podstrona Raportów, raport, lista raportów
#### 7.1) podstrona Tworzenie raportu
##### 7.1.1) Bugs
- brak tłumaczenia na język polski przycisków "SUBMIT" i "CLEAR"
- brak tłumaczenia na język angielski nazwy zakładki "mecze gracza"
- brak reakcji po użyciu przycisku "Clear"
##### 7.1.2) Appearance/pages design bugs
- brak informacji o działaniu i celu podstrony
- podstrona mało intuicyjna, mało czytelna zawierająca zle sformatowaną treść.
#### 7.2) podstrona raportu
##### 7.2.1) Bugs
- brak tłumaczenia na język polski przycisku "save"
- w dostępnych "framach" wprowadzania własnej treści do raportu źle działający przycisk "numbered-list", lista numerowana jest zawsze od 1.

##### 7.2.2) Appearance/pages design bugs
- brak informacji o działaniu i celu podstrony
- podstrona mało intuicyjna, mało czytelna zawierająca zle sformatowaną treść.
- brak możliwości wydrukowania raportu, możliwe byłoby dodanie możliwości wydruku
- brak skalowania tabelki z raportem, do rozmiarów przeglądarki i okna

#### 7.3) podstrona tabelki z wprowadzonymi raportami
##### 7.3.1) Bugs
- przycisk "+ dodaj raport", przekierowuje na stronę listy meczy, bez informacji o dodatkowych krokach
- brak możliwości sortowania po kolumnach

##### 7.3.2) Appearance/pages design bugs
- brak skalowania tabelki z raportem, do rozmiarów przeglądarki i okna
- w tabeli raportów brak opisu tabelki

### 8 Podstrona "Rozpocznij mecz"
#### 8.1) Bugs
- brak opisu dostepych działań
- działanie ikonka z koszem (usuwanie pozycji), nie usuwa ani meczu ani pozycji
- źle działająca opcja informacji o kolejnej połowie, brak blokady wartości Powyżej < 2.
- brak tłumaczenia na język polski działania "Faul"
- brak ustawionej nazwy/zakładki title, wpisany jest adres strony

#### 8.2) Appearance/pages design bugs
- brak opisu strony oraz brak instrukcji działania wizualizacji meczu
- brak opisu dostępnych opcji po rozpoczęciu meczu
- po rozpoczęciu meczu i dodania akcji, brak sformatowanego przycisku "zapisz"



