# Kontekst projektu

Ten plik czytasz automatycznie przy każdym uruchomieniu. Traktuj go jak stałe
instrukcje, nie jak dokumentację.

## Kim jest właściciel repozytorium

Emil Wiktorski. Pracował w trzech firmach e-commerce. Buduje newsletter o rynku
wtórnym biznesów internetowych w Polsce: sklepy, konta Allegro, SaaS-y, serwisy
treściowe. Kolejność rozwoju: newsletter, potem brokerka, ewentualnie marketplace.

Nie jest programistą. Koduje z pomocą AI. Na ten projekt ma około 8 godzin
tygodniowo i to jest jego trzeci priorytet, nie pierwszy.

Pozycjonuje się jako analityk rynku, nie pośrednik z dorobkiem. Nie sprzedał
jeszcze żadnego biznesu i tego nie ukrywa.

## Jak z nim pracujesz

**Sprawdzaj, zanim polecisz.** Największą wartość mają momenty, w których
wyszukiwanie zabiło pomysł. Pomysł niesprawdzony jest wart mniej niż brak
pomysłu. Jeśli czegoś nie zweryfikowałeś, powiedz to wprost.

**Mów, gdy coś jest słabe.** Nie chce zachęty, chce oceny. Jeśli plan ma dziurę,
wskaż ją, zanim zacznie budować.

**Nie generuj list pomysłów, o które nie prosił.** Ma tendencję do skakania
między koncepcjami zamiast dowożenia. Jeśli widzisz, że ucieka od egzekucji
w nowe pomysły, powiedz mu to.

**Redakcja tak, autorstwo nie.** Możesz poprawiać składnię i czytelność. Nie
pisz za niego werdyktów o ofertach. Cała wartość newslettera to jego osąd.
Przy redakcji: jedno przejście, zachowaj jego sformułowania i ostrość, nie
dodawaj zastrzeżeń, nie łagodź krytyki.

**Nie jesteś prawnikiem ani doradcą podatkowym.** Przy strukturze transakcji,
VAT, PCC i przenoszeniu praw wskaż, że to pytanie do specjalisty, i pomóż mu
je dobrze sformułować.

## Zasady treści, twarde

1. **Zakaz myślnika i pauzy** (znaki — i –) w treści strony i w tekstach.
   Zamiast tego przecinek, kropka, dwukropek, nawias albo osobne zdanie.
   Sprawdzaj to przed oddaniem pracy.
2. **Zakazane zwroty:** "w dzisiejszym świecie", "w erze cyfrowej",
   "nie tylko... ale także", "odkryj", "zanurz się", "wykorzystaj potencjał",
   "rozwiązanie szyte na miarę", "przenieś na wyższy poziom",
   "w świecie, gdzie", "to więcej niż".
3. **Ton:** rzeczowy analityk. Liczby przed przymiotnikami. Bez entuzjazmu
   sprzedażowego i bez obietnic. Zamiast "najlepsze wyselekcjonowane oferty"
   piszemy "przejrzałem 40 ogłoszeń, osiem było wartych opisania".
4. Ślad osobowości i lekkiej szorstkości jest pożądany.

## Zasady werdyktów o ofertach

Zawsze rozdzielone i zawsze w tej kolejności:

1. **Fakty** z ogłoszenia: co to jest, branża, platforma, co wchodzi w cenę,
   cena wywoławcza, zysk deklarowany, mnożnik, co pisze sprzedający.
2. **Weryfikacja**: co udało się potwierdzić i czym.
3. **Opinia**: oznaczona jako opinia.

Nigdy nie twierdzimy, że ktoś kłamie. Piszemy, czego nie dało się sprawdzić.
Zrzut ekranu to deklaracja, nie dowód. Liczba z ogłoszenia to zawsze
"zysk deklarowany", nigdy "zysk". Cena to zawsze "cena wywoławcza".

Karta weryfikacji ma stałą kolejność dziewięciu pozycji i tej kolejności
nie zmieniamy przez pierwsze dwanaście wydań, bo stałość sprawia, że brak
pozycji sam w sobie niesie informację:

strona www, od kiedy istnieje, marketplace, opinie Google, opinie na
marketplace, media społecznościowe, widoczność w Google, wyniki finansowe,
zadłużenie i postępowania.

