# Vad kurs DD1331 behöver från ett LADOK/Canvas-API

## Use case: Slå ihop delresultat i Canvas till Ladok-moment och rapportera in till Ladok. Hitta också studenter som saknar enstaka delresultat och lägg in dessa i en separat lista som jag kan maila och berätta vad de har kvar att göra.

Manuell variant, använd studentstatus-scriptet som Alexander har skrivit, räkna ihop i huvudet och om det utgör ett Ladok-moment, rapportera in till Ladok manuellt. Gör detta kolumn för kolumn i Ladok.

Automatiserad variant:
Från API:et vill jag ha samma information som jag hade fått om jag hade gjort Result Export från Canvas manuellt, med tillägget att jag också vill ha den ladoknyckel för varje enskild student som jag kan använda för att rapportera in eventuellt delresultat till Ladok.

Jag vill dessutom kunna göra detta för alla gamla kursomgångar för att dels kunna leta efter gamla delresultat, men också se om studenten har varit inskriven på gamla kursomgångar eftersom detta gör att eventuella bonuspoäng till följd av att göra saker i tid är irrelevanta eftersom DD1331 inte erbjuder plusning.

De kursomgångar jag vill läsa från är endast de kursomgångar som går för CTFYS, inte andra DD1331-kursomgångar som Stenes kurser för CTMAT och CTFYS.

Att ha alla uppgifter i en grupp fungerar inte eftersom vi har deadlinegrundande betyg, och det går inte att mata in i Canvas när en viss uppgift faktiskt blev klar. Detta gör att jag måste ha separata fält för labb 1 i tid, labb 1 extra i tid, labb 1 mindre än en vecka sen och liknande. Dessa moment behöver jag sedan slå ihop manuellt men detta ingår i min del av scriptet och inte själva Canvas-API:et.

När jag gör dessa summeringar så kommer jag att upptäcka enskilda studenter som inte är helt klara med kursen. Då vore det bra att spara undan dessa "Nästan klara"-studenter i en fil. Det jag behöver från API:et här är att när jag använder canvaslms så får jag inte ut studenternas mailadresser eller namn utan endast deras LADOK-nyckel. Den är bra vid inrapportering, men inte vid mailning av "du är nästan klar".

LADOK-api:et är utmärkt för att rapportera in alla när jag väl har räknat ihop det och behöver inget ytterligare för detta use case.

## Use case: Statistik.

Jag vill föra statistik inte bara över hur många som har klarat ett visst delmoment ett visst år utan också hur stor andel av de förförstagångenregistrerade studenter som gjorde detta. Det är mycket mer relevant för mig än hur många inklusive överliggare. Statistik kan behöva fråga Canvas om individuella labbar som inte slagits ihop till.

# Vad DD1366 behöver från ett LADOK/Canvas-API

DD1366 har delresultat utspridda på 3 olika gamla kurskoder, DD1360, DD1361 och DD1362. Dessa har lite olika poängtal och olika mått på när studenterna är klara med kursen. Tidigare år har jag bara slagit ihop och testat att rapportera in alla kurskoder som studenten är färdig med. Om studenten sedan inte skulle vara registrerad på en variant som hen har gjort klart så är detta inget problem eftersom LADOK-scriptet då helt enkelt inte lyckas rapportera in denna student på detta ladokmoment.

## Use case: Rapportera in resultat till Ladok

Det här fungerar redan. Jag kan hämta ut alla gamla delresultat, slå ihop dessa med ett Pythonscript till ett Ladokinrapporteringsscript och rapportera in till Ladok.

## Use case: Statistik

Här är det klurigt. Jag vill kunna kolla hur stor andel av de förförstagångenregistrerade studenterna som går datateknik som har klarat ett visst moment automatiskt. Det ger mig inte så mycket att kolla hur många överliggare/studenter från andra linjer som har klarat ett visst moment utan jag är främst ute efter FFG-registrerade från en viss linje. Det här är kan jag inte göra med det nuvarande API:et eftersom jag inte kan få ut information om vilken linje studenten tillhör. Jag vill sedan kunna kolla om studenten har äldre registreringar så att jag inte räknar omregistrerade studenter. Det vore förstås intressant att ha den statistiken också, men separat från FFG-statistiken.