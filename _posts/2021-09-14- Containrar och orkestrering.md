---
title: "Blogg 03: Containrar och orkestrering"
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

Sen körde jag i PoweShell ”build -t webapp .” Jag har ändrat namnet till webapp för att göra det lättare och med det här steget så har jag skapat min docker image. Genom att klistra http://localhost:8080 i min webbläsare har fått bekräftat att min container kör vilket den gjorde. 

### Beskrivning av min docker fil

För att få innehåll är det första vi behöver definiera är en image som vi vill basera den på. Vi måste också ange en fungerande working directory där vi vill att filerna ska hamna i containern. Vi gör det med kommandot FRÅN och WORKDIR. 
![Dockerfile](/assets/images/dockerfile1.png)


På bilden nedan så kopierar vi projektfilen som slutar på .csproj. Dessutom anropar vi ”dotnet restore” för att säkerställa att vi installerar alla dependencies
![Dockerfile](/assets/images/dockerfile2.png)

Sedan, vi kopierar app filerna och byggar appen
![Dockerfile](/assets/images/dockerfile3.png)

Här anger vi igen vår image och working directory
![Dockerfile](/assets/images/dockerfile4.png)

Det är dock en skillnad, den här gången vill vi kopiera våra byggda filer till app/out
![Dockerfile](/assets/images/dockerfile5.png)

Slutligen lägger vi till ett kommando för att ange hur vi startar vår app. Vi gör det med kommandot ENTRYPOINT
![Dockerfile](/assets/images/dockerfile6.png)

