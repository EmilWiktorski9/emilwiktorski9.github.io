# Instrukcja obsługi strony

Napisane dla kogoś, kto nie programuje. Nic tu nie trzeba instalować na własnym komputerze.

---

## 1. Co uzupełnić, zanim pokażesz stronę komukolwiek

W kilku miejscach zostawiłem nawiasy kwadratowe. To są dziury do zalepienia. Znajdziesz je tak: na GitHubie wciśnij klawisz `t`, wpisz nazwę pliku, otwórz go i szukaj nawiasu `[`.

| Co | Gdzie |
|---|---|
| `[NAZWA]` nazwa projektu | `_config.yml`, linia `title` |
| `[DOMENA]` twoja domena | `_config.yml` linia `url` oraz `robots.txt` |
| `[EMAIL]` adres kontaktowy | `_config.yml`, linia `email` |
| `[FORMULARZ_MAILERLITE]` | `_includes/zapis.html` |
| `[ADRES DO KORESPONDENCJI]`, `[DATA]` i pozostałe | `polityka-prywatnosci.md` |

Strona zadziała także z niewypełnionymi nawiasami. Po prostu będzie w nich pisało `[NAZWA]`.

---

## 2. Postawienie strony na GitHub Pages

**Krok 1.** Wejdź na github.com i utwórz nowe repozytorium (przycisk **New**). Nazwa może być dowolna, na przykład `strona`. Wybierz **Public**. Publiczne jest konieczne, jeśli masz darmowe konto.

**Krok 2.** Wgraj pliki. Na stronie pustego repozytorium kliknij **uploading an existing file**. Rozpakuj u siebie archiwum, zaznacz **całą zawartość** rozpakowanego katalogu (nie sam katalog, tylko to, co jest w środku) i przeciągnij do przeglądarki.

Ważne: musi się wgrać też katalog `_posts` i pozostałe zaczynające się od podkreślnika. Jeśli przeciąganie ich pomija, wgraj je osobno.

Na dole strony kliknij zielony **Commit changes**.

**Krok 3.** W repozytorium wejdź w **Settings**, potem w menu po lewej w **Pages**.

W sekcji **Build and deployment**, pole **Source**, wybierz **Deploy from a branch**. Poniżej wybierz gałąź `main` i katalog `/ (root)`. Kliknij **Save**.

**Krok 4.** Poczekaj dwie, trzy minuty. Zakładka **Actions** w repozytorium pokaże, czy budowanie się udało. Zielony znaczek znaczy, że tak. Wróć do **Settings → Pages**, będzie tam adres w rodzaju `https://twojanazwa.github.io/strona/`. To jest twoja działająca strona.

Od tej pory każda zmiana pliku na GitHubie i kliknięcie **Commit changes** automatycznie przebudowuje stronę. Nie ma nic więcej do robienia.

---

## 3. Podpięcie własnej domeny

Rób w tej kolejności, bo odwrotna kolejność jest niebezpieczna: gdybyś ustawił DNS przed dodaniem domeny na GitHubie, ktoś inny mógłby przejąć twój adres.

**Krok 1. Najpierw GitHub.** Settings → Pages → pole **Custom domain**. Wpisz domenę bez `https://` i bez `www`, czyli na przykład `twojadomena.pl`. Kliknij **Save**.

GitHub sam utworzy w repozytorium plik o nazwie `CNAME` z twoją domeną w środku. Nie twórz go ręcznie i nie kasuj. Jeśli kiedyś zmienisz domenę, zmień ją w tym samym polu w ustawieniach, a nie w pliku.

**Krok 2. Potem DNS u rejestratora domeny.** Wejdź w panel firmy, w której kupiłeś domenę, i znajdź zarządzanie DNS. Dodaj pięć wpisów:

Cztery rekordy typu **A**, nazwa `@` (czasem pole nazwy zostawia się puste), wartości kolejno:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

Jeden rekord typu **CNAME**, nazwa `www`, wartość `twojanazwauzytkownika.github.io` (twoja nazwa użytkownika na GitHubie, z kropką na końcu, jeśli panel jej wymaga).

Jeśli rejestrator dodał własne domyślne rekordy A wskazujące gdzie indziej, usuń je.

**Krok 3.** Poczekaj. Zwykle kilkanaście minut, czasem do doby. Potem wróć do **Settings → Pages** i zaznacz **Enforce HTTPS**. Ta opcja bywa niedostępna przez pierwszą godzinę, bo GitHub musi najpierw wystawić certyfikat. To normalne.

**Krok 4.** Wpisz nową domenę w `_config.yml` w linii `url` oraz w pliku `robots.txt`. Bez tego adresy w mapie strony i w danych dla Google będą wskazywać na `[DOMENA]`.

---

## 4. Jak dodać nowy wpis

Wpis to jeden plik. Nie ruszasz nawigacji, strony głównej ani list. Wszystko podepnie się samo.

**Krok 1.** Otwórz plik `SZABLON-WPISU.txt` i skopiuj tekst spod linii.

**Krok 2.** W repozytorium wejdź do katalogu `_posts`. Kliknij **Add file → Create new file**.

**Krok 3.** W polu nazwy wpisz nazwę pliku w tym formacie:

```
2026-09-15-wydanie-02.md
```

Zasady nazwy: rok, myślnik, miesiąc dwucyfrowo, myślnik, dzień dwucyfrowo, myślnik, tytuł małymi literami bez polskich znaków i bez spacji, na końcu `.md`. Data w nazwie musi się zgadzać z datą w środku pliku.

