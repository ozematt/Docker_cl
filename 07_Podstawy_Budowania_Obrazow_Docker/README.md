![Coders-Lab-1920px-no-background](https://user-images.githubusercontent.com/30623667/104709394-2cabee80-571f-11eb-9518-ea6a794e558e.png)


# Tworzenie prostego Dockerfile

#### Cel zadania:
Stworzenie własnego Dockerfile dla prostej aplikacji webowej, np. serwującej statyczną stronę HTML.

#### Krok po kroku:
1. **Przygotuj katalog projektu:**
    - Utwórz nowy katalog na swoim komputerze, np. `moja-aplikacja-webowa`.
    - Wewnątrz katalogu, stwórz plik `index.html` zawierający kod HTML Twojej strony.

2. **Stwórz Dockerfile:**
    - W tym samym katalogu, utwórz plik o nazwie `Dockerfile` bez rozszerzenia.
    - Wprowadź następującą zawartość do Dockerfile:
      ```
      FROM nginx:alpine
      COPY ./index.html /usr/share/nginx/html/index.html
      CMD ["nginx", "-g", "daemon off;"]
      ```
    - Ten Dockerfile używa obrazu `nginx:alpine` jako bazy, kopiuje Twój plik `index.html` do odpowiedniego katalogu w kontenerze i uruchamia serwer Nginx.

3. **Zbuduj obraz Docker:**
    - Otwórz terminal i przejdź do katalogu projektu.
    - Uruchom polecenie budujące obraz:
      ```
      docker build -t moja-aplikacja-webowa .
      ```
    - Tag `-t moja-aplikacja-webowa` nadaje nazwę Twojemu obrazowi.

4. **Uruchom kontener:**
    - Po zbudowaniu obrazu, uruchom kontener:
      ```
      docker run -d -p 8080:80 moja-aplikacja-webowa
      ```
    - To polecenie uruchamia kontener w tle, mapując port 8080 na hoście do portu 80 w kontenerze.

5. **Sprawdź działanie aplikacji:**
    - Otwórz przeglądarkę i przejdź do `http://localhost:8080`. Powinieneś zobaczyć swoją statyczną stronę HTML.



# Budowanie obrazu Dockerowego z narzędziami diagnostycznymi i Docker Compose


Celem tego zadania jest stworzenie własnego obrazu Dockerowego, który będzie diagnozował wybrany adres www.
Adres ten powinien być przekazywany przez zmienną środowiskową.
Następnie, dane z nslookup i whois powinny być zapisane do pliku /report/<nazwa_domeny>.txt.
Dodatkowo, przygotuj plik docker-compose.yml, który pozwoli na uruchomienie tego obrazu i zapisanie raportów na hoście.

## Krok 1: Stworzenie pliku Dockerfile
Stwórz plik Dockerfile w wybranym przez siebie katalogu. W tym pliku, będziesz definiować, jak Docker ma zbudować Twój obraz.

- **FROM**: Na początek, użyj instrukcji FROM aby określić obraz bazowy. W tym przypadku, użyj obrazu debian:latest.

- **WORKDIR**: Użyj instrukcji WORKDIR aby ustawić katalog roboczy w kontenerze. Możesz ustawić go na /root.

- **RUN**: Użyj instrukcji RUN aby zainstalować narzędzia nslookup i whois. Możesz to zrobić za pomocą polecenia apt-get update && apt-get install -y dnsutils whois.

- **ENV**: Użyj instrukcji ENV aby zdefiniować zmienną środowiskową, która będzie przechowywać adres do diagnozy. Możesz nazwać ją TARGET.

- **CMD**: Na koniec, użyj instrukcji CMD aby określić, jaką komendę Docker ma uruchomić, gdy kontener zostanie uruchomiony. W tym przypadku, powinno to być `sh -c 'mkdir -p /report && nslookup $TARGET > /report/$TARGET.txt && whois $TARGET >> /report/$TARGET.txt'`.

## Krok 2: Budowanie obrazu
Teraz, użyj polecenia docker build aby zbudować obraz. Pamiętaj, aby nadać mu nazwę za pomocą flagi -t.

## Krok 3: Przygotowanie pliku docker-compose.yml
Stwórz plik docker-compose.yml w tym samym katalogu co Dockerfile. W pliku tym, zdefiniuj usługę, która będzie uruchamiać Twój obraz. Pamiętaj, aby przekazać wartość zmiennej środowiskowej TARGET i zbindować katalog /report z katalogiem na hoście.

```yaml
version: '3'
services:
  network-diagnostic:
    image: <nazwa_twojego_obrazu>
    environment:
      - TARGET=www.example.com
    volumes:
      - ./report:/report
```
## Krok 4: Uruchomienie kontenera za pomocą Docker Compose
Na koniec, uruchom kontener z Twoim nowym obrazem za pomocą polecenia docker-compose up.
