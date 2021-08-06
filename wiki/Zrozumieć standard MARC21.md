Gdy pierwszy raz ujrzysz stronę dodawania wpisu MARC, może ci się wydać to niemożliwe, jednak w tym artykule pokażę ci jak **zrozumieć standard MARC21**.

😒 - najprawdopodobniej będziesz chciałx to pominąć
🏀 - wymagane

## Przydatne informacje
W wielu przypadkach pole z danym numerem można umieścić kilkukrotnie, przykładowo pole 020 aby zapisać kilka identyfikatorów. Przyciskiem do duplikacji danego pola w programie koha jest `Repeat this tag`, znajdujący się obok przycisku usuwania.

## Opis sekcji i pól - record
### Section 0
**000, 005, 008** 🏀 - automatycznie wygenerowane przez koha'ę

**[007](https://www.oclc.org/bibformats/en/0xx/007text.html)** - fizyczny opis przedmiotu
dla standardowych książek - `ta`; t - text, a - regular print

**015** 😒 - identyfikator NBN, książki przeznaczone na rynek polski raczej nie posiadają

**[020](https://www.oclc.org/bibformats/en/0xx/020.html)** - identyfikator ISBN, zarówno wersja 13'sto jak i 10'cio znakowa jest akceptowana
Pola:
a - identyfikator
q 😒 - informacje o przedmiocie z danym identyfikatorem np.: paperback, electronic

**037** 😒 - Źródło pozyskania

**040** - organizacja która stworzyła dany wpis
a - organizacja która stworzyła oryginalny wpis
c - organizacja która jest odpowiedzialna za przepisanie go do formatu cyfrowego 
W przypadku Hackerspace Pomorze proponuję używać skrótu `HSP`.


**041** - Język
Pierwszy wskaźnik - tłumaczenie:
\# - Brak informacji
0 - Nie dotyczy
1 - Dotyczy
Drugi wskaźnik - źródło kodu:
\# - kod standardu MARC
7 - Źródło określone w polu `2` 
Pola:
a - kod języka (pol, eng itd.)
h - język oryginału
2 😒 - źródło kodu (np. iso639-1)

### Section 1
**100** - autor (każdy autor ma swój oddzielny wpis)

## Opis sekcji i pól - authority


## Przykłady
Jeżeli jesteś zainteresowanx tym jak w bazie gdańskich bibliotek wojewódzkich są zapisywane książki przy użyciu MARC, wejdź na stronę http://katalogbpg.wbpg.org.pl:8085/Opac4/faces/Glowna.jsp, wybierz książkę i w zakładce `Widok` wejdź w `Wszystko w Marc OPAC kartoteka`

### Przykładowy wpis z tej biblioteki:
```
005 a20171109085338.0  
008 a171109p20172017pl ? ? - ? - pol|d  
041 0 apol  
045 0 bd1983  
046 k1983  
100 1 aNowaczyk, Henryk.  
245 10 aGroźba zawisła nad Półwyspem Helskim :bzamgania ludzi z groźnym żywiołem : drogi i tory podmyte : zagrożone całe Wybrzeże : alarm powodziowy w Gdańsku /cHenryk Nowaczyk, (M.T.), (A.C.).  
336 aTekstbtxt2rdacontent  
337 aBez urządzenia pośredniczącegobn2rdamedia  
338 aWoluminbnc2rdacarrier  
380 aArtykuły  
388 1 a1901-2000  
388 1 a1945-1989  
648 4 a1901-2000  
648 4 a1945-1989  
650 4 aPowódź  
650 4 aMeteorologia  
650 4 aKlimat  
650 4 aKlęski elementarne  
651 4 aMierzeja Helskaxklęski elementarne  
655 4 aArtykuł z czasopisma regionalnego i lokalnego  
655 4 aArtykuł z gazety  
658 aBiologia  
700 0 aM.T  
700 0 a(A.C.)  
773 1 i//tDziennik Bałtycki. - g1983, nr 15, s. 1-2  
999 aGD Wbij
```

## Przydatne linki
### Wyszukiwanie informacji przy pomocy ISBN
https://isbnsearch.org/isbn/9788373661349
https://isbndata.org/978-83-7197-465-6/sed-i-awk
https://www.googleapis.com/books/v1/volumes?q=isbn:9788324643363

### Wyszukiwanie ISBN w serwerach Z39.50 bibliotek
https://www.worldcat.org/title/css-the-definitive-guide/oclc/967188453&referer=brief_results

### Wyszukiwanie biblotek z publicznie dostępnymi serwerami Z39.50
http://mle.dmu.ac.uk/mle-project/files/z39_50_target_directory.htm
http://irspy.indexdata.com/find.html?_count=10&_search=Search&_skip=100&zeerex.country=Canada

## License
CC BY 4.0 Maciej Błędkowski (@mble) for Hackerspace Pomorze