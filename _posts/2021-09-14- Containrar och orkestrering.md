---
title: "Containrar och orkestrering"
date: 2021-09-14T15:34:30-04:00
categories:
  - blog
tags:
  - Dockerfile
  - Build
  - Image
 
---
Innan jag började så hade jag redan docker/ docker desktop installerat på min dator. Jag började med att klona ner “Hello world” .NET Core webb applikationen från Github. Jag följde den här tutorial efter att ha klonat ner projektet: [How YOU can Dockerize a .Net Core app](https://softchris.github.io/pages/dotnet-dockerize.html#build-our-image-start-container)  

I Visual Studio Code har jag manuellt skapat en Dockerfile. I den har jag klistrat in texten från ovanstående tutorial. I dockerfilen har jag ändrat sdk på rad 1 och 13 från 2.2 till 3.1. På rad 16 så har jag ändrat namnet på applikationen till ”SimpleWebHalloWorld.dll” som på bilden:
![Dockerfile](/assets/images/dockerfile.png)

Sedan har jag manuellt skapat en dockerignore fil som ser ut som på bilden nedan:
![Dockerignore](/assets/images/dockerignore.png)

Sen körde jag i PoweShell ”build -t webapp .” Jag har ändrat namnet till webapp för att göra det lättare och med det här steget så har jag skapat min docker image. Genom att klistra http://localhost:8080 i min webbläsare har jag fått bekräftat att min container kör. 

### Beskrivning av min docker fil

För att få innehåll är det första vi behöver definiera är en image som vi vill basera den på. Vi måste också ange en fungerande working directory där vi vill att filerna ska hamna i containern. Vi gör det med kommandot FRÅN och WORKDIR. 
![Dockerfile](/assets/images/dockerfile1.png)


På bilden nedan så kopierar vi projektfilen som slutar på .csproj. Dessutom anropar vi ”dotnet restore” för att säkerställa att vi installerar alla dependencies
![Dockerfile](/assets/images/dockerfile2.png)

Sedan, kopierar vi app filerna och byggar appen
![Dockerfile](/assets/images/dockerfile3.png)

Här anger vi igen vår image och working directory
![Dockerfile](/assets/images/dockerfile4.png)

Det är dock en skillnad, den här gången vill vi kopiera våra byggda filer till app/out
![Dockerfile](/assets/images/dockerfile5.png)

Slutligen lägger vi till ett kommando för att ange hur vi startar vår app. Vi gör det med kommandot ENTRYPOINT
![Dockerfile](/assets/images/dockerfile6.png)

### Beskrivning av min github pipeline 
För att skapa min github pipeline så har jag följt den [här](https://itnext.io/build-ship-github-container-registry-kubernetes-aa06029b3f21#0075) guiden och detta innebär att jag skapade en pipeline som var baserad på Publish Docker Container mallen i github workflow. Den har tyvärr inte funkat och jag fick ersätta den med exemplet Stephan hade lagt under uppgift 3. För att få den att funka så fick jag ändra mitt användarnamn på github till små bokstäver. 

![Github pipeline](/assets/images/githubpipeline.png)

### Hemlisar 
Först skapade jag en token under mina kontoinställningar. Sen efter att ha frågat en klasskamrat så har jag förstått att man ska använda { { github.actor } } och { { secrets.GITHUB_TOKEN } } för att hålla användarnamn och lösenord hemligt. På detta sätt så skapar Github en github token för repot. Så jag behövde inte använda mig av den token jag har skapat och inte hellre göra något med ”Secrets” som finns på repo settings. 

