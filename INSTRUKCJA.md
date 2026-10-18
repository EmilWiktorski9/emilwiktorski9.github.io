# Instrukcja obsługi strony

Napisane dla kogoś, kto nie programuje. Nic nie trzeba instalować na komputerze.

Każdą zmianę robisz na github.com w repozytorium strony: otwierasz plik, klikasz ikonę ołówka (**Edit**), zmieniasz tekst i na dole klikasz zielony **Commit changes**. Po jednej, dwóch minutach zmiana jest na emilwiktorski.pl. Zamiast tego możesz też poprosić Claude Code, żeby zrobił to za ciebie.

---

## 1. Co gdzie zmieniasz

| Co | Gdzie |
|---|---|
| Zdanie o tobie na stronie głównej | `_config.yml`, linia `bio` |
| Link do LinkedIna | `_config.yml`, linia `linkedin` |
| Zdjęcie profilowe | `_config.yml`, linia `zdjecie` (rozdział 3) |
| Cel na pasku postępu (10 aplikacji) | `_config.yml`, linia `cel_aplikacji` |
| Adres e-mail | `_config.yml`, linia `email` |
| Opis strony w Google i przy udostępnianiu | `_config.yml`, linia `description` |
| Projekty | `_data/projekty.yml` (rozdział 2) |
| Strona O mnie | `o-mnie.md` |
| Wpisy na blogu | katalog `_posts` (rozdział 4) |
| Kolory i kroje | `assets/styl.css`, zmienne na samej górze pliku |

W `_config.yml` cudzysłowy muszą zostać. Zmieniasz tylko tekst w środku.

---

## 2. Jak dodać projekt

**Krok 1. Logo i zrzut ekranu.** Wejdź do katalogu `assets/projekty`, kliknij **Add file → Upload files**, przeciągnij pliki i kliknij **Commit changes**. Nazwy plików bez polskich znaków i bez spacji, na przykład `moja-aplikacja.png` i `moja-aplikacja-zrzut.png`. Logo najlepiej kwadratowe.

**Krok 2. Wpis w pliku projektów.** Otwórz `_data/projekty.yml` i kliknij ołówek. Skopiuj cały blok Korektora Lektorskiego, od linii `- nazwa:` do ostatniej linii bloku, wklej go pod spodem i zmień wartości:

| Pole | Co wpisać |
|---|---|
| `nazwa` | nazwa projektu |
| `opis` | jedno zdanie, co robi |
| `url` | pełny adres strony projektu, z `https://` |
| `status` | dokładnie `Live`, `Beta` albo `W budowie` |
| `logo` | ścieżka do logo, np. `/assets/projekty/moja-aplikacja.png` |
| `zrzut` | ścieżka do zrzutu ekranu aplikacji (opcjonalnie) |
| `tlo` | kolor okładki karty, gdy nie ma zrzutu, np. `#080b16` |
| `narzedzia` | lista w nawiasach kwadratowych, np. `["Claude", "Supabase"]` |
| `przychod` | przychód, np. `"1200 zł/mies."` (opcjonalnie) |

**Krok 3.** Kliknij **Commit changes**.

Co dzieje się samo:

- Jeden projekt zajmuje całą szerokość, od dwóch karty układają się po dwie w rzędzie.
- Pasek celu na stronie głównej liczy projekty ze statusem `Live`.
- Kliknięcie karty otwiera stronę projektu w nowej karcie przeglądarki.

**Linie zaczynające się od `#`** są wyłączone (to komentarze). Żeby włączyć na przykład zrzut ekranu albo przychód, usuń `# ` z początku linii. Żeby wyłączyć, dopisz `# ` z powrotem.

**Jak zrobić zrzut aplikacji:** zaloguj się do aplikacji, ustaw ekran, który najlepiej pokazuje, co robi, wciśnij **Win + Shift + S**, zaznacz obszar i zapisz obraz jako PNG. Najlepiej wygląda zrzut w proporcjach szerokiego ekranu.

---

## 3. Zdjęcie profilowe

Wgraj zdjęcie do katalogu `assets`, na przykład jako `zdjecie.jpg`. Najlepiej kwadratowe, co najmniej 300 na 300 pikseli. Potem w `_config.yml` wpisz:

```
zdjecie: "/assets/zdjecie.jpg"
```

Dopóki linia jest pusta (`zdjecie: ""`), na stronie głównej pokazuje się kółko z inicjałami EW.

W pliku `index.html` jest też wyłączony fragment na przychód miesięczny pod nazwiskiem. To edycja kodu, więc gdy będziesz chciał go włączyć, poproś o to Claude Code.

---

## 4. Jak dodać wpis na blog

Wpis to jeden plik. Nie ruszasz nawigacji, strony głównej ani listy wpisów. Wszystko podepnie się samo.

**Krok 1.** Otwórz `SZABLON-WPISU-BLOG.txt` i skopiuj tekst spod linii "KOPIUJ OD TEJ LINII".

**Krok 2.** Kliknij **Add file → Create new file**. W polu nazwy wpisz nazwę razem z katalogiem, na przykład:

```
_posts/2026-10-20-jak-zbudowalem-korektor.md
```

Ukośnik po `_posts` sam utworzy katalog, jeśli go jeszcze nie ma. Zasady nazwy: data w formacie rok, miesiąc, dzień, potem tytuł małymi literami bez polskich znaków i bez spacji, słowa połączone znakiem `-`, na końcu `.md`. Data w nazwie musi się zgadzać z datą w środku pliku.

**Krok 3.** Wklej szablon i zmień treść. W górnej części, między liniami `---`, ustaw:

