---
title: "Webb applikationer i molnet"
date: 2021-09-07T15:34:30-04:00
categories:
  - blog
tags:
  - Azure App Service
  - Razor Pages
  - ACR
---
Min applikation är en enkel to-do items verktyg som visar användaren sina to-do items och det går att lägga till nya items. 

![Applikationen](/assets/images/minpage.png)

Index sidan har jag använt för att visa alla to-do items, den innehåller alltså get metoden. För att lägga till nya items så har jag skapat en ny razor page i ”Pages” för att ha put metoden. 

![Lägg till](/assets/images/additems.png)

Efter att användaren har lagt till en ny item och klickar på Submit så blir hen omdirigerad till Index sidan där hen ser alla items inklusive den nya. 

![Lägg till to-do item](/assets/images/exitem.png)

![Lägg till to-do item index](/assets/images/exitem2.png)