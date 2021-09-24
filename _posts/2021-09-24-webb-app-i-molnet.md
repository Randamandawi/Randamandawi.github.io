---
title: "Webb applikationer i molnet"
date: 2021-09-24T15:34:30-04:00
categories:
  - blog
tags:
  - Azure App Service
  - Razor Pages
  - ACR
---

Min applikation är en enkel to-do items verktyg som visar användaren sina to-do items och det går att lägga till nya items. 

![Applikationen](/assets/images/minpage.png)

Index sidan har jag använt för att visa alla to-do items, den innehåller alltså get metoden. För att lägga till nya items så har jag skapat en ny razor page i ”Pages” för att ha put metoden i. 

![Lägg till](/assets/images/additems.png)

Efter att användaren har lagt till en ny item och klickar på Submit så blir hen omdirigerad till Index sidan där hen ser alla items inklusive den nya. 

![Lägg till to-do item](/assets/images/exitem.png)

![Koden](/assets/images/exitem2.png)



## Koden 

I och med jag hade många problem med att få connection med databasen för förra uppgiften så har jag för det första tagit bort den gamla databasen och skapat en ny. Och för det andra så har jag gjort en ful lösning som på bilden nedan för att bli connectad med databasen/container. Jag har använt mig av den [här](https://docs.microsoft.com/en-us/azure/cosmos-db/sql/sql-api-get-started#GetSolution) guiden.

![Get metoden](/assets/images/indexcode.png)

För att fa fram alla to-do items från databasen så har jag använt koden från [Codegrepper](https://www.codegrepper.com/code-examples/csharp/cosmos+db+get+all+items+in+container) och skapat en lista för att lägga in alla items som har blivit skapade efter foreach loopen. 

Logiken i "AddItems" sida för att lägga till nya items.

![Put metoden](/assets/images/put.png)

Koden till frontend

![Frontend get](/assets/images/front.png)

Skapat en from och kopplat den till post metoden (på rad 8) så det blir view med rätt metod. 

![Frontend put](/assets/images/front2.png)

Efter att applikationen var klar och jag hade testad båda get och put metoder då var dags för att skapa en dockerfile, bygga an image och pusha den till Azure Container Registry (ACR) som jad hade skapat.

![ACR](/assets/images/acr.png)
 
 Till slut så har jag deployat docker image till Azure app genom Visual Studio med hjälp av [guiden](https://code.visualstudio.com/docs/containers/app-service)

 ![Sida](/assets/images/mywebsite.png)

## Kostnader 
 Nästan ingen använadere

![Låga kostnader](/assets/images/lowcost.png)

Många användare

![Höga kostnader](/assets/images/highcosts.png)



### Källor

- [Youtube](https://www.youtube.com/watch?v=aP02__gMLtw)