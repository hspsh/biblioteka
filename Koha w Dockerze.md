Jednym z popularniejszych obrazów dockerowych dla koha'y jest [quantumobject/docker-koha](https://hub.docker.com/r/quantumobject/docker-koha).
Przed uruchomieniem tworzymy woluminy `kohaconf` i `kohadb`
```
sudo docker volume create kohaconf
sudo docker volume create kohadb
```
a następnie tworzymy następujący plik docker-compose.yml (!!! plik ten jest work in progress, aktualnie volumes są źle ustawione !!!)
```
services:
  koha:
    image: quantumobject/docker-koha
    volumes:
      - kohaconf:/var/lib/koha/library
      - kohadb:/var/lib/mysql
    ports:
      - "80:80"
      - "8080:8080"
    cap_add:
      - SYS_NICE
      - DAC_READ_SEARCH
volumes:
  kohaconf:
    external: true
  kohadb:
    external: true
```
po czym wpisujemy komendę `sudo docker-compose up`
Przy pierwszym uruchomieniu kontenera, będzie co sekundę wyświetlać się nam następujący błąd
```
ok: run: mysqld: (pid 586) 0s
httpd (pid 440) already running
```
z tego też powodu kontener należy uruchomić ponownie.

Po uruchomieniu wejdź na http://localhost:8080.
Login: `koha_library`
Password: Znajduje się w logach z pierwszego uruchomienia
```
[...]
koha_1  | Site 000-default disabled.
koha_1  | To activate the new configuration, you need to run:
koha_1  |   service apache2 reload
koha_1  | Password:  ku7gDLeOzA5ys5V@
koha_1  | starting rc.local scritps
koha_1  | Booting runit daemon...
koha_1  | Process runsvdir running with PID 576
[...]
```
W tym przypadku jest to `ku7gDLeOzA5ys5V@`

## License
CC BY 4.0 Maciej Błędkowski (@mble) for Hackerspace Pomorze