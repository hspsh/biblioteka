One of the most popular Docker images for Koha is [quantumobject/docker-koha](https://hub.docker.com/r/quantumobject/docker-koha).
In this example we are going to use the fork of mine of this image [mbledkowski/koha](https://hub.docker.com/r/mbledkowski/koha).
Before running the container we need to create `koha_database` volume
```
sudo docker volume create koha_database
```
and then we need to create, or download from this repository [docker-compose.yml](../docker-compose.yml) with given data
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
after that we type the following command `sudo docker-compose up`
When we start the container for the first time, the following error will be printed every second
```
ok: run: mysqld: (pid 586) 0s
httpd (pid 440) already running
```
or
```
ok: down: mysqld: 1s, normally up, want up
httpd (pid 566) already running
mysqld_safe Logging to syslog.
mysqld_safe A mysqld process already exists
```
for that reason, after the start script ends up executing, we should reboot

When container is up go to http://localhost:8080.
Login: `koha_library`
Password: In the logs from a first boot 
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
In this example it is `ku7gDLeOzA5ys5V@`

## License
CC BY 4.0 Maciej Błędkowski (@mble) for Hackerspace Pomorze
