---
title: "Monitorering av moln applikationer"
date: 2021-10-06T15:34:30-04:00
categories:
  - blog
tags:
  - Monitorering
  - Serilog
---

Min applikation är en enkel to-do items verktyg som visar användaren sina to-do items och det går även att lägga till nya items. Mer information om applikationen finns [här](https://randamandawi.github.io/blog/webb-app-i-molnet/)

![Min applikation](/assets/images/serilog1.png)

### Diagram

![Diagram](/assets/images/serilog2.png)

För att implementera Serilog i min applikation så började jag med att ta hem de Nuget packages som behövdes och lägga till using. Serilog. I program.cs/main har jag lagt till kod som bilden nedan visar. Denna gången har jag valt att lägga InstrumentationKey i main istället för appsettings.json. För att få tillgång till min instrumentationsnyckel så har jag först skapat en ny application insights genom azure portalen.

![MainMetoden](/assets/images/serilog3.png)

Har även lagt till .UseSerilog(); i CreateHostBuilder

![Confiq](/assets/images/serilog4.png)

### Kusto queries

Första queryn tar fram alla Errors och Warnings i min applikation. Warnings är level 2 och Errors level 3. 

![Query](/assets/images/serilog5.png)

Jag har loggat när en to-do item blir tillagd av användaren. Detta gör jag för att få insikt i vilka kategorier som förkommer ofta/ skrivs ofta av användaren. På detta sätt kan jag förbättra min nya applikation genom att till exempel lägga till standard val av kategorier(som jag har samlat från logging) som användaren kan välja/markera istället för att mata in det manuellt. 

![Query](/assets/images/serilog6.png)

Query som visar tiden (loadtime) det tar att inläsa websidan

![Query](/assets/images/serilog7.png)

Det går även att göra queries på till exempel ”Client-Country/Region” för att få bild på länderna användare kommer ifrån eller befinner sig för att som utvecklare kunna implantera fler språk i applikationen. 

### Säkerhet

Om jag skulle har haft inloggning i min applikation vilket innebär att endast rätt personer har tillgång till datat. Genom att ha en Warning loggning kan jag då se om en användare plötsligt befinner sig i ett annat land eller befinner sig i två länder samtidigt. 
