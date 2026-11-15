# Instrukcja obsługi strony

Napisane dla kogoś, kto nie programuje. Nic nie trzeba instalować na komputerze.

Każdą zmianę robisz na github.com w repozytorium strony: otwierasz plik, klikasz ikonę ołówka (**Edit**), zmieniasz tekst i na dole klikasz zielony **Commit changes**. Po jednej, dwóch minutach zmiana jest na emilwiktorski.pl.

Strona to jedna krótka podstrona: start, „Co robię” (strony premium, aplikacje, automatyzacje), „Jak pracuję” i kontakt. Kroje pisma są w `assets/fonty`, strona nie korzysta z Google Fonts.

---

## 1. Co gdzie zmieniasz

| Co | Gdzie |
|---|---|
| Duży nagłówek na górze | `_config.yml`, linie `naglowek_przed`, `naglowek_wyroznienie` (słowo kursywą z kreską), `naglowek_po` |
| Tekst pod nagłówkiem | `_config.yml`, linia `wstep` |
| Opis strony w Google i przy udostępnianiu linku | `_config.yml`, linia `description` |
| Obrazek przy udostępnianiu linku | `assets/og.jpg` (1200 x 630) |
| Nagłówek i tekst w sekcji kontaktu | `_config.yml`, linie `kontakt_tytul` i `kontakt_opis` |
| Adres e-mail, LinkedIn, Facebook | `_config.yml`, linie `email`, `linkedin`, `facebook` |
| Formularz kontaktowy | `_config.yml`, linia `formspree` (rozdział 3) |
| „Co robię”: trzy wiersze i linki do moich aplikacji | `_data/oferta.yml` |
| Realizacje (na razie wyłączone) | `_data/strony.yml` |
| Jak pracuję | `_data/kroki.yml` |
| Kolory | `assets/styl.css`, zmienne na górze pliku (`--akcent` to niebieska kursywa) |

W plikach `.yml` cudzysłowy muszą zostać. Zmieniasz tylko tekst w środku.

**Realizacje:** gdy w `_data/strony.yml` dopiszesz stronę klienta (wzór jest w pliku), pod nagłówkiem pojawi się kolaż, a niżej sekcja „Realizacje”. Pusty plik = nic się nie pokazuje.

Plik `_data/projekty.yml` zostaje na później, na stronie głównej się teraz nie wyświetla.

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
