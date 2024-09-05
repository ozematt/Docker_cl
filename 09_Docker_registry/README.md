![Coders-Lab-1920px-no-background](https://user-images.githubusercontent.com/30623667/104709394-2cabee80-571f-11eb-9518-ea6a794e558e.png)


# Budowanie i zarządzanie prostym obrazem Dockerowym

## Cel zadania:
Celem tego zadania jest zbudowanie prostego obrazu Dockerowego, który po uruchomieniu wypisze w konsoli "Hello Docker", zalogowanie się do rejestru Dockerowego GitHub-a, wypchnięcie obrazu do rejestru oraz pobranie go z powrotem.

## Kroki do wykonania:

1. **Utworzenie repozytorium publicznego na Githubie:**
    - Przejdź do swojego konta na GitHubie.
    - Utwórz nowe repozytorium, nadając mu nazwę i opis.
    - Ustaw repozytorium jako publiczne - dzięi temu uzyskasz bezpłatną przestrzeń w rejestrze - zapoznaj sie z https://github.com/pricing.

2. **Utworzenie pliku Dockerfile:**
    - W lokalnym katalogu projektu utwórz plik o nazwie `Dockerfile`.
    - W pliku `Dockerfile` zdefiniuj instrukcje potrzebne do zbudowania obrazu, który po uruchomieniu wypisze "Hello Docker" w konsoli.

3. **Zbudowanie obrazu lokalnie:**
    - W terminalu, w lokalnym katalogu projektu, użyj polecenia `docker build` do zbudowania obrazu na podstawie pliku `Dockerfile`.

4. **Zalogowanie się do rejestru Dockerowego Github-a w CLI:**
    - Uruchom terminal i zaloguj się do rejestru Dockerowego GitHub-a przy użyciu odpowiednich poleceń CLI

5. **Otagowanie obrazu:**
    - Użyj polecenia `docker tag` do otagowania zbudowanego obrazu.

6. **Wypchnięcie obrazu do rejestru Dockerowego Github-a dla wcześniej utworzonego repozytorium:**
    - W terminalu, użyj polecenia `docker push`, aby wypchnąć otagowany obraz do rejestru Dockerowego GitHub-a.

7. **Usunięcie obrazu lokalnego:**
    - Po wypchnięciu obrazu, użyj polecenia `docker rmi <nazwa_obrazu>`, aby usunąć lokalną kopię obrazu.

8. **Pobranie obrazu z rejestru Dockerowego Github-a:**
    - Zaloguj się do GitHuba i przejdź do repozytorium, w którym został wypchnięty obraz.
    - Skopiuj adres obrazu i użyj polecenia `docker pull`, aby pobrać ten obraz na swoją maszynę lokalną.

9. **Dopisz plik Readme.md:**
    - W repozytorium dodaj plik `Readme.md` z krótkim opisem projektu.

## Zalecenia:
- Upewnij się, że plik `Dockerfile` zawiera odpowiednie instrukcje do wydrukowania "Hello Docker" po uruchomieniu kontenera.
- Starannie zastanów się nad nazwami repozytorium i obrazu, aby były zrozumiałe.
- Upewnij się, że masz zainstalowane narzędzia Docker CLI i jesteś zalogowany do swojego konta GitHub.

Powodzenia!