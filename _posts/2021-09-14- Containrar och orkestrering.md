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
Innan jag började så hade jag redan Docker installerat på min dator. Jag började med att klona ner “Hello world” .NET Core webb applikationen från Github. Jag följde den här tutorial efter att ha klonat ner projektet: [How YOU can Dockerize a .Net Core app](https://softchris.github.io/pages/dotnet-dockerize.html#build-our-image-start-container)  

I Visual Studio Code har jag manuellt skapat en Dockerfile. I den har jag klistrat in texten från ovanstående tutorial. I dockerfilen har jag ändrat sdk på rad 1 och 13 från 2.2 till 3.1. På rad 16 så har jag ändrat namnet på applikationen till ”SimpleWebHalloWorld.dll” som på bilden:
![Dockerfile](/assets/images/dockerfile.png)

Sedan har jag skapat en dockerignore fil som ser ut som på bilden nedan:
![Dockerignore](/assets/images/dockerignore.png)

Sen körde jag i PoweShell ”build -t webapp .”. Jag har ändrat namnet till webapp för att göra det lättare. Och med det här steget så har jag skapat min docker image. Genom att klistra http://localhost:8080 i min webbläsare har fått bekräftat att min container kör vilket det den gjorde. 
