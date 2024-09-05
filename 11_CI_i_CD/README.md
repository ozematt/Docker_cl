![Coders-Lab-1920px-no-background](https://user-images.githubusercontent.com/30623667/104709394-2cabee80-571f-11eb-9518-ea6a794e558e.png)


#### Cel zadania:

Cześć! Przed Wami praktyczne zadanie, które pozwoli Wam przećwiczyć konfigurację procesu CI/CD dla poznanej wcześniej aplikacji TaskTracker napianej z wykorzystaniem Next.JS.
Wykorzystajcie swoją wiedzę zdobytą z materiałów szkoleniowych i poprzednich doświadczeń, aby skonfigurować workflow, który automatyzuje procesy związane z budowowaniem i skanowaniem kodu jak i obrazu Dockerowego.

#### Krok 1: Fork repozytorium z aplikacją Next.JS

Waszym pierwszym zadaniem jest wykonanie forka repozytorium z aplikacją TimeTracker (https://github.com/DevNotes-it/TimeTracker/tree/basic-fe). Po wykonaniu forka, sklonujcie repozytorium na swój lokalny komputer i przełączcie się na gałąź `basic-fe` aby móc pracować nad konfiguracją pipeline.

#### Krok 2: Konfiguracja pipeline dla Waszej aplikacji Next.JS

Bazując na Waszej dotychczasowej wiedzy oraz przeczytanych materiałach, stwórzcie plik YAML z konfiguracją, który będzie zawierał kolejne kroki procesu CI/CD dla Waszego projektu
- Budowanie obrazu Dockerowego
- Wypychniecie obrazu do GitHub Container Registry
  Workflow ma się uruchamiać gdy będziecie robić Pull Request do gałęzi `develop` lub `main` (nie zapomnijcie utworzyć takich gałęzi)


#### Krok 3: Uruchomienie pipeline

Wyphchnijcie swoje zmiany i utwórzcie PR, sprawdzcie czy Workflow się uruchomił.
Obserwujcie proces i przeanalizujcie wyniki - to świetna okazja, aby zobaczyć, jak działa proces CI/CD w praktyce.

#### Krok 4: Dodatkowe zadanie

Zaawansowane zadanie!
Dodajcie następujące zadania w CI/CD:
- skanowanie zbudowanego w pricesie CI/CD obrazu Dockerowego pod kątem bezpieczeństwa
- skanowanie kodu aplikacji pod kątem bezpieczeństwa

Do obu zadań wykorzystajcie narzędzie Trivy - zapoznajcie się z jego możliwościami: https://github.com/aquasecurity/trivy-action

#### Podsumowanie:

Po wykonaniu wszystkich kroków będzie skonfigurowany pipeline CI/CD dla aplikacji. To doskonała okazja do poeksperymentowania dalej z budowaniem CI/CD, możecie np. dopisać testy i dodać ich uruchamianie jako kolejne zadanie.
Oczywiście najlepiej jakbyście teraz poeksperymentowali z budowaniem obrazu Dockerowego jak i CI/CD dla Waszej własnej aplikacji, do czego gorąco zachęcamy :)