**Krok 4.** Wklej szablon i zmień treść. W górnej części, między liniami `---`, ustaw:

- `title` tytuł w cudzysłowie
- `date` data w formacie 2026-09-15
- `categories` wpisz `wydania` albo `blog`, to decyduje, na której liście wpis się pojawi
- `lead` jedno zdanie streszczenia, pokazuje się na liście i w wynikach Google

**Krok 5.** Napisz tekst. Zwykłym pismem, pusta linia oddziela akapity. `## Tekst` robi śródtytuł, `**tekst**` pogrubia, `[słowo](adres)` robi link.

**Krok 6.** Na dole kliknij **Commit changes**. Po dwóch minutach wpis jest na stronie, w odpowiedniej liście, w mapie strony i w kanale RSS.

### Blok pojedynczej oferty

W wydaniach każdą ofertę opakowujesz w gotowy blok, który znajdziesz na końcu `SZABLON-WPISU.txt`. Zmieniasz w nim numer, tytuł, trzy liczby i trzy akapity. Reszta zrobi się sama.

Uwaga na jeden szczegół: w linii `<div class="oferta" markdown="1">` fragment `markdown="1"` musi zostać. Bez niego pogrubienia i śródtytuły w środku bloku przestaną działać.

---

## 5. Aktualizacja paska liczników

Pasek pod nazwą strony pokazuje numer wydania, datę i twoje liczby. To jest wyróżnik tej strony, więc powinien być prawdziwy.

Zmieniasz go w `_config.yml`, w sekcji `licznik`. Cztery linie, raz w tygodniu, przy okazji publikacji wydania. Tam też jest linia `naglowek_glowny` ze zdaniem otwierającym stronę główną.

---

## 6. Wklejenie formularza z MailerLite

W MailerLite utwórz formularz osadzany (embedded form) i skopiuj kod HTML. Otwórz `_includes/zapis.html` i zastąp linię `[FORMULARZ_MAILERLITE]` wklejonym kodem.

Dwie rzeczy do ustawienia po stronie MailerLite, nie tutaj:

1. **Double opt in włączony.** Bez tego nie masz dowodu zgody.
2. **Zgoda marketingowa jako pole w formularzu, domyślnie niezaznaczone.** MailerLite ma to jako gotową opcję.

Pod formularzem zostawiłem krótką klauzulę informacyjną. Jeśli MailerLite doda własny checkbox ze zgodą, nie dokładaj drugiego, bo dwie zgody obok siebie wyglądają na błąd i zniechęcają do zapisu.

---

## 7. Kiedy coś się popsuje

Jeśli po zatwierdzeniu zmian strona się nie zaktualizowała, wejdź w zakładkę **Actions** w repozytorium. Czerwony znaczek znaczy, że budowanie się nie powiodło. Kliknij w nie, znajdź czerwoną linię z komunikatem błędu i przyślij mi ten komunikat.

Najczęstsza przyczyna: literówka w górnej części pliku wpisu, między liniami `---`. Zwykle brakujący cudzysłów w tytule albo zła data.

Poprzednia wersja strony zostaje online, dopóki nowa się nie zbuduje, więc zepsuty wpis nie wyłączy ci strony.

---

## 8. Pytania do zadania prawnikowi

Nie jestem prawnikiem i polityka prywatności w tym repozytorium to szkielet, a nie gotowy dokument. Zanim uruchomisz zapis na newsletter, warto zadać te pytania:

1. Czy przy działalności nierejestrowanej muszę podać w klauzuli informacyjnej adres do korespondencji, czy wystarczy imię, nazwisko i e-mail?
2. Czy zapis przez formularz z podwójnym potwierdzeniem spełnia wymóg zgody z art. 398 Prawa komunikacji elektronicznej, czy potrzebna jest osobna, odrębnie zaznaczana zgoda marketingowa?
3. Czy przy korzystaniu z MailerLite muszę informować o przekazywaniu danych poza Europejski Obszar Gospodarczy i czy wystarczy do tego umowa powierzenia oferowana przez dostawcę?
4. Od którego momentu opisywanie cudzych ofert w newsletterze wymaga rejestracji działalności, jeśli nie pobieram za to żadnych opłat?
5. Czy publikowanie moich ocen konkretnych, publicznie wystawionych ofert rodzi ryzyko po stronie prawa prasowego albo ochrony dóbr osobistych sprzedających, i jak to ryzyko ograniczyć.

---

## 9. Struktura plików

```
_config.yml               ustawienia całej strony, tu zmieniasz nazwę, domenę, liczniki
index.html                strona główna
blog.html                 lista wpisów bloga
archiwum.html             lista wydań newslettera
o-mnie.md                 strona o mnie
polityka-prywatnosci.md   szkielet polityki, do uzupełnienia
404.html                  strona pokazywana przy złym adresie
robots.txt                instrukcja dla wyszukiwarek
SZABLON-WPISU.txt         szablon do kopiowania przy nowym wpisie

_posts/                   TU DODAJESZ WPISY, jeden plik to jeden wpis
_layouts/                 układ stron, nie musisz tu zaglądać
_includes/                powtarzalne kawałki: nagłówek, stopka, blok zapisu
assets/styl.css           wygląd, kolory zebrane na samej górze pliku
```

Mapa strony `sitemap.xml` i kanał `rss.xml` powstają automatycznie. Nie ma ich w repozytorium i nie trzeba ich tworzyć.
