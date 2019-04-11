---
title: Verwenden des Azure Maps-Kartensteuerelements | Microsoft-Dokumentation
description: Hier wird beschrieben, wie Sie die clientseitige JavaScript-Bibliothek des Azure Maps-Kartensteuerelements verwenden.
author: dsk-2015
ms.author: dkshir
ms.date: 10/08/2018
ms.topic: conceptual
ms.service: azure-maps
services: azure-maps
manager: timlt
ms.openlocfilehash: 56580454753ae6af60f5f8c51d9504f813f91e97
ms.sourcegitcommit: cf971fe82e9ee70db9209bb196ddf36614d39d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58540124"
---
# <a name="use-the-azure-maps-map-control"></a><span data-ttu-id="4548f-103">Verwenden des Azure Maps-Kartensteuerelements</span><span class="sxs-lookup"><span data-stu-id="4548f-103">Use the Azure Maps Map Control</span></span>

<span data-ttu-id="4548f-104">Mit der clientseitigen JavaScript-Bibliothek des Kartensteuerelements können Sie Karten und eingebettete Azure Maps-Funktionen in Ihrer Web- oder Mobilanwendung rendern.</span><span class="sxs-lookup"><span data-stu-id="4548f-104">The Map Control client-side Javascript library allows you to render maps and embedded Azure Maps functionality into your web or mobile application.</span></span>

## <a name="create-a-new-map-in-a-web-page"></a><span data-ttu-id="4548f-105">Erstellen einer neuen Karte auf einer Webseite</span><span class="sxs-lookup"><span data-stu-id="4548f-105">Create a new map in a web page</span></span>

<span data-ttu-id="4548f-106">Sie können eine Karte in eine Webseite einbetten, indem Sie die clientseitige JavaScript-Bibliothek des Kartensteuerelements verwenden.</span><span class="sxs-lookup"><span data-stu-id="4548f-106">You can embed a map in a web page by using the Map Control client-side Javascript library.</span></span>

1. <span data-ttu-id="4548f-107">Erstellen Sie eine neue HTML-Datei.</span><span class="sxs-lookup"><span data-stu-id="4548f-107">Create a new HTML file.</span></span>

