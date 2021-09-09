---
title: "Vad är CI pipeline?"
date: 2021-09-07T15:34:30-04:00
categories:
  - blog
tags:
  - CI Pipeline
  - Github
  - Actions
 
---

Först vill jag börja med att förklara vad Continuous Integration (CI), eller kontinuerlig integration innebär. CI handlar om att utvecklare kontinuerligt integrerar och testar sitt arbete i ett automatiserat ramverk. Så det är en programutvecklingsmetod där alla utvecklare slår samman kodändringar centralt flera gånger om dagen. Varje kodändring (push eller pull) gör att det sker en automatisk bygg och test för att upptäcka fel så tidigt som möjligt. På så vis kan man snabbt och tidigt få en signal på om något i koden är fel eller behöver göras om. Själva testfasen fungerar därmed som en kvalitetssäkring av den slutgiltiga produkten.

Men vad är en pipeline? Inom datavetenskap är en datarörledning – oftare kallad en rörledning – en serie steg som utför fördefinierade åtgärder på tillhandahållna data eller kod. Varje utgång från ett steg blir ingången till nästa steg i rörledningen. Dessa steg kan initieras efter varandra eller samtidigt. Målet med en pipeline är att automatisera en uppsättning repetitiva processer för att spara tid och öka precisionen.

En CI pipeline är en serie steg som består av bygg och test och som utföras vid varje kodändring. Vid varje ändring trigger/aktiverar en automatiserad build-and-test-sekvens för det givna projektet, vilket ger feedback till utvecklaren som gjorde ändringen. 

![CI pipeline](/assets/images/CI.png)


### Implementering CI pipeline 

Vi har implementerat en CI pipeline på ett gammalt projekt. I Github började vi med att forka projektet. Efter det valde vi ”Actions” och sen ”New Workflow”. Från de olika mallar så valde vi .Net mallen för att hålla det enkelt nu i början. I ”yml” filen behövde vi ändra vad som gör att pipeline triggas och vi valde ”push” enligt uppgiften. Vi har även ändrat vid ”branches” genom att låta det tomt efter ”branches” så det blir default vilket innebär att det ska kolla på alla branches. I ”jobs” behövde vi lägga till sökvägen till SpacePark.sln för att den ska hitta vad som skall byggas och testas.

### Beskrivning min GitHub action workflow YAML fil
![yml file](/assets/images/yml2.png)


### Källor
[title](https://www.example.com)
