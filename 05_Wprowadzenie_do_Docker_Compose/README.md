![Coders-Lab-1920px-no-background](https://user-images.githubusercontent.com/30623667/104709394-2cabee80-571f-11eb-9518-ea6a794e558e.png)


# Pierwsze kroki z Docker Compose i PostgreSQL

Po obejrzeniu prezentacji na temat Docker Compose, nadszedł czas, aby praktycznie zastosować zdobytą wiedzę. W tym zadaniu przygotujecie własny plik `docker-compose.yml`, który pozwoli na uruchomienie prostej aplikacji wielokontenerowej z serwerem Nginx i bazą danych PostgreSQL. Skoncentrujemy się na wykorzystaniu Docker Compose do zarządzania aplikacjami, zwracając szczególną uwagę na użycie zmiennych środowiskowych w konfiguracji usług oraz na łączenie się z bazą danych PostgreSQL, aby zweryfikować jej działanie.

#### Krok 1: Przygotowanie katalogu projektu

Na swoim komputerze utwórz katalog, który będzie zawierał wszystkie pliki potrzebne do wykonania tego zadania:

```bash
mkdir moj-projekt-compose
cd moj-projekt-compose
```

#### Krok 2: Tworzenie pliku `docker-compose.yml`

W katalogu projektu, utwórz plik o nazwie `docker-compose.yml`, gdzie zdefiniujesz konfigurację usług, które chcesz uruchomić za pomocą Docker Compose:

```yaml
version: '3.8'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  db:
    image: postgres
    environment:
      POSTGRES_PASSWORD: mojeHaslo
```

W tym przykładzie definiujemy dwie usługi: `web` (serwer Nginx) i `db` (baza danych PostgreSQL) z użyciem zmiennej środowiskowej `POSTGRES_PASSWORD` dla ustawienia hasła dla bazy danych.

#### Krok 3: Uruchomienie aplikacji

Uruchom aplikację za pomocą polecenia Docker Compose:

```bash
docker-compose up
```

To polecenie uruchomi wszystkie usługi zdefiniowane w pliku `docker-compose.yml`, tworząc sieć, w której będą mogły komunikować się między sobą.

#### Krok 4: Łączenie się z bazą danych PostgreSQL

Po uruchomieniu usług, połącz się z bazą danych PostgreSQL, aby zweryfikować jej działanie:

```bash
docker-compose exec db psql -U postgres
```

W tym momencie możesz wykonać kilka prostych operacji SQL, na przykład utworzyć nową bazę danych, tabelę i wstawić do niej dane:

```sql
CREATE DATABASE moja_testowa_baza;
\c moja_testowa_baza
CREATE TABLE moja_tabela (id SERIAL PRIMARY KEY, nazwa VARCHAR(50));
INSERT INTO moja_tabela (nazwa) VALUES ('Testowa wartość');
SELECT * FROM moja_tabela;
```

Po zakończeniu pracy z bazą danych, możesz wyjść z narzędzia `psql`:

```sql
\q
```


#### Krok 5: Persystencja danych

Aby zachować dane bazy PostgreSQL po zatrzymaniu i ponownym uruchomieniu kontenera, możemy skorzystać z volumenów. Zmodyfikuj plik `docker-compose.yml`, aby dodać volumen dla bazy danych.

#### Podsumowanie

Dzięki wykonaniu tego zadania, udało Wam się skonfigurować i uruchomić prostą aplikację wielokontenerową za pomocą Docker Compose, a także połączyć się z bazą danych PostgreSQL i wykonać na niej podstawowe operacje SQL. To zadanie pozwoliło na praktyczne zastosowanie wiedzy na temat Docker Compose, a także na zrozumienie roli i zalet używania Docker Compose w procesie deweloperskim.

Eksperymentuj dalej z Docker Compose i PostgreSQL, aby jeszcze lepiej zrozumieć ich możliwości i jak mogą one wspierać rozwój Twoich projektów aplikacji.