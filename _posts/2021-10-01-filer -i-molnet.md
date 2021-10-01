---
title: "Filer i molnet"
date: 2021-10-01T15:34:30-04:00
categories:
  - blog
tags:
  - AZzure cloud storage
  - Blob
---

Jag har gjort en konsolapplikation som laddar upp filer till min Azure blob storage/ container. Applikationen hämtar de filerna som finns på Azure och visar deras namn och URL som på bilden nedan.

![Konsolapplikation](/assets/images/showurl.png)

Blobs som finns i min container

![Blobcontainer](/assets/images/blobcontainer.png)

Diagrammet visar hur data flyttar sig från applikationen till containern i Azure

![Diagram](/assets/images/digram.png)

Koden för att ladda upp filer

![Ladda upp](/assets/images/upload.png)

Koden för att hämta filer och visa deras namn och URL

![Ladda ner](/assets/images/getblob.png)

#### Kostnader

![Kostnader](/assets/images/blobcost.png)

### Säkerhet

Azure garanterar säkerhet på tre olika nivåer:
* Säkerhet av deras moln: inbyggda säkerhetsfunktionerna i deras underliggande molnplattformsinfrastruktur
* Säkerhet i deras moln: genom att ha säkerhetsprodukter och tjänsttillägg som är tillgängliga i deras molnplattform
* Säkerhet var som helst: garantera säkerheten utanför deras molnplattform för att skydda användaren data oavsett plats genom kryptering. 

Datakryptering i sin tur består av:
* Kryptering av data i vila
* Kryptering av data under överföring
* Nyckel hantering med Key Vault

### Källor
- [Medium](https://medium.com/@rammonzito/azure-blob-storage-using-a-net-core-console-application-106a0c2e6de5)

- [Cloudacademy](https://cloudacademy.com/blog/how-does-azure-encrypt-data/)

- [Microsoft](https://docs.microsoft.com/en-us/javascript/api/@azure/storage-blob/containerclient?view=azure-node-latest)