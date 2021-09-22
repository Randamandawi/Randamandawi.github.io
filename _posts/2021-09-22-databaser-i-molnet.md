---
title: "Databaser i molnet"
date: 2021-09-17T15:34:30-04:00
categories:
  - blog
tags:
  - CosmosDB
  - Databas
  - Azure
---

Min applikation sparar ToDoItems som består av en id, namn och en kategori. Det går att visa en Item genom att söka på kategori eller namn. 

Jag började bygga min ”Azure function/http trigger” i Visual Studio Code och har connectad den med ComosDb. Alltså databasen som jag har skapat på Azure portalen efter att jag skapade database resource group. När jag försökte bygga den så fick jag ett fel och efter att Stephan och jag har öppnat applikationen i Visual Studio så blev det tydligt att felet beror på en NuGet package som saknades. 

Jag bestämde mig att jobba vidare i Visual Studio och fick nedanstående applikationen byggd utan fel. 
![app](/assets/images/VSoK.png)  


Jag la till en Get metod och försökte testa den i Azure portalen där jag fick fel att den inte hittar id property. Jag har bland annat testat med stora och små bokstäver på azure portalen, och även kommenterat bort nedanstående raderna i koden men det har inte hjälpt. 
![app2](/assets/images/vsOut.png) 


Efter ett tag så var de omöjligt att bygga projektet i Visual Studio på grund av massa fel.
![app3](/assets/images/error.png) 

Med hjälp av Sofie så har vi skapat en ny applikation men på grund av tidsbrist så har jag tyvärr inte hunnit med att göra den helt färdig. 