- `title` tytuł w cudzysłowie
- `date` data w formacie 2026-10-20
- `categories` zostaw `blog`
- `lead` jedno albo dwa zdania streszczenia, pokazują się na liście i w wynikach Google

**Krok 4.** Napisz tekst. Pusta linia oddziela akapity. `## Tekst` robi śródtytuł, `**tekst**` pogrubia, `[słowo](adres)` robi link. Obrazek: wgraj go do `assets/wpisy` i wstaw `![opis obrazka](/assets/wpisy/nazwa-pliku.png)`.

**Krok 5.** Kliknij **Commit changes**.

Po chwili wpis jest na liście na `/blog`, w sekcji "Proces budowy" na stronie głównej (trzy ostatnie wpisy), w mapie strony i w kanale RSS. Na końcu wpisu automatycznie pojawia się formularz zapisu na newsletter. Nagłówek nad formularzem na `/blog` sam zmieni się z "Pierwszy wpis już wkrótce" na "Nie przegap kolejnych wpisów".

---

## 5. Newsletter

Formularz zapisu jest w trzech miejscach: na górze `/blog`, na dole `/o-mnie` i na końcu każdego wpisu. Na stronie głównej jest przycisk, który prowadzi na `/blog`.

**Nie zmieniaj kodu formularza** w `_includes/zapis.html`. To kod z MailerLite i każda zmiana nazw pól może po cichu zepsuć zapisy.

Nagłówek i zdanie nad formularzem zmieniasz w pliku konkretnej strony, w miejscach `tytul="..."` i `opis="..."`: dla bloga w `blog.html`, dla O mnie w `o-mnie.md`.

Dwie rzeczy do ustawienia po stronie MailerLite, nie tutaj:

1. **Double opt-in włączony.** Bez tego nie masz dowodu zgody.
2. **Zgoda marketingowa jako pole w formularzu, domyślnie niezaznaczone.**

Klauzula informacyjna pod formularzem zostaje. Jej usunięcie to decyzja prawna, nie kwestia wyglądu.

Jeśli kiedyś dodasz analitykę, piksel reklamowy albo czat, trzeba zaktualizować politykę prywatności i jej datę. Teraz polityka mówi, że strona nie ma analityki ani plików cookies.

---

## 6. Kiedy coś się popsuje

Jeśli po zatwierdzeniu zmian strona się nie zaktualizowała, wejdź w zakładkę **Actions** w repozytorium. Czerwony znaczek znaczy, że budowanie się nie powiodło. Kliknij w nie, znajdź czerwoną linię z komunikatem błędu i przyślij ten komunikat Claude Code.

Najczęstsze przyczyny:

- w `_data/projekty.yml`: przesunięte wcięcie, brakujący cudzysłów albo dwukropek,
- w górnej części wpisu, między liniami `---`: brakujący cudzysłów w tytule albo zła data.

Poprzednia wersja strony zostaje online, dopóki nowa się nie zbuduje, więc błąd nie wyłączy ci strony.

Jeśli strona wczyta się jako goły tekst bez kolorów i krojów, sprawdź linię `baseurl` w `_config.yml`. Przy własnej domenie musi być pusta: `baseurl: ""`.

---

## 7. Domena i stare adresy

Domena emilwiktorski.pl jest podpięta. Plik `CNAME` w repozytorium utworzył GitHub: nie usuwaj go i nie edytuj. Domenę zmienia się w **Settings → Pages**, w polu **Custom domain**.

Stare adresy `/wydania/` i `/kontakt/` przekierowują na stronę główną.

---

## 8. Pytania do zadania prawnikowi

Nie jestem prawnikiem. Te pytania warto zadać, zanim newsletter zacznie rosnąć:

1. Czy przy działalności nierejestrowanej muszę podać w klauzuli informacyjnej adres do korespondencji, czy wystarczy imię, nazwisko i e-mail?
2. Czy zapis przez formularz z podwójnym potwierdzeniem spełnia wymóg zgody z art. 398 Prawa komunikacji elektronicznej, czy potrzebna jest osobna, odrębnie zaznaczana zgoda marketingowa?
3. Czy przy korzystaniu z MailerLite muszę informować o przekazywaniu danych poza Europejski Obszar Gospodarczy i czy wystarczy do tego umowa powierzenia oferowana przez dostawcę?

---

## 9. Struktura plików

```
_config.yml               ustawienia: opis, bio, LinkedIn, zdjęcie, cel aplikacji
_data/projekty.yml        TU DODAJESZ PROJEKTY
_posts/                   TU DODAJESZ WPISY, jeden plik to jeden wpis
index.html                strona główna
blog.html                 lista wpisów bloga
o-mnie.md                 strona o mnie
polityka-prywatnosci.md   polityka prywatności
404.html                  strona pokazywana przy złym adresie
archiwum.html             przekierowanie starego adresu /wydania/
kontakt.html              przekierowanie starego adresu /kontakt/
robots.txt                instrukcja dla wyszukiwarek
SZABLON-WPISU-BLOG.txt    szablon wpisu na bloga
CLAUDE.md                 stałe instrukcje dla Claude Code
INSTRUKCJA.md             ten plik

_layouts/                 układ stron, nie musisz tu zaglądać
_includes/                powtarzalne kawałki: nagłówek, stopka, formularz zapisu
assets/styl.css           wygląd, kolory i kroje zebrane na samej górze pliku
assets/projekty/          logo i zrzuty ekranu projektów
```

Mapa strony `sitemap.xml` i kanał `rss.xml` powstają automatycznie. Pliki `CLAUDE.md`, `INSTRUKCJA.md` i szablon nie są publikowane na stronie.
