![Coders-Lab-1920px-no-background](https://user-images.githubusercontent.com/30623667/104709394-2cabee80-571f-11eb-9518-ea6a794e558e.png)


### Budowa i analiza obrazu produkcyjnego dla aplikacji Next.JS

#### Cel:
Twoim zadaniem jest zbudowanie obrazu produkcyjnego dla aplikacji Next.JS oraz przeprowadzenie analizy tego obrazu pod kątem bezpieczeństwa. Następnie należy uruchomić ten obraz lokalnie i zweryfikować działanie aplikacji.

#### Instrukcje:

1. **Budowanie obrazu produkcyjnego dla aplikacji Next.JS:**
    - Sklonuj repozytorium z aplikacją Next.JS (z gałęzi basic-fe): [TimeTracker](https://github.com/DevNotes-it/TimeTracker/tree/basic-fe).
    - Przejdź do katalogu projektu.
    - Utwórz odpowiedni Dockerfile do budowy obrazu produkcyjnego. Upewnij się, że Dockerfile zawiera wszystkie niezbędne instrukcje do zbudowania i uruchomienia aplikacji Next.JS w trybie produkcyjnym.
    - Wykonaj polecenie `docker build`, aby zbudować obraz produkcyjny dla aplikacji Next.JS.

2. **Uruchomienie obrazu produkcyjnego lokalnie:**
    - Po zbudowaniu obrazu, wykonaj polecenie `docker run`, aby uruchomić kontener z zbudowanym obrazem.
    - Sprawdź, czy aplikacja Next.JS działa poprawnie, korzystając z lokalnego adresu URL.

3. **Analiza obrazu pod kątem bezpieczeństwa:**
    - Skorzystaj z narzędzi do analizy obrazów Dockerowych, takich jak Trivy lub Docker Scout, aby przeskanować zbudowany obraz pod kątem podatności.
    - Przeanalizuj raport z przeskanowania i zidentyfikuj ewentualne luki w zabezpieczeniach.
    - Wnioskuj, jakie kroki należy podjąć, aby zabezpieczyć obraz.

