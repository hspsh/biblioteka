## Web installer
### Login
Login: `koha_library` gdzie library to nazwa stworzonej biblioteki
Password: w pliku `/etc/koha/sites/library/koha-conf.xml` (gdzie library to nazwa biblioteki) wewnątrz `config` > `pass`
### Choose your language
Select a language: **en**
### Check Perl dependencies
Continue
### Database settigns
Continue i continue
### Set up database
Continue i continue
### Install basic configuration settings
Continue
### Select your MARC flavor
**Marc21**
### Selecting default settings
#### MARC frameworks
##### Mandatory
✅Default MARC21 Standard Authority types
✅MARC21 Default and Acquisitions bibliographic frameworks
##### Optional
✅Selected matching rules for MARC 21 bibliographic records
✅'FA', a 'Fast Add' minimal MARC21 framework suitable for ILL or on-the-fly cataloguing
✅Simple MARC 21 bibliographic frameworks for some common types of bibliographic material

#### Other data
##### Mandatory
✅Default Koha system authorised values  
✅Default classification sources and filing rules for Koha.  
✅Sample frequencies for subscriptions  
✅Sample notices  
✅Sample numbering patterns for subscriptions  
#### Optional
✅Some basic default authorised values for library locations, item lost status, etc.  
You can change these at any time after installation.  
✅CSV profiles
✅Default CSV export profiles; including one for exporting serial claims
✅Coded values conforming to the Z39.71-2006 holdings statements for bibliographic items
✅MARC code list for relators, as of http://www.loc.gov/marc/relators/relaterm.html  
✅Some basic currencies with USA dollar as default for ACQ module  
✅Useful patron attribute types
✅Sample patron types and categories
✅Sample label and patron card data
✅A set of default item types
☐Sample libraries
✅Sample holidays: Sunday, Christmas, New Year's  
✅Sample news items  
☐Sample patrons  
✅Sample quotes  
✅Allow access to the following servers to search and download record information

#### Wyjaśnienie poszczególnych opcji
[Koha Installation on Ubuntu Linux - YouTube; Od: 16:07](https://youtu.be/ooPIgy-rBVU?t=967)

### Create a library
Library code: `HSP`
Name: `Hackerspace Pomorze Library` lub `Biblioteka Hackerspace Pomorze`
### Create Koha administrator patron
#### Administrator identity
Surname: *Kowalski*
First name: *Jan*
Card number: *1337*
Library: `Hackerspace Pomorze Library`
Patron category: `Staff`
#### Administrator login
Username: `jkowalski`
Password: Staff account's password
### Create a new circulation rule
Library branch All
Patron category: All
Item type: All
Current checkouts allowed: 50
Loan period: 14
Units: Days
Renewals allowed: 10
Renewals period: 14
Holds allowed (total): 10
Holds allowed (daily): 10
Holds per record (count): 1
On shelf holds allowed: Yes

## Koha administration
### Modify the statistics you share with the Koha community
Administration › [Usage statistics](http://localhost:8080/cgi-bin/koha/admin/usage_statistics.pl)
Share my Koha usage statistics: `No`

### Importing MARC entries from file
https://kohageek.blogspot.com/2016/12/import-marc-records-into-koha.html

## Komendy
### Instalowanie innych języków
`koha-translate --list` - pobierz listę języków
`koha-translate --list --available` - pokaż listę dostępnych języków
`koha-translate --install pl-PL` - zainstaluj język polski

## Porady
Nie działa wyszukiwanie? Użyj komendy `koha-rebuild-zebra`
-   `-f, --full` Reindeksuje całą kolekcję. Wykona się, nawet jeśli USE_INDEXER_DAEMON=yes.
-   `-a, --authorities` Wykonuje proces indeksowania dla rekordów authority.
-   `-b, --biblios` Wykonuje proces indeksowania dla rekordów biblio.
-   `-q, --quiet` Może być ciut szybsze, przydatne dla skryptów/cronjobs
-   `-v, --verbose` Tryb gadatliwy, przydatny dla debugowania.

Przykład: `koha-rebuild-zebra -v -f library`

Połączenie z serwerami memcached nie działa? Spróbuj tego https://kohageek.blogspot.com/2018/06/enable-memcached-with-koha.html
Wpisz `sudo apt-get install memcached`, jeśli jest już zainstalowane wpisz `sudo service memcached restart`.

## License
CC BY 4.0 Maciej Błędkowski (@mble) for Hackerspace Pomorze
