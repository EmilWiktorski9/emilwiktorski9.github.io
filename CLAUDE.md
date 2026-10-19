# Zasady projektu

Ten plik czytasz automatycznie przy każdym uruchomieniu. Zawiera wyłącznie
zasady dotyczące strony. Repozytorium jest publiczne i ten plik może
przeczytać każdy, dlatego nie dopisuj tu informacji o właścicielu, notatek
roboczych ani ustaleń z rozmów. Na samej stronie plik jest wyłączony
w `_config.yml`.

Strona emilwiktorski.pl: profil, projekty SaaS, blog z procesem budowy
i newsletter.

## Zasady treści, twarde

1. **Zakaz myślnika i pauzy** (znaki — i –) w treści strony i w tekstach.
   Zamiast tego przecinek, kropka, dwukropek, nawias albo osobne zdanie.
   Sprawdzaj to przed oddaniem pracy.
2. **Zakazane zwroty:** "w dzisiejszym świecie", "w erze cyfrowej",
   "nie tylko... ale także", "odkryj", "zanurz się", "wykorzystaj potencjał",
   "rozwiązanie szyte na miarę", "przenieś na wyższy poziom",
   "w świecie, gdzie", "to więcej niż".
3. **Ton:** rzeczowo i szczerze. Liczby przed przymiotnikami: koszty, czas,
   przychód. Bez entuzjazmu sprzedażowego i bez obietnic. Zamiast ogólnika
   podaj konkret.
4. Ślad osobowości i lekkiej szorstkości jest pożądany. Wpadki i nietrafione
   narzędzia opisujemy wprost.

## Czym jest to repozytorium

Statyczna strona na Jekyllu, budowana automatycznie przez GitHub Pages
z gałęzi `main`. Domena emilwiktorski.pl (plik `CNAME`, nie usuwać).
Bez frameworków, bez npm, bez buildu po stronie użytkownika.

```
_config.yml               ustawienia: opis, bio, LinkedIn, zdjęcie, cel aplikacji
_data/projekty.yml        lista projektów na stronie głównej, jedno miejsce
index.html                strona główna: dwie kolumny, profil i projekty
blog.html                 lista wpisów (adres /blog/), formularz zapisu na górze
o-mnie.md                 strona o mnie
polityka-prywatnosci.md   polityka prywatności
archiwum.html             przekierowanie starego adresu /wydania/ na główną
kontakt.html              przekierowanie starego adresu /kontakt/ na główną
_posts/                   wpisy bloga, jeden plik to jeden wpis
_layouts/ _includes/      szablony i powtarzalne kawałki (zapis.html = newsletter)
assets/styl.css           cały wygląd, zmienne kolorów i krojów na górze pliku
assets/projekty/          logo i zrzuty ekranu projektów
SZABLON-WPISU-BLOG.txt    układ wpisu na bloga
INSTRUKCJA.md             instrukcja obsługi strony, aktualizuj przy zmianach
```

Wpisy: kategoria `blog`, nazwa pliku `RRRR-MM-DD-tytul.md`, bez polskich znaków
i spacji. Trzy ostatnie wpisy pokazują się na głównej w sekcji "Proces budowy".

## Decyzje wizualne, nie zmieniaj bez pytania

Styl "indie maker" (wzór: indiepage.co).

- Tło `#F7F7F4`, karty białe, tekst `#15161A`, akcent pomarańczowy `#FF5A1F`.
- Kroje: nagłówki Bricolage Grotesque, tekst Inter.
- Zaokrąglone karty z delikatnym cieniem, linki kontaktowe jako pigułki.
- Strona główna w dwóch kolumnach. Lewa: kółko z inicjałami albo zdjęcie,
  imię i nazwisko, bio, pasek celu, LinkedIn, e-mail, przycisk newslettera;
  na komputerze zostaje na miejscu przy przewijaniu. Prawa: karty projektów
  i skrót wpisów. Na telefonie jedna pod drugą, lewa na górze.
- Teksty (blog, wpisy, o mnie, polityka) w wąskiej kolumnie 40rem. Nagłówek,
  stopka i strona główna w szerokim kontenerze 66rem.
- Karta projektu: okładka (zrzut ekranu albo logo na kolorze projektu), logo,
  nazwa, adres, status (Live, Beta, W budowie), opis, narzędzia. Jeden projekt
  zajmuje całą szerokość, od dwóch układają się po dwa. Karta otwiera stronę
  projektu w nowej karcie. Bez wykresów przychodu; pole `przychod` czeka na
  później.
- Pasek celu: główna liczba "X / 10" to aplikacje, za które ktoś zapłacił
  (pole `zarabia: true`), druga linia "Wypuszczone aplikacje" liczy projekty
  ze statusem "Live". Na pasku pełny pomarańcz = zarabia, jasny = wypuszczona.
- Na głównej nagłówek strony nie powtarza nazwiska, bo jest w lewej kolumnie.
- Bez emotek i bez stockowej dekoracji.

## Newsletter i formularz zapisu

- Maile idą wyłącznie do MailerLite. Nie buduj własnego systemu zbierania maili.
- Kod formularza MailerLite w `_includes/zapis.html`: nie zmieniaj ani nie
  wymyślaj atrybutów name, id ani ukrytych pól, bo muszą zgadzać się z kontem
  MailerLite. Wygląd zmieniasz wyłącznie w CSS.
- Formularz ma stały id, więc na jednej stronie może być najwyżej jeden.
  Obecne miejsca: góra /blog, dół /o-mnie, koniec każdego wpisu. Strona główna
  ma przycisk prowadzący na /blog. Stopka jest bez formularza.
- Nagłówek i zdanie nad formularzem ustawiasz parametrami include
  `tytul` i `opis` w pliku strony, nie w `zapis.html`.
- Klauzula RODO pod formularzem zostaje. Jej usunięcie to decyzja prawna,
  nie wizualna.
- Polityka prywatności mówi, że strona nie ma analityki ani cookies, z wyjątkiem
  pingu MailerLite o wyświetleniu formularza. Każde nowe narzędzie zewnętrzne
  (analityka, piksel, czat) wymaga aktualizacji polityki i jej daty.

## Pułapki techniczne

**baseurl.** Jeśli strona wczytuje się jako goły tekst bez stylów, to prawie
zawsze rozjazd między `baseurl` w `_config.yml` a faktycznym adresem.
Własna domena albo repozytorium `nazwa.github.io` to `baseurl: ""`.

**Google Fonts.** API css2 samo serwuje rozszerzoną łacinkę przez unicode-range.
Po każdej zmianie krojów sprawdź polskie znaki, zwłaszcza ł, ą, ę, ż.

**Nie dodawaj bibliotek JavaScript.** Strona ma się ładować szybko i działać
bez buildu. Jedynym skryptem zewnętrznym jest skrypt formularza MailerLite.

**Pliki robocze.** Pliki bez front matter (np. `.md`, `.txt`) Jekyll publikuje
na stronie jako zwykłe pliki. Każdy nowy plik roboczy w katalogu głównym
dopisz do `exclude` w `_config.yml`.

**markdown="1"** w znacznikach `<div>` we wpisach musi zostać, inaczej markdown
w środku przestaje działać.
