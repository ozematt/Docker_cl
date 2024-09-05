![Coders-Lab-1920px-no-background](https://user-images.githubusercontent.com/30623667/104709394-2cabee80-571f-11eb-9518-ea6a794e558e.png)


# Uruchomienie serwera HTTP w Dockerze z mapowaniem portów

Celem tego zadania jest uruchomienie kontenera Dockera zawierającego prostą aplikację webową – serwer HTTP (Apache), oraz skonfigurowanie mapowania portów, aby umożliwić dostęp do aplikacji z hosta. Wykonanie tego zadania pozwoli Ci zrozumieć podstawy konteneryzacji aplikacji webowych oraz mechanizmy mapowania portów w Dockerze.

#### Krok 1: Pobieranie obrazu Apache HTTP Server

Twoim pierwszym zadaniem jest pobranie obrazu `httpd` z Docker Hub. Obraz `httpd` zawiera gotowy do użycia Apache HTTP Server, który posłuży jako nasza aplikacja webowa. Aby pobrać obraz, użyj następującego polecenia w terminalu:

```
docker pull httpd
```

#### Krok 2: Uruchomienie kontenera z mapowaniem portów

Po pobraniu obrazu, uruchom kontener na bazie obrazu `httpd`, skonfigurując mapowanie portów. Chcemy, aby serwer HTTP był dostępny na porcie 8080 naszego hosta. Użyj poniższego polecenia, aby uruchomić kontener:

```
docker run -d --name moj-apache -p 8080:80 httpd
```

Upewnij się, że polecenie zostało wykonane poprawnie, a kontener został uruchomiony.

#### Krok 3: Weryfikacja działania serwera HTTP

Aby zweryfikować, czy serwer HTTP działa i jest dostępny z hosta, otwórz przeglądarkę internetową i wpisz w pasku adresu `http://localhost:8080`. Powinieneś zobaczyć domyślną stronę powitalną Apache HTTP Server.

Jeśli strona się wyświetli, oznacza to, że pomyślnie uruchomiłeś serwer HTTP w kontenerze Docker i skonfigurowałeś mapowanie portów, aby umożliwić dostęp do serwera z hosta.

#### Podsumowanie

Gratulacje! Ukończyłeś zadanie praktyczne dotyczące uruchamiania kontenerów z aplikacjami webowymi i konfiguracji mapowania portów. Posiadanie tej umiejętności jest kluczowe przy pracy z kontenerami Docker, szczególnie gdy rozwijasz lub testujesz aplikacje webowe.

Jeśli napotkałeś jakiekolwiek trudności podczas wykonywania zadania, wróć do instrukcji i upewnij się, że wszystkie kroki zostały wykonane zgodnie z wytycznymi.