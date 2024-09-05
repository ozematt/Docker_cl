![Coders-Lab-1920px-no-background](https://user-images.githubusercontent.com/30623667/104709394-2cabee80-571f-11eb-9518-ea6a794e558e.png)



## Cel zadania

Celem zadania jest utworzenie środowiska developerskiego dla aplikacji ToDo z wykorzystaniem Dockera i Docker Compose.
Środowisko to będzie zawierać wszystkie niezbędne narzędzia do uruchomienia projektu, takie jak: Node.js, npm, itp.

## Krok 1: Utwórz plik Docker Compose
W tym pliku najpierw uruchomimy kontener Node.js i powiążemy aktualny katalog z kontenerem. W ten sposób możemy edytować pliki na naszej maszynie lokalnej, a zmiany zostaną odzwierciedlone w kontenerze. Wiemy, że będziemy używać Next.js do tego projektu, dlatego eksponujemy port 3000 kontenera na port 3000 maszyny lokalnej.

Pamiętaj, aby ustawić właściwy UID i GID, aby zapobiec problemom z uprawnieniami - możesz eksportować swoje ID jako zmienne środowiskowe USER_ID i GROUP_ID, edytując plik `.bashrc`, dzięki czemu nie będziesz musiał ich eksportować za każdym razem, gdy uruchamiasz kontener.

```bash
# ...poprzednia zawartość...
export USER_ID=$(id -u)
export GROUP_ID=$(id -g)
```

Utwórz plik o nazwie docker-compose.yml w głównym katalogu projektu z następującą zawartością:

```yaml
services:
  todo-app:
    image: node:21
    container_name: todo-app
    volumes:
      - .:/app
    working_dir: /app
    user: "${USER_ID}:${GROUP_ID}"
    tty: true
    ports:
      - "3000:3000"
```

## Krok 2: Uruchom kontener
Teraz możesz uruchomić kontener za pomocą następującego polecenia:

```bash
docker-compose up -d 
```

Gdy się uruchomi, utwórz nowy projekt Next.js.

Wejdź do powłoki kontenera:

```bash
docker compose exec -it todo-app bash
```

Z powłoki kontenera utwórz nowy projekt Next.js:

```bash
npx create-next-app app
```

Wybierz następujące parametry:

- TypeScript: YES
- ESLint: YES
- Tailwind CSS: NO // będziemy używać MaterialUI
- Użyj katalogu /src: NO
- Router aplikacji: YES // będziemy używać routera Next.js
- Importuj alias (@/*): NO

## Krok 3: Ponownie skonfiguruj docker-compose
Teraz mamy nowy katalog app i chcemy mieć tylko ten katalog powiązany z kontenerem:

```yaml
services:
  todo-app:
    image: node:21
    container_name: todo-app
    volumes:
      - ./app:/app
    working_dir: /app
    user: "${USER_ID}:${GROUP_ID}"
    tty: true
    ports:
      - "3000:3000"
```

Teraz zrestartuj kontener i uruchom aplikację:

```bash
docker-compose up -d 
docker compose exec -it timetracker bash
npm run dev
```

## Krok 4: Uprość uruchamianie środowiska deweloperskiego
Usuń kontener:

```bash
docker compose down
```

Napisz skrypt shell startdev.sh:

```bash
#!/bin/bash
docker compose up -d
docker compose exec -it timetracker bash
```

Następnie ustaw odpowiednie uprawnienia do wykonania skryptu:

```bash
chmod +x startdev.sh
```

Teraz, aby uruchomić nasze środowisko deweloperskie:

```bash
./startdev.sh
```

Jak teraz możemy zatrzymać środowisko deweloperskie? Najpierw zatrzymaj procesy w kontenerze, które uruchomiliśmy, np. npm start dev, następnie wyjdź z powłoki kontenera ctrl + d i wykonaj docker compose down.

Nie będziemy pisać kolejnego skryptu shell aby upraszczać ten proces, ale po prostu otwórz nowy terminal i wpisz docker compose down - to zatrzyma kontener i usunie go.

**Pamiętaj zawsze, aby opisać w pliku README.md, jak uruchamiać i zatrzymywać środowisko deweloperskie.**

## Krok 5: Rozpocznij rozwój
Teraz, gdy masz wszystko przygotowane, możesz otworzyć swój edytor kodu (np. VSCode), otworzyć w nim terminal i wykonać ./stardev.sh

Teraz znajdujesz się w terminalu kontenera, więc możesz wykonywać standardowe polecenia, których potrzebujesz, na przykład instalować paczki (npm i ...) lub uruchamiać serwer deweloperski (npm run dev).

Z edytora kodu możesz edytować swój kod źródłowy, tworzyć commity itp.

## Podsumowanie

Gratulacje! Udało Ci się utworzyć środowisko deweloperskie dla aplikacji ToDo z wykorzystaniem Dockera i Docker Compose. Teraz możesz zacząć pracę nad aplikacją.






## Cel zadania

Celem zadania jest skonfigurowanie procesu CI/CD dla aplikacji ToDo z wykorzystaniem GitHub Actions. Proces ten powinien zawierać następujące kroki:

- Budowanie obrazu Dockera
- Wypychanie obrazu do rejestru
- Skanowanie obrazu pod kątem bezpieczeństwa

Pipeline/Workflow ma być uruchamiany przy każdym pull request do gałęzi `develop` jak i `main`.


## Krok 1: Utwórz plik konfiguracyjny dla GitHub Actions

Utwórz plik konfiguracyjny dla GitHub Actions w katalogu `.github/workflows` o nazwie `ci-cd.yml`, który będzie zawierał następujące kroki:

- Budowanie obrazu Dockera
- Wypychanie obrazu do rejestru
- Skanowanie obrazu pod kątem bezpieczeństwa

## Krok 2: Github

Utwórz nowe repozytorium na GitHubie i wypchnij do niego projekt.

## Krok 3: Przetestuj proces CI/CD

Sprawdź czy odpowiednie akcje są uruchamiane przy każdym pull request do gałęzi `develop` jak i `main`.

- Utwórz nowy branch `develop` i utwórz pull request do gałęzi `main`. Sprawdź czy proces CI/CD działa poprawnie.
- Utwórz nowy branch np. `feature/new-feature` i utwórz pull request do gałęzi `develop`. Sprawdź czy proces CI/CD działa poprawnie.
- Sprawdź czy odpowiednie obrazy pojawiają się w rejestrze.


**Hint:**
W razie problemów, możesz podejrzeć odpowidnią gałąź w repozytorium [TimeTracker](https://github.com/DevNotes-it/TimeTracker)

## Cel zadania
Dopisanie funkcjonalności do aplikacji ToDo::
- Wyświetlanie listy zadań
- Dodawanie nowego zadania
- Zaznaczanie zadania jako wykonane (zadanie znika z listy)
- Wyświetlanie zakończonych zadań
- Filtrowanie zadań po treści (zarówno w zakończonych jak i niezakończonych, na górze nie zakończone, na dole zakończone)

## Wymagania

Aplikacja ma być zbudowana w oparciu o framework Next.js i :
- MaterialUI jako biblioteka komponentów
- React-Hook-Form jako biblioteka do obsługi formularzy
- Zod jako walidator formularzy

Design pozostawiamy do Twojej inwencji twórczej :)

## Krok 1: Instalacja niezbędnych paczek

Utwórz nową gałąź o nazwie `feature/todo-app` i przejdź na nią, a następnie uruchom środowisko deweloperskie, wykonując:

- `./startdev.sh` - aby uruchomić kontener deweloperski Docker
- `npm i` - aby zainstalować niezbędne paczki

### Doinstaluj niezbędne paczki

**MaterialUI dla komponentów stylizowanych**
```bash
npm install @mui/material-nextjs @mui/material @emotion/cache @emotion/react @emotion/styled @mui/icons-material @mui/x-date-pickers
```

**Zod do walidacji**
```bash
npm install zod
```

**ReactForm do obsługi formularzy**
```bash
npm install @tanstack/react-query
```

**luxon do obsługi dat**
```
npm install luxon @types/luxon
```

**uuid do generowania unikalnych identyfikatorów**
```bash
npm install uuid
```

### Krok 2: Zainspiruj się

Przeglądnij jak napisana jest aplikacja TimeTracker, jak są zaimplementowane funkcjonalności, jakie komponenty są wykorzystane, Zod jest wykorzystywany do walidacji formularzy itd.

(Time Tracker - Basic FE app)[https://github.com/DevNotes-it/TimeTracker/tree/basic-fe]


### Krok 3: Rozpocznij implementację

Po zainstalowaniu paczek, zapoznaniu się z aplikacją TimeTracker, rozpocznij implementację funkcjonalności.

### Krok 4: Testowanie CI/CD

Sprawdź czy proces CI/CD działa poprawnie, czy obrazy są budowane, czy są wypychane do rejestru, czy są skanowane pod kątem bezpieczeństwa, przy odpowiednich Pull Requestach.

### Krok 5: Testowanie aplikacji (krok dodatkowy)

Jako dodatkowy krok dopisz testy do aplikacji, które sprawdzą czy aplikacja działa poprawnie - mogą to być proste testy jednostkowe czy testy integracyjne.

Następnie rozbuduj proces CI/CD o uruchamianie testów.
