![Coders-Lab-1920px-no-background](https://user-images.githubusercontent.com/30623667/104709394-2cabee80-571f-11eb-9518-ea6a794e558e.png)


# Instalacja i pierwsze uruchomienie Dockera

### Jak zainstalować Docker i uruchomić swój pierwszy kontener

Docker to niezbędne narzędzie dla deweloperów i administratorów systemów, umożliwiające łatwe tworzenie, wdrażanie i uruchamianie aplikacji w izolowanych kontenerach. Kontenery Dockera zapewniają konsystencję środowiska między różnymi etapami cyklu życia oprogramowania, co znacznie upraszcza rozwój i deployment aplikacji. Oto jak szybko zainstalować Docker na różnych systemach operacyjnych i uruchomić swój pierwszy kontener.

#### Krok 1: Instalacja Dockera

Instalacja Dockera różni się w zależności od używanego systemu operacyjnego. Poniżej znajdziesz instrukcje dla trzech najpopularniejszych systemów: Windows, macOS i Linux.

**Windows:**
- Odwiedź [oficjalną stronę Dockera](https://docker.com) i pobierz Docker Desktop dla Windows.
- Uruchom pobrany plik instalacyjny i postępuj zgodnie z instrukcjami na ekranie.
- Po zakończeniu instalacji, uruchom Docker Desktop. Pierwsze uruchomienie może zająć trochę czasu.

**macOS:**
- Pobierz Docker Desktop dla macOS ze [strony Dockera](https://docker.com).
- Otwórz pobrany plik `.dmg` i przeciągnij Docker do folderu Aplikacje.
- Otwórz Docker z folderu Aplikacje. Przy pierwszym uruchomieniu, macOS poprosi o potwierdzenie, że chcesz otworzyć aplikację pobraną z internetu.

**Linux:**
- Otwórz terminal i zaktualizuj listę pakietów: `sudo apt-get update` (dla dystrybucji opartych na Debianie/Ubuntu).
- Zainstaluj Docker używając polecenia: `sudo apt-get install docker-ce docker-ce-cli containerd.io`.
- Możesz potrzebować dodatkowych kroków w zależności od dystrybucji. Dokładne instrukcje dla różnych wersji Linuxa znajdziesz na [oficjalnej stronie Dockera](https://docs.docker.com/engine/install/).

**Weryfikacja instalacji:**
Bez względu na system, możesz sprawdzić, czy Docker został poprawnie zainstalowany, otwierając terminal (lub wiersz poleceń w Windows) i wpisując `docker --version`. Powinieneś zobaczyć numer wersji Dockera, co potwierdza, że instalacja przebiegła pomyślnie.

#### Krok 2: Uruchomienie pierwszego kontenera

Po pomyślnej instalacji Dockera, czas uruchomić swój pierwszy kontener. Użyjemy do tego celu prostego obrazu "Hello World" dostępnego na Docker Hub.

- Otwórz terminal lub wiersz poleceń i wpisz `docker run hello-world`.
- Docker automatycznie pobierze obraz "hello-world" z Docker Hub i uruchomi kontener. Na ekranie powinna pojawić się wiadomość powitalna od Dockera.

To polecenie demonstruje podstawową funkcjonalność Dockera - uruchamianie kontenerów. Docker pobiera obraz "hello-world", tworzy z niego kontener i uruchamia go, izolując jego środowisko od reszty systemu.

Gratulacje! Właśnie zainstalowałeś Docker i uruchomiłeś swój pierwszy kontener. Teraz jesteś gotowy do eksploracji bardziej zaawansowanych funkcji Dockera i uruchamiania własnych aplikacji w kontenerach.