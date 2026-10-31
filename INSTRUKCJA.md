# Instrukcja obsługi strony

Napisane dla kogoś, kto nie programuje. Nic nie trzeba instalować na komputerze.

Każdą zmianę robisz na github.com w repozytorium strony: otwierasz plik, klikasz ikonę ołówka (**Edit**), zmieniasz tekst i na dole klikasz zielony **Commit changes**. Po jednej, dwóch minutach zmiana jest na emilwiktorski.pl.

Strona to jedna podstrona, wizytówka: start, "Co zrobiłem", "Co mogę dla Ciebie zrobić" i kontakt.

---

## 1. Co gdzie zmieniasz

| Co | Gdzie |
|---|---|
| Duży nagłówek na górze | `_config.yml`, linia `naglowek` |
| Tekst o tobie pod nagłówkiem | `_config.yml`, linia `wstep` |
| Opis strony w Google i przy udostępnianiu linku | `_config.yml`, linia `description` |
| Nagłówek i tekst w sekcji kontaktu | `_config.yml`, linie `kontakt_tytul` i `kontakt_opis` |
| Adres e-mail | `_config.yml`, linia `email` |
| LinkedIn i Facebook | `_config.yml`, linie `linkedin` i `facebook` |
| Formularz kontaktowy | `_config.yml`, linia `formspree` (rozdział 3) |
| Projekty w "Co zrobiłem" | `_data/projekty.yml` (rozdział 2) |
| Kafle w "Co mogę dla Ciebie zrobić" | `_data/oferta.yml` |
| Kolory i kroje | `assets/styl.css`, zmienne na samej górze pliku |

W plikach `.yml` cudzysłowy muszą zostać. Zmieniasz tylko tekst w środku.

**Facebook:** wklej pełny adres profilu w linii `facebook`, np. `facebook: "https://www.facebook.com/twoj.profil"`. Dopóki linia jest pusta, ikona Facebooka się nie pokazuje.

---

## 2. Jak dodać projekt

**Krok 1. Logo.** Wejdź do katalogu `assets/projekty`, kliknij **Add file → Upload files**, przeciągnij plik i kliknij **Commit changes**. Nazwa pliku bez polskich znaków i spacji, np. `moja-aplikacja.png`. Logo najlepiej kwadratowe.

**Krok 2. Wpis w pliku projektów.** Otwórz `_data/projekty.yml` i kliknij ołówek. Skopiuj cały blok Korektora Lektorskiego, od linii `- nazwa:` do ostatniej linii bloku, wklej pod spodem i zmień wartości:

| Pole | Co wpisać |
|---|---|
| `nazwa` | nazwa projektu |
| `opis` | dwa, trzy zdania: dla kogo i co robi |
| `url` | pełny adres strony projektu, z `https://` |
| `status` | dokładnie `Live`, `Beta` albo `W budowie` (`Live` wyświetla się jako "Działa") |
| `logo` | ścieżka do logo, np. `/assets/projekty/moja-aplikacja.png` |
| `tlo` | kolor tła pod logo, np. `#080b16` |
| `start` | kiedy projekt powstał, np. `"kwiecień 2026"` |
| `dla_kogo` | krótko, dla kogo jest, np. `"studia i wydawnictwa"` |
| `przychod` | przychód, np. `"1200 zł/mies."` (opcjonalnie) |

Pola `zarabia`, `zrzut` i `narzedzia` mogą zostać, na obecnej stronie się nie wyświetlają.

**Krok 3.** Kliknij **Commit changes**.

Jeden projekt zajmuje całą szerokość, od dwóch karty układają się po dwie w rzędzie.

**Linie zaczynające się od `#`** są wyłączone (to komentarze). Żeby włączyć np. przychód, usuń `# ` z początku linii.

---

## 3. Formularz kontaktowy (Formspree)

Dopóki linia `formspree` jest pusta, w sekcji kontaktu zamiast formularza jest przycisk z adresem e-mail. Żeby włączyć formularz:

1. Załóż darmowe konto na formspree.io, zaloguj się adresem emil@emilwiktorski.pl.
2. Kliknij **New Form**, nazwij go np. "Strona emilwiktorski.pl".
3. Skopiuj adres formularza. Wygląda tak: `https://formspree.io/f/xyzabcde`. Potrzebujesz tylko końcówki po `/f/`, czyli `xyzabcde`.
4. W `_config.yml` wpisz ją w linii `formspree`, np. `formspree: "xyzabcde"`.
5. W tej samej sekcji zmień `polityka_aktualizacja` na dzisiejszą datę.
6. Kliknij **Commit changes**, poczekaj dwie minuty i wyślij próbną wiadomość ze strony. Pierwszą wiadomość Formspree może poprosić o potwierdzenie w mailu.

Polityka prywatności sama dopisze wtedy sekcję o formularzu.

---

## 4. Blog i newsletter

Na razie są wyłączone. Stare adresy `/blog/` i `/o-mnie/` przekierowują na stronę główną. Kod formularza MailerLite został w `_includes/zapis.html`, żeby dało się go kiedyś włączyć. Nie zmieniaj go, każda zmiana nazw pól może po cichu zepsuć zapisy.
