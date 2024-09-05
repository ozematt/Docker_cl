![Coders-Lab-1920px-no-background](https://user-images.githubusercontent.com/30623667/104709394-2cabee80-571f-11eb-9518-ea6a794e558e.png)


# Łączenie kontenerów

### Część 1
Utwórzcie trzy kontenery bazujące na obrazie alpine

```
docker run -it --name alpine01 -d alpine

docker run -it --name alpine02 -d alpine

docker run -it --name alpine03 -d alpine
```

Poprzez polecenie docker inspect zobaczcie jak wygląda konfiguracja sieciowa.
Wejdźcie do terminala każdego kontenera i poprzez polecenie ping sprawdźcie komunikację z pozostałymi kontenerami.

### Część 2

Utwórzcie dwie sieci:

```
docker network create FENet
docker network create BENet
```

Do sieci FENet podepnijcie kontenery alpine01 i alpine02.
Do sieci BENet podepnijcie kontenery alpine02 i alpine03.
Odepnijcie domyślną sieć bridge od wszystkich trzech kontenerów.

Sprawdźcie poprzez wejście do terminala każdego z kontenerów i ponownie skorzystnie z polecenia ping, które mogą się ze sobą komunikować.