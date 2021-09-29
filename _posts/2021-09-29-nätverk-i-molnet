---
title: "Nätverk i molnet"
date: 2021-09-29T15:34:30-04:00
categories:
  - blog
tags:
  - Azure Service Bus
  - Virtual Private Cloud
  - Azure Private Link 
---

Hej CTO, 

Stort tack för att få några minuter av din tid. 

Förra veckan har vi diskuterat hur vi kan modernisera vår applikation och har kommit fram till att Azure Service Bus skulle vara värdefullt för vår verksamhet. Jag har tagit i beaktning din argument och oro gällande data säkerhet och en molnlösning som denna. 
För att kunna implementera Azure Service Bus så kan vi använda oss av Azure Private Link för att säkerställa att data färdas på ett säkert sätt. Hur detta fungerar kommer jag att förklara nedan. 

Jag börjar med att summera Azure Service Bus och dess features. Innan vi går vidare med att berättar varför Azure Private Link är en lösning för oss.

Azure Service Bus är en molnplattform som gör att man kan skicka data mellan olika program och tjänster med asynkrona meddelanden. Service Bus används för att frikoppla program och tjänster från varandra och garanterar att inga meddelanden förloras. För att skicka och ta emot meddelanden så kan man använda sig av köer/queue,  ämnen/topics. 

### Köer
Meddelanden skickas till och tas emot från köer. Köer lagrar meddelanden tills det mottagande programmet är tillgängligt för att ta emot och bearbeta dem. En kö tillåter bearbetning av ett meddelande av en enskild mottagare/konsument. Meddelanden skickas från punkt 1 (avsändare) till punkt 2(mottagare) och mottagaren brukar vara en specifik sort/typ applikation. 
Meddelanden i köer sorteras och tidsstämplas vid ankomst och blir levererade enligt First In, First Out principen men det går att påverka det genom att tilldela properties till meddelanden. 

### Ämnen
Medan en kö oftast används för kommunikation från punkt1 till punkt2 är ämnen användbara i scenarier med subscription/prenumeration som är riktade till flera mottagare. Ämnen kan ha flera, oberoende prenumerationer som bifogas till ämnet och fungerar på samma sätt precis som köer från mottagarsidan. En prenumerant på ett ämne får en kopia av varje meddelande. Det går att använda ett filter på prenumeration för att till exempel en prenumeration inte ska ta emot alla meddelanden som skickas till ett ämne.

Service Bus erbjuder funktioner som gör att man kan lösa mer komplexa meddelandeproblem. Jag vill gärna ta upp följande funktioner:

* Dead-letter: när ett meddelande inte bli levererat till en mottagare på grund av ett fel så hamnar meddelandet i en dead-letter kö (DLQ). Meddelanden loggas med orsaken varför de har placerats i kön och är där tills det bestäms vad man ska göra med de. Ta bort de, automatiskt vidarebefordra eller åtgärda felet. På detta sätt så förlorar man inga meddelanden. 
* Meddelandesessioner: detta innebär att man kan gruppera meddelanden och hanteras eller  bearbetas i samma session. 
* Schemalagd leverans: innebär att man kan skicka meddelanden till en kö eller ett ämne och ange en tid när meddelandet ska bli tillgängligt för användning. Meddelandet blir osynligt för mottagaren tills den valde tiden inträffar. 
* Duplicate message detection: om av någon anledning ett meddelande blir skickad två gånger. Systemet förstår att det är samma meddelande som har skickats igen. Meddelandet blir ignorerad och kastas bort
* Förfallodatum för meddelanden (Time to Live): om ett meddelande inte blir levererad efter en viss tidsgräns så levereras inte innehållet längre, eller så körs inte längre den begärda åtgärden.

För att kunna komma åt den här tjänsten så kan vi använda oss av Azure Private Link Service. Azure Private Link Service gör att vi kan komma åt Azure Service Bus via en privat tunnel och endpoint mellan vårt företags virtuella nätverk och azure services, se bilden nedan.

![app4](/assets/images/virtualprivatemoln.png)

Den privata endpointen använder alltså en privat IP-adress från vårt VNet vilket gör att inga offentliga IP-adresser behövs. Så all trafik mellan vårt virtuella nätverk och tjänsten passerar över Microsofts stamnätverk, vilket eliminerar exponering mot det offentliga Internet. 
Vi ansluter oss privat till Azure resurser som det vore en del av vårt nätverk och skapar på det sättet en Virtual Private Cloud vilket innebär att vi har tillgång till en isolerad del av Azure molnbaserade tjänster som vi nyttjar. I Azure kan man skapa ett eget nätverk med våra tjänster som virtuella maskiner och Azure services. På det här sättet kan vi kombinera Azure resuser med våra interna system. 
Med denna förklaring av Azure Bus, Private Link hoppas jag att det  är tydligare kring hur vi kan säkerställa att datat färdas på ett säkert sätt från företags nätverk och de tjänster som nyttjas i Azure miljön. 
