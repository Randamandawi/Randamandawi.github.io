---
title: "Severless applikationer"
date: 2021-09-17T15:34:30-04:00
categories:
  - blog
tags:
  - Serverless
  - FaaS
  - Azure

---

Serverless innebär att ett företag kan köra sina applikationer och tjänster utan att bry sig om de underliggande servrarna. Hur mycket datakraft, minne och virtuella hårddiskar en applikation behöver är inget företaget behöver tänka på, utan molnleverantören ansvarar för att hantera allt detta. 

Trots namnet används givetvis servrar fortfarande i bakgrunden men all hantering och resursplanering av dessa görs av molnleverantören som jag nämnde ovan. 

När man refererar till serverless så är begreppet FaaS (Function as a service) som används som definition. Function as a Service är ett sätt att exekvera funktioner i molnet utan att ha en egen webbserver. Som utvecklare skriver man funktioner som kan anropa varandra, eller andra rutiner, och även kan triggas av olika händelser. Och det kostar bara pengar när funktioner körs. 

### kalkylator

Jag började min kalkylator i Visual Studio och valde ”Azure function” mallen. I koden har jag tagit bort ”string name” och lagt till 2 ”doubles” som på bilden.

![Koden](/assets/images/code.png)  

Dem ”doubles” bli parsade med ”double.TryParse(req.Query["first"], out first)” för att inte tillåta att användaren kan skicka nåt annat än en siffra som till exempel en bokstav eller ett annat tecken för att det returneras 0. ”String sum” har jag också lagt till och jag byggde funktionen. Efter applikationen byggde klart så har jag testat den lokalt. Jag gick sen till Azure för att skapa ”Resource group” och en ”Function App” (bara skalet) för att kunna publicera min applikation från Visual Studio till Azure. Med Azure URL har jag testat applikationen i båda Visual Studio code och på Azure som på bilden nedan.

![Test 1](/assets/images/testazure.png)

Vid inmatning av # så får användaren en 0 tillbaka
![Test 2](/assets/images/testazure2.png)



### Säkerhet

Efter en genomgång av OWASPs top tio lisa så har jag konstaterat att injection och Cross-Site Scripting (XSS) kan hota min applikations säkerhet. Injection blir mer aktuellt om jag skulle ha haft ett inloggningssystem eller databas kopplad till min applikation. Indatat för min applikation har jag begränsat till bara siffror, jag har ingen känslig data in min kod och jag har inget behöv av att autentisera användare vilket gör risken för en injection liten. Det finns också en risk för Cross-Site Scripting om jag skulle till exempel har visat ett felmeddelande till användaren som går att manipulera av en hackare i syfte att försöka dirigera om webbläsaren till en fientlig webbsida. Min applikation kräver ingen inloggning vilket minimerar risken att den fientliga webbsidan begär inloggningsinformation eller annan information från användaren. 

### Källor 
- [Infozone](https://www.infozone.se/2021/06/21/vad-ar-serverless/)
- [OWASP Top 10](https://owasp.org/www-pdf-archive/OWASP-Top-10-Serverless-Interpretation-en.pdf)


