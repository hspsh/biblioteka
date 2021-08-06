Jednym z popularniejszych obrazów dockerowych dla koha'y jest [quantumobject/docker-koha](https://hub.docker.com/r/quantumobject/docker-koha).
W tym przypadku, użyjemy forka tego obrazu stworzonego przeze mnie [mbledkowski/koha](https://hub.docker.com/r/mbledkowski/koha).
Przed uruchomieniem tworzymy wolumin `koha_database`
```
sudo docker volume create koha_database
```
a następnie tworzymy lub pobieramy z repozytorium plik [docker-compose.yml](../docker-compose.yml) o danej zawartości
```
services:
  koha:
    image: mbledkowski/koha:latest
    volumes:
      - koha_database:/database
    ports:
      - "80:80"
      - "8080:8080"
    cap_add:
      - SYS_NICE
      - DAC_READ_SEARCH
volumes:
  koha_database:
    external: true
```
po czym wpisujemy komendę `sudo docker-compose up`
Przy pierwszym uruchomieniu kontenera, będzie co sekundę wyświetlać się nam następujący błąd

```
ok: run: mysqld: (pid 586) 0s
httpd (pid 440) already running
```
w przypadku oryginalnego kontenera lub
```
ok: down: mysqld: 1s, normally up, want up
httpd (pid 566) already running
mysqld_safe Logging to syslog.
mysqld_safe A mysqld process already exists
```
w przypadku mojego forka 
z tego też powodu, po wykonaniu się skryptu startowego, kontener należy uruchomić ponownie.

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