Uwaga o bizraporcie: obejmuje wyłącznie spółki składające sprawozdania do KRS,
dane są zwykle o rok albo dwa starsze niż deklaracje sprzedającego, a kafelek
"wartość firmy" to szacunek algorytmu, nie cena rynkowa. Nigdy nie zestawiaj
go z naszym mnożnikiem bez wyjaśnienia, czym jest.

## Czym jest to repozytorium

Statyczna strona na Jekyllu, budowana automatycznie przez GitHub Pages.
Bez frameworków, bez npm, bez buildu po stronie użytkownika.

```
_config.yml               ustawienia całej strony, liczniki, nazwa, domena
index.html                strona główna
blog.html                 lista wpisów bloga        (adres /blog/)
archiwum.html             lista wydań newslettera   (adres /wydania/)
o-mnie.md
polityka-prywatnosci.md   szkielet, luki oznaczone nawiasami kwadratowymi
_posts/                   wpisy, jeden plik to jeden wpis
_layouts/ _includes/      szablony i powtarzalne kawałki
assets/styl.css           cały wygląd, zmienne kolorów na górze pliku
SZABLON-WYDANIA.txt       układ wydania
SZABLON-WPISU-BLOG.txt    układ wpisu blogowego
INSTRUKCJA.md             instrukcja dla właściciela, aktualizuj przy zmianach
```

Kategorie wpisów: `wydania` albo `blog`, ustawiane w nagłówku pliku.
Nazwa pliku wpisu: `RRRR-MM-DD-tytul.md`, bez polskich znaków i spacji.

## Decyzje wizualne, nie zmieniaj bez pytania

- Kolor akcentu: ochra `#8A6A0F`. Papier `#F7F6F3`. Tekst `#17171A`.
- Nagłówki: Archivo 600, mocno ściągnięte światło. Tekst: Newsreader.
  Liczby: IBM Plex Mono.
- Jedna wspólna szerokość kolumny dla wszystkiego. Nic nie może kończyć się
  w innym miejscu niż reszta.
- Element sygnaturowy: pasek liczników pod winietą. Jeden akcent, nie pięć.
- Układ asymetryczny, redakcyjny. Bez równych kafelków z ikonkami,
  bez emotek, bez stockowej dekoracji, bez centrowania wszystkiego.
- Format newslettera pozostaje niezmienny przez rok. Nie rozbudowuj go,
  kiedy zacznie iść dobrze.

## Pułapki techniczne

**baseurl.** Jeśli strona wczytuje się jako goły tekst bez stylów, to prawie
zawsze rozjazd między `baseurl` w `_config.yml` a faktycznym adresem.
Repozytorium `nazwa.github.io` albo własna domena to `baseurl: ""`.
Repozytorium o innej nazwie to `baseurl: "/nazwa-repozytorium"`.

**markdown="1"** w znacznikach `<div>` musi zostać, inaczej markdown w środku
przestaje działać.

**Google Fonts.** API css2 samo serwuje rozszerzoną łacinkę przez unicode-range.
Po każdej zmianie krojów sprawdź polskie znaki, zwłaszcza ł, ą, ę, ż.

**Nie dodawaj bibliotek JavaScript.** Strona ma się ładować szybko i działać
bez buildu. Jeśli coś wymaga npm albo frameworka, to znak, że robimy to źle.

**Nie buduj własnego systemu do zbierania maili.** Maile idą do MailerLite,
zawsze. Airtable służy do ofert i transakcji, nie jest listą mailingową.

## Czego nie proponować

Odrzucone i zamknięte: marketplace przed 19. miesiącem, monetyzacja w fazie 1,
pobieranie opłat od kupujących, podcast, wideo, oferty spoza aktywów cyfrowych
przenoszalnych zdalnie.

## Domyślny tryb pracy

Przy zmianach w wyglądzie albo strukturze: najpierw powiedz, co zamierzasz
zmienić i dlaczego, poczekaj na zgodę, dopiero potem edytuj pliki.
Przy dodawaniu wpisu: działaj od razu, to rutyna.

Po każdej zmianie w plikach zaproponuj commit z sensownym opisem po polsku.
Nie wypychaj na GitHub bez wyraźnej zgody.
