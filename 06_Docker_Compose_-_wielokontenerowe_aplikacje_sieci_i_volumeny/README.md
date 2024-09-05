![Coders-Lab-1920px-no-background](https://user-images.githubusercontent.com/30623667/104709394-2cabee80-571f-11eb-9518-ea6a794e558e.png)


# Konfiguracja prostego stacku aplikacji z Nginx i bazą danych

W tym zadaniu skupimy się na stworzeniu prostej konfiguracji z wykorzystaniem Docker Compose, która obejmuje serwer Nginx oraz bazę danych. Nginx będzie dostępny w sieci publicznej i wewnętrznej (FrontEnd i BackEnd), podczas gdy baza danych będzie dostępna tylko w sieci wewnętrznej (BackEnd). Ponadto przećwiczycie również jak używać volumenów do przechowywania danych bazy oraz jak weryfikować możliwość komunikacji między Nginx a bazą danych.

#### Krok 1: Tworzenie pliku `docker-compose.yml`

W wybranym katalogu projektu utwórz plik `docker-compose.yml` i wklej poniższą konfigurację:

```yaml
version: '3.8'
services:
  nginx:
    image: nginx:latest
    ports:
      - "8080:80"
    networks:
      - FrontEnd
      - BackEnd
  db:
    image: postgres:latest
    environment:
      POSTGRES_PASSWORD: mojeHaslo
    volumes:
      - db-data:/var/lib/postgresql/data
    networks:
      - BackEnd

volumes:
  db-data:

networks:
  FrontEnd:
  BackEnd:
```

#### Krok 2: Uruchomienie stacku aplikacji

W terminalu, będąc w katalogu z plikiem `docker-compose.yml`, uruchom swoje usługi:

```bash
docker-compose up -d
```

#### Krok 3: Weryfikacja działania Nginx

Aby sprawdzić, czy Nginx jest dostępny z zewnątrz, otwórz przeglądarkę i przejdź do `http://localhost:8080`. Powinieneś zobaczyć domyślną stronę powitalną Nginx.

#### Krok 4: Testowanie komunikacji między Nginx a bazą danych

Komunikacja pomiędzy Nginx a bazą danych wymaga pewnych dodatkowych konfiguracji w aplikacji lub skryptów, które wykorzystują bazę danych, jednak możemy zweryfikować, czy obie usługi mogą "widzieć" się nawzajem za pomocą prostego testu:

1. Zaloguj się do kontenera Nginx:

```bash
docker-compose exec nginx /bin/bash
```

2. Zainstaluj narzędzie `curl` (może wymagać uruchomienia `apt-get update` przed instalacją):

```bash
apt-get update && apt-get install curl
```

3. Użyj `curl` do zrobienia zapytania do bazy danych. Ponieważ Nginx domyślnie nie będzie miał dostępu do PostgreSQL przez HTTP, możemy tylko sprawdzić, czy sieć pozwala na nawiązanie połączenia:

```bash
curl db:5432
```

Otrzymasz informację, że połączenie zostało zainicjowane, ale nie udało się je utrzymać (co jest oczekiwanym wynikiem, gdyż próbujemy połączyć się z bazą danych za pomocą protokołu HTTP).

#### Krok 5: Czyszczenie po zadaniu

Po zakończeniu eksperymentów nie zapomnij zatrzymać i usunąć kontenerów oraz sieci utworzonych przez Docker Compose:

```bash
docker-compose down
```

To zadanie dało Wam wgląd w to, jak można konfigurować prostą aplikację wielokontenerową z wykorzystaniem Docker Compose, tworzyć sieci i volumeny, a także jak testować komunikację między różnymi usługami. Zachęcam do eksperymentowania z różnymi konfiguracjami, aby jeszcze lepiej zrozumieć możliwości Docker Compose.

# Aplikacja Wordpress z bazą danych MySQL

W tym ćwiczeniu musicie uruchomić aplikację Wordpress z bazą danych MySQL za pomocą Docker Compose.
Tym razem musicie się posłużyć dokumentacją aby znaleźć odpowiednie obrazy i zmienne środowiskowe.

https://github.com/docker/awesome-compose/blob/master/official-documentation-samples/wordpress/README.md


## Zadania
- Uruchom aplikację Wordpress z bazą danych MySQL za pomocą Docker Compose.
- Sprawdź czy aplikacja działa poprawnie w przeglądarce.
- Zatrzymaj aplikację i upewnij się, że dane nie zostały utracone.
- Usuń aplikację i upewnij się, że nie ma żadnych pozostałości po niej.
- Przeczytaj dokumentację obrazów i zrozum, jakie zmienne środowiskowe są używane w pliku `docker-compose.yml`.
- Spróbuj zmodyfikować plik `docker-compose.yml` tak, aby aplikacja działała na innych portach.
- Spróbuj zmodyfikować plik `docker-compose.yml` tak, aby aplikacja korzystała z innych wersji obrazów.