2. <span data-ttu-id="4548f-108">Laden Sie das Azure Maps Web SDK.</span><span class="sxs-lookup"><span data-stu-id="4548f-108">Load in the Azure Maps Web SDK.</span></span> <span data-ttu-id="4548f-109">Dies kann auf einem von zwei Wegen erfolgen:</span><span class="sxs-lookup"><span data-stu-id="4548f-109">This can be done using one of two options;</span></span>

    <span data-ttu-id="4548f-110">a.</span><span class="sxs-lookup"><span data-stu-id="4548f-110">a.</span></span> <span data-ttu-id="4548f-111">Verwenden Sie die global gehostete CDN-Version des Azure Maps Web SDK, indem Sie dem Stylesheet die URL-Endpunkte und Skriptverweise im `<head>`-Element der Datei hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="4548f-111">Use the globally hosted CDN version of the Azure Maps Web SDK by adding the URL endpoints to the stylesheet and script references in the `<head>` element of the file:</span></span>

    ```HTML
    <link rel="stylesheet" href="https://atlas.microsoft.com/sdk/css/atlas.min.css?api-version=2" type="text/css">
    <script src="https://atlas.microsoft.com/sdk/js/atlas.min.js?api-version=2"></script>
    ```

    <span data-ttu-id="4548f-112">b.</span><span class="sxs-lookup"><span data-stu-id="4548f-112">b.</span></span> <span data-ttu-id="4548f-113">Laden Sie alternativ den Quellcode des Azure Maps Web SDK lokal mithilfe des NPM-Pakets [azure-maps-control](https://www.npmjs.com/package/azure-maps-control), und hosten Sie es zusammen mit Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="4548f-113">Alternatively, load the Azure Maps Web SDK source code locally using the [azure-maps-control](https://www.npmjs.com/package/azure-maps-control) NPM package and host it with your app.</span></span> <span data-ttu-id="4548f-114">Dieses Paket enthält außerdem TypeScript-Definitionen.</span><span class="sxs-lookup"><span data-stu-id="4548f-114">This package also includes TypeScript definitions.</span></span>

    > <span data-ttu-id="4548f-115">npm install azure-maps-control</span><span class="sxs-lookup"><span data-stu-id="4548f-115">npm install azure-maps-control</span></span>

    <span data-ttu-id="4548f-116">Fügen Sie dann dem `<head>`-Element der Datei Verweise auf das Azure Maps-Stylesheet und die Skriptquelle hinzu:</span><span class="sxs-lookup"><span data-stu-id="4548f-116">Then add references to the Azure Maps stylesheet and script source references to the `<head>` element of the file:</span></span>

    ```HTML
    <link rel="stylesheet" href="node_modules/azure-maps-control/dist/css/atlas.min.css" type="text/css">
    <script src="node_modules/azure-maps-control/dist/js/atlas.min.js"></script>
    ```

3. <span data-ttu-id="4548f-117">Um die Karte so zu rendern, dass sie den gesamten Bereich der Seite ausfüllt, fügen Sie dem `<head>`-Element das folgende `<style>`-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="4548f-117">To render the map so that it fills the full body of the page, add the following `<style>` element to the `<head>` element.</span></span>

    ```HTML
    <style>
        html, body {
            margin: 0;
        }

        #myMap {
            height: 100vh;
            width: 100vw;
        }
    </style>
    ```

4. <span data-ttu-id="4548f-118">Fügen Sie im Seitenbereich ein `<div>`-Element hinzu, und geben Sie ihm die `id` **myMap**.</span><span class="sxs-lookup"><span data-stu-id="4548f-118">In the body of the page, add a `<div>` element and give it an `id` of **myMap**.</span></span>

    ```HTML
    <body>
        <div id="myMap"></div>
    </body>
    ```

5. <span data-ttu-id="4548f-119">Definieren Sie zum Initialisieren des Kartensteuerelements im HTML-Text einen neuen Abschnitt, und erstellen Sie ein Skript.</span><span class="sxs-lookup"><span data-stu-id="4548f-119">To initialize the map control, define a new section in the html body and create a script.</span></span> <span data-ttu-id="4548f-120">Verwenden Sie Ihren eigenen Azure Maps-Kontoschlüssel oder Ihre Azure Active Directory-Anmeldeinformationen (AAD), um die Karte mithilfe der [Authentifizierungsoptionen](https://docs.microsoft.com/javascript/api/azure-maps-control/atlas.authenticationoptions) zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="4548f-120">Use your own Azure Maps account key or Azure Active Directory (AAD) credentials to authenticate the map using [authentication options](https://docs.microsoft.com/javascript/api/azure-maps-control/atlas.authenticationoptions).</span></span> <span data-ttu-id="4548f-121">Wenn Sie ein Konto erstellen oder Ihren Schlüssel ermitteln müssen, lesen Sie die Informationen unter [Verwalten Ihres Azure Maps-Kontos und der dazugehörigen Schlüssel](how-to-manage-account-keys.md).</span><span class="sxs-lookup"><span data-stu-id="4548f-121">If you need to create an account or find your key, see [How to manage your Azure Maps account and keys](how-to-manage-account-keys.md).</span></span> <span data-ttu-id="4548f-122">Die Option**language** gibt die Sprache an, die für Kartenbeschriftungen und Steuerelemente verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="4548f-122">The **language** option specifies the language to be used for map labels and controls.</span></span> <span data-ttu-id="4548f-123">Weitere Informationen zu unterstützten Sprachen finden Sie unter [Unterstützte Sprachen](supported-languages.md).</span><span class="sxs-lookup"><span data-stu-id="4548f-123">For more information on supported languages, see [supported languages](supported-languages.md).</span></span> <span data-ttu-id="4548f-124">Falls ein Abonnementschlüssel für die Authentifizierung verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="4548f-124">If using a subscription key for authentication.</span></span>

    ```HTML
    <script type="text/javascript">
        var map = new atlas.Map('myMap', {
            center: [-122.33, 47.6],
            zoom: 12,
            language: 'en-US',
            authOptions: {
                authType: 'subscriptionKey',
                subscriptionKey: '<Your Azure Maps Key>'
            }
        });
    </script>
    ```

    <span data-ttu-id="4548f-125">Falls Azure Active Directory (AAD) für die Authentifizierung verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="4548f-125">If using Azure Active Directory (AAD) for authentication:</span></span>

    ```HTML
    <script type="text/javascript">
        var map = new atlas.Map('myMap', {
            center: [-122.33, 47.6],
            zoom: 12,
            language: 'en-US',
            authOptions: {
                authType: 'aad',
                clientId: '<Your AAD Client Id>',
                aadAppId: '<Your AAD App Id>',
                aadTenant: 'msft.ccsctp.net'
            }
        });
    </script>
    ```

    <span data-ttu-id="4548f-126">Weitere Details finden Sie unter [Authentifizierung mit Azure Maps](azure-maps-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4548f-126">See [Authentication with Azure Maps](azure-maps-authentication.md) for more details.</span></span>

6. <span data-ttu-id="4548f-127">Es kann sinnvoll sein, dem Kopf der Seite die folgenden optionalen Metatagelemente hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="4548f-127">Optionally, you may find adding the following meta tag elements to the head of your page helpful:</span></span>

    ```HTML
    <!-- Ensures that IE and Edge uses the latest version and doesn't emulate an older version -->
    <meta http-equiv="x-ua-compatible" content="IE=Edge">

    <!-- Ensures the web page looks good on all screen sizes. -->
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    ```

7. <span data-ttu-id="4548f-128">Im Ergebnis sollte Ihre HTML-Datei ungefähr wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="4548f-128">Putting it all together your HTML file should look something like the following:</span></span>

    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <title></title>

        <meta charset="utf-8">

        <!-- Ensures that IE and Edge uses the latest version and doesn't emulate an older version -->
        <meta http-equiv="x-ua-compatible" content="IE=Edge">

        <!-- Ensures the web page looks good on all screen sizes. -->
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

        <!-- Add references to the Azure Maps Map control JavaScript and CSS files. -->
        <link rel="stylesheet" href="https://atlas.microsoft.com/sdk/css/atlas.min.css?api-version=2" type="text/css">
        <script src="https://atlas.microsoft.com/sdk/js/atlas.min.js?api-version=2"></script>

        <style>
            html, body {
                margin: 0;
            }

            #myMap {
                height: 100vh;
                width: 100vw;
            }
        </style>
    </head>
    <body>
        <div id="myMap"></div>

        <script type="text/javascript">
            //Create an instance of the map control and set some options.
            var map = new atlas.Map('myMap', {
                center: [-122.33, 47.6],
                zoom: 12,
                language: 'en-US',
                authOptions: {
                    authType: 'subscriptionKey',
                    subscriptionKey: '<Your Azure Maps Key>'
                }
            });
        </script>
    </body>
    </html>
    ```

8. <span data-ttu-id="4548f-129">Öffnen Sie die Datei in Ihrem Webbrowser, und zeigen Sie die gerenderte Karte an.</span><span class="sxs-lookup"><span data-stu-id="4548f-129">Open the file in your web browser and view the rendered map.</span></span> <span data-ttu-id="4548f-130">Die Anzeige sollte folgendermaßen aussehen:</span><span class="sxs-lookup"><span data-stu-id="4548f-130">It should look like the following:</span></span>

    <iframe height="700" style="width: 100%;" scrolling="no" title="Verwenden des Kartensteuerelements" src="//codepen.io/azuremaps/embed/yZpEYL/?height=557&theme-id=0&default-tab=html,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
<span data-ttu-id="4548f-132">Weitere Informationen finden Sie unter dem Pen <a href='https://codepen.io/azuremaps/pen/yZpEYL/'>Verwenden des Kartensteuerelements</a> von Azure Maps (<a href='https://codepen.io/azuremaps'>@azuremaps</a>) bei <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="4548f-132">See the Pen <a href='https://codepen.io/azuremaps/pen/yZpEYL/'>How to use the map control</a> by Azure Maps (<a href='https://codepen.io/azuremaps'>@azuremaps</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
    </iframe>

## <a name="next-steps"></a><span data-ttu-id="4548f-133">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="4548f-133">Next steps</span></span>

<span data-ttu-id="4548f-134">Erfahren Sie, wie Sie Karten erstellen und mit ihnen interagieren:</span><span class="sxs-lookup"><span data-stu-id="4548f-134">Learn how to create and interact with a map:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4548f-135">Erstellen einer Karte</span><span class="sxs-lookup"><span data-stu-id="4548f-135">Create a map</span></span>](map-create.md)

<span data-ttu-id="4548f-136">Erfahren Sie, wie Sie den Stil einer Karte auswählen:</span><span class="sxs-lookup"><span data-stu-id="4548f-136">Learn how to style a map:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4548f-137">Auswählen eines Kartenstils</span><span class="sxs-lookup"><span data-stu-id="4548f-137">Choose a map style</span></span>](choose-map-style.md)
