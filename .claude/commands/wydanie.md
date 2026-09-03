Tworzysz nowy plik wydania newslettera na podstawie surowego tekstu, który
podał Emil.

Surowy tekst: $ARGUMENTS

Jeśli nic nie podał po nazwie komendy, poproś go o wklejenie treści i zatrzymaj się.

Kroki:

1. Przeczytaj `SZABLON-WYDANIA.txt` i trzymaj się tego układu co do znaku.
2. Ustal numer wydania: sprawdź `_posts`, weź najwyższy dotychczasowy numer
   z kategorii `wydania` i dodaj jeden.
3. Utwórz plik `_posts/RRRR-MM-DD-wydanie-NN.md` z dzisiejszą datą.
4. Złóż wydanie w czterech częściach: wstęp z liczbą przejrzanych ogłoszeń,
   tabela wszystkich ofert, trzy oferty rozpisane pełnym schematem,
   sekcja "czego nie było".
5. Policz mnożniki sam i sprawdź arytmetykę. Jeśli cena podzielona przez zysk
   nie zgadza się z mnożnikiem podanym przez Emila, zatrzymaj się i zapytaj.
6. Zaktualizuj sekcję `licznik` w `_config.yml`: numer wydania, datę,
   liczbę przejrzanych i opisanych ogłoszeń.

Twarde zasady:

- Nie pisz werdyktów za Emila. Opinie, oceny i wnioski przepisujesz z jego
  tekstu, poprawiając wyłącznie składnię i czytelność. Nie dodawaj zastrzeżeń,
  nie łagodź krytyki, nie dopisuj ostrożnych sformułowań.
- Jeśli w jego tekście brakuje któregoś pola karty weryfikacji, wpisz
  `*brak danych*` i wypisz na końcu listę braków. Nie zgaduj i nie dopisuj.
- Zakaz myślnika i pauzy w treści.
- Liczba z ogłoszenia to "zysk deklarowany", cena to "cena wywoławcza".
- Zachowaj stałą kolejność dziewięciu pozycji w karcie weryfikacji.

Na koniec pokaż mu listę braków i zaproponuj commit. Nie wypychaj na GitHub
bez zgody.
