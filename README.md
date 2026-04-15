# Spawozdanie-Pawcho-1

## Opis Dockerfile
Użycie najnowszego obrazu systemu Ubuntu jako bazy.
```dockerfile
FROM ubuntu:latest
```
dane o autorze
```dockerfile
LABEL author="s101635@pollub.edu.pl Nowak Tomasz"
```

Aktualizacja systemu, instalacja Apache i czyszczenie cache.
```dockerfile
RUN apt update && \
    apt upgrade -y && \
    apt-get install -y apache2 && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
```
Kopiowanie pliku index do katalogu domyślnego Apache.
```dockerfile
COPY index.html /var/www/html/
```
Nasłuchiwanie w porcie 80.
```dockerfile
EXPOSE 80
```
Uruchomienie Apache w trybie foreground żeby kontener nie zakończył działania
```dockerfile
CMD ["apache2ctl", "-D", "FOREGROUND"]
```
## Warstwy
docker history sprawozdanie1
IMAGE          CREATED         CREATED BY                                      SIZE      COMMENT

41cd2a2b3ce3   5 minutes ago   CMD ["apache2ctl" "-D" "FOREGROUND"]            0B        buildkit.dockerfile.v0

<missing>      5 minutes ago   EXPOSE [80/tcp]                                 0B        buildkit.dockerfile.v0

<missing>      5 minutes ago   COPY index.html /var/www/html/                  20.5kB    buildkit.dockerfile.v0

<missing>      5 minutes ago   RUN /bin/sh -c apt update && apt upgrade -y...  142MB     buildkit.dockerfile.v0

<missing>      5 minutes ago   LABEL author=s101635@pollub.edu.pl Nowak Tom... 0B        buildkit.dockerfile.v0
