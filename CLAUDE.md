# Zasady projektu

Ten plik czytasz automatycznie przy każdym uruchomieniu. Zawiera wyłącznie
zasady dotyczące strony. Repozytorium jest publiczne i ten plik może
przeczytać każdy, dlatego nie dopisuj tu informacji o właścicielu, notatek
roboczych ani ustaleń z rozmów. Na samej stronie plik jest wyłączony
w `_config.yml`.

Strona emilwiktorski.pl: jednostronicowa wizytówka. Kto to jest, co zrobił
(projekty), co może zrobić dla firm (oferta) i kontakt.

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
_config.yml               ustawienia: opis, teksty góry strony, kontakt, Formspree
_data/projekty.yml        sekcja "Co zrobiłem", jedno miejsce na projekty
_data/oferta.yml          kafle sekcji "Co mogę dla Ciebie zrobić"
index.html                strona główna: start, projekty, oferta, kontakt
polityka-prywatnosci.md   polityka prywatności (sekcja o formularzu włącza się sama)
blog.html, o-mnie.html    przekierowania starych adresów /blog/ i /o-mnie/ na główną
archiwum.html             przekierowanie starego adresu /wydania/ na główną
kontakt.html              przekierowanie starego adresu /kontakt/ na główną
_layouts/ _includes/      szablony i powtarzalne kawałki (zapis.html = newsletter, nieużywany)
assets/styl.css           cały wygląd, zmienne kolorów i krojów na górze pliku
assets/projekty/          logo i zrzuty ekranu projektów
SZABLON-WPISU-BLOG.txt    układ wpisu na bloga, na przyszłość
INSTRUKCJA.md             instrukcja obsługi strony, aktualizuj przy zmianach
```

Blog i newsletter są na razie wyłączone. Układ `wpis` i `_includes/zapis.html`
zostają w repozytorium, żeby dało się je włączyć bez budowania od zera.

## Decyzje wizualne, nie zmieniaj bez pytania

Prosta wizytówka: im mniej, tym lepiej.

- Tło `#F7F7F4`, karty białe z cienką ramką, tekst `#12141A`, akcent niebieski `#2448D8`.
- Kroje: nagłówki Bricolage Grotesque, tekst Inter.
- Jedna strona, kolejno: start (nagłówek, wstęp, dwa przyciski tej samej szerokości
  obok siebie), "Co zrobiłem", "Co mogę dla Ciebie zrobić", kontakt, stopka.
- Nagłówek: nazwa po lewej, zakładki "Co zrobiłem" i "Co mogę zrobić", przycisk
  Kontakt. Na telefonie zakładki znikają, zostaje nazwa i Kontakt w jednej linii.
- Karta projektu: logo, nazwa, status ("Live" wyświetla się jako "Działa"), opis,
  fakty (start, dla kogo, opcjonalnie przychód), link. Jeden projekt na całą
  szerokość, od dwóch po dwa w rzędzie.
- Oferta: kafle dwa na dwa, na telefonie jeden pod drugim.
- Kontakt: tekst i ikony (mail, LinkedIn, Facebook) po lewej, formularz po prawej,
  na telefonie formularz pod spodem. Ikona Facebooka pokazuje się tylko, gdy
  w `_config.yml` jest link.
- Bez emotek, bez stockowej dekoracji, bez placeholderów typu "wkrótce".

## Formularz kontaktowy

- Formspree, identyfikator w `_config.yml` (`formspree`). Puste pole = zamiast
  formularza przycisk z adresem e-mail.
- Wysyłka przez krótki skrypt w `index.html` (fetch), bez bibliotek. Bez JS
  formularz działa zwykłym wysłaniem.
- Pole `_gotcha` to pułapka na spam, zostaje ukryte.
- Klauzula RODO pod formularzem zostaje.
- Polityka prywatności sama dopisuje sekcje o Formspree, gdy pole `formspree`
  jest uzupełnione. Przy włączeniu zmień datę w `polityka_aktualizacja`.

## Newsletter i formularz zapisu

- Maile idą wyłącznie do MailerLite. Nie buduj własnego systemu zbierania maili.
- Kod formularza MailerLite w `_includes/zapis.html`: nie zmieniaj ani nie
  wymyślaj atrybutów name, id ani ukrytych pól, bo muszą zgadzać się z kontem
  MailerLite. Wygląd zmieniasz wyłącznie w CSS.
- Formularz ma stały id, więc na jednej stronie może być najwyżej jeden.
  Obecnie nie jest osadzony nigdzie poza końcem wpisów (blog wyłączony).
- Nagłówek i zdanie nad formularzem ustawiasz parametrami include
  `tytul` i `opis` w pliku strony, nie w `zapis.html`.
- Klauzula RODO pod formularzem zostaje. Jej usunięcie to decyzja prawna,
  nie wizualna.
- Polityka prywatności mówi, że strona nie ma analityki ani cookies. Każde nowe
  narzędzie zewnętrzne (analityka, piksel, czat, nowy formularz) wymaga
  aktualizacji polityki i jej daty.

## Pułapki techniczne

**baseurl.** Jeśli strona wczytuje się jako goły tekst bez stylów, to prawie
zawsze rozjazd między `baseurl` w `_config.yml` a faktycznym adresem.
Własna domena albo repozytorium `nazwa.github.io` to `baseurl: ""`.

**Google Fonts.** API css2 samo serwuje rozszerzoną łacinkę przez unicode-range.
Po każdej zmianie krojów sprawdź polskie znaki, zwłaszcza ł, ą, ę, ż.

**Nie dodawaj bibliotek JavaScript.** Strona ma się ładować szybko i działać
bez buildu. Na stronie głównej nie ma skryptów zewnętrznych, jest tylko krótki
skrypt wysyłki formularza kontaktowego.

**Pliki robocze.** Pliki bez front matter (np. `.md`, `.txt`) Jekyll publikuje
na stronie jako zwykłe pliki. Każdy nowy plik roboczy w katalogu głównym
dopisz do `exclude` w `_config.yml`.

**markdown="1"** w znacznikach `<div>` we wpisach musi zostać, inaczej markdown
w środku przestaje działać.
