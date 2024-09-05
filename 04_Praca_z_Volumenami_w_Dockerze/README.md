![Coders-Lab-1920px-no-background](https://user-images.githubusercontent.com/30623667/104709394-2cabee80-571f-11eb-9518-ea6a794e558e.png)


# Użycie Bind Mounts do współdzielenia danych między kontenerem a hostem

Celem zadania jest uruchomienie kontenera ze zbindowanym katalogiem na hoście, co umożliwi bezpośredni dostęp do plików na hoście z poziomu kontenera. Wykonanie tego zadania pozwoli Ci zrozumieć, jak wykorzystać Bind Mounts w Dockerze do współdzielenia danych między kontenerem a hostem, a tym samym ułatwi pracę z aplikacjami, które wymagają dostępu do plików na hoście - np. w trakcie developmentu.

#### Krok 1: Przygotowanie katalogu na hoście

Stwórz katalog na swoim komputerze, który będzie współdzielony z kontenerem. Możesz to zrobić za pomocą polecenia `mkdir`. Przykład:

```bash
mkdir ~/moj-katalog-dla-dockera
```

Umieść w tym katalogu pliki, które chcesz udostępnić kontenerowi.

#### Krok 2: Uruchomienie kontenera z wykorzystaniem Bind Mounts

Uruchom kontener, który będzie korzystał z twojego katalogu jako Bind Mount. Użyjemy obrazu `nginx`, aby zademonstrować serwowanie plików HTML:

```bash
docker run -d --name moj-nginx -v ~/moj-katalog-dla-dockera:/usr/share/nginx/html -p 8080:80 nginx
```

- `-d` uruchamia kontener w tle.
- `--name moj-nginx` nadaje kontenerowi nazwę.
- `-v ~/moj-katalog-dla-dockera:/usr/share/nginx/html` tworzy Bind Mount między katalogiem na hoście a katalogiem w kontenerze.
- `-p 8080:80` mapuje porty, umożliwiając dostęp do serwera nginx przez port 8080 na hoście.

#### Krok 3: Weryfikacja działania

W katalogu `~/moj-katalog-dla-dockera` umieść plik `index.html` z dowolną treścią HTML. Następnie, odwiedź `http://localhost:8080` w przeglądarce, aby sprawdzić, czy serwer nginx poprawnie wyświetla zawartość pliku `index.html`.

#### Podsumowanie

Wykonałeś zadanie praktyczne związane z Bind Mounts, co pozwoliło na bezpośrednie udostępnienie danych z systemu hosta w kontenerze. To podejście jest niezwykle przydatne podczas pracy nad aplikacjami, gdzie szybka iteracja i dostęp do plików na hoście jest kluczowy.

Pamiętaj o ostrożności podczas korzystania z Bind Mounts, gdyż zapewniają one bezpośredni dostęp do systemu plików hosta.

# Implementacja trwałego przechowywania danych z użyciem volumenów w Dockerze

Celem zadania jest uruchomienie kontenera z podpiętym volumenem w celu przechowywania danych bazy danych MySQL. Dzięki temu, dane z bazy będą trwałe i nie zostaną utracone po zatrzymaniu kontenera. Wykonanie tego zadania pozwoli Wam zrozumieć, jak volumeny w Dockerze mogą być wykorzystane do zarządzania danymi w aplikacjach, zapewniając ich trwałość.

#### Krok 1: Tworzenie Volumenu

Rozpocznijcie od utworzenia nowego volumenu, który posłuży do przechowywania danych bazy danych. Użyjcie poniższego polecenia w terminalu:

```bash
docker volume create mysql-dane
```

To polecenie tworzy volumen o nazwie `mysql-dane`, który będzie wykorzystany do trwałego przechowywania danych bazy danych MySQL.

#### Krok 2: Uruchomienie kontenera MySQL

Następnie, uruchomcie kontener Docker z bazą danych MySQL, przypisując do niego wcześniej utworzony volumen. Dzięki temu, dane z bazy będą przechowywane na volumenie i nie zostaną utracone po zatrzymaniu kontenera. Wykonajcie polecenie:

```bash
docker run -d --name moja-mysql -e MYSQL_ROOT_PASSWORD=mojeHaslo -v mysql-dane:/var/lib/mysql mysql
```

Oto co każdy z elementów polecenia oznacza:
- `-d` uruchamia kontener w tle.
- `--name moja-mysql` nadaje kontenerowi nazwę.
- `-e MYSQL_ROOT_PASSWORD=mojeHaslo` ustawia hasło dla użytkownika root MySQL.
- `-v mysql-dane:/var/lib/mysql` montuje volumen `mysql-dane` w ścieżce `/var/lib/mysql` w kontenerze, co umożliwia trwałe przechowywanie danych MySQL.

#### Krok 3: Testowanie trwałości danych

Po uruchomieniu kontenera, przetestujcie zachowanie danych:
1. Wejdźcie do MySQL w kontenerze, aby stworzyć testową bazę danych.
2. Zatrzymajcie i uruchomcie ponownie kontener.
3. Sprawdźcie, czy testowa baza danych nadal istnieje.

To zadanie pozwoli Wam zrozumieć, jak volumeny w Dockerze mogą być wykorzystane do zarządzania danymi w aplikacjach, zapewniając ich trwałość. Po zakończeniu eksperymentujcie z różnymi scenariuszami, aby lepiej zrozumieć działanie i możliwości volumenów. Powodzenia!