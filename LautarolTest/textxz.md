---
title: How to use the Azure Maps Map Control | Microsoft Docs
description: Learn how to use the Azure Maps Map Control client-side Javascript library.
author: dsk-2015
ms.author: dkshir
ms.date: 10/08/2018
ms.topic: conceptual
ms.service: azure-maps
services: azure-maps
manager: timlt
---

# <a name="use-the-azure-maps-map-control"></a><span data-ttu-id="551ff-103">Use the Azure Maps Map Control</span><span class="sxs-lookup"><span data-stu-id="551ff-103">Use the Azure Maps Map Control</span></span>

<span data-ttu-id="551ff-104">The Map Control client-side Javascript library allows you to render maps and embedded Azure Maps functionality into your web or mobile application.</span><span class="sxs-lookup"><span data-stu-id="551ff-104">The Map Control client-side Javascript library allows you to render maps and embedded Azure Maps functionality into your web or mobile application.</span></span>

## <a name="create-a-new-map-in-a-web-page"></a><span data-ttu-id="551ff-105">Create a new map in a web page</span><span class="sxs-lookup"><span data-stu-id="551ff-105">Create a new map in a web page</span></span>

<span data-ttu-id="551ff-106">You can embed a map in a web page by using the Map Control client-side Javascript library.</span><span class="sxs-lookup"><span data-stu-id="551ff-106">You can embed a map in a web page by using the Map Control client-side Javascript library.</span></span>

1. <span data-ttu-id="551ff-107">Create a new HTML file.</span><span class="sxs-lookup"><span data-stu-id="551ff-107">Create a new HTML file.</span></span>

2. <span data-ttu-id="551ff-108">Load in the Azure Maps Web SDK.</span><span class="sxs-lookup"><span data-stu-id="551ff-108">Load in the Azure Maps Web SDK.</span></span> <span data-ttu-id="551ff-109">This can be done using one of two options;</span><span class="sxs-lookup"><span data-stu-id="551ff-109">This can be done using one of two options;</span></span>

    <span data-ttu-id="551ff-110">a.</span><span class="sxs-lookup"><span data-stu-id="551ff-110">a.</span></span> <span data-ttu-id="551ff-111">Use the globally hosted CDN version of the Azure Maps Web SDK by adding the URL endpoints to the stylesheet and script references in the `<head>` element of the file:</span><span class="sxs-lookup"><span data-stu-id="551ff-111">Use the globally hosted CDN version of the Azure Maps Web SDK by adding the URL endpoints to the stylesheet and script references in the `<head>` element of the file:</span></span>

    ```HTML
    <link rel="stylesheet" href="https://atlas.microsoft.com/sdk/javascript/mapcontrol/2/atlas.min.css" type="text/css">
    <script src="https://atlas.microsoft.com/sdk/javascript/mapcontrol/2/atlas.min.js"></script>
    ```

    <span data-ttu-id="551ff-112">b.</span><span class="sxs-lookup"><span data-stu-id="551ff-112">b.</span></span> <span data-ttu-id="551ff-113">Alternatively, load the Azure Maps Web SDK source code locally using the [azure-maps-control](https://www.npmjs.com/package/azure-maps-control) NPM package and host it with your app.</span><span class="sxs-lookup"><span data-stu-id="551ff-113">Alternatively, load the Azure Maps Web SDK source code locally using the [azure-maps-control](https://www.npmjs.com/package/azure-maps-control) NPM package and host it with your app.</span></span> <span data-ttu-id="551ff-114">This package also includes TypeScript definitions.</span><span class="sxs-lookup"><span data-stu-id="551ff-114">This package also includes TypeScript definitions.</span></span>

    > <span data-ttu-id="551ff-115">npm install azure-maps-control</span><span class="sxs-lookup"><span data-stu-id="551ff-115">npm install azure-maps-control</span></span>

    <span data-ttu-id="551ff-116">Then add references to the Azure Maps stylesheet and script source references to the `<head>` element of the file:</span><span class="sxs-lookup"><span data-stu-id="551ff-116">Then add references to the Azure Maps stylesheet and script source references to the `<head>` element of the file:</span></span>

    ```HTML
    <link rel="stylesheet" href="node_modules/azure-maps-control/dist/css/atlas.min.css" type="text/css">
    <script src="node_modules/azure-maps-control/dist/js/atlas.min.js"></script>
    ```

3. <span data-ttu-id="551ff-117">To render the map so that it fills the full body of the page, add the following `<style>` element to the `<head>` element.</span><span class="sxs-lookup"><span data-stu-id="551ff-117">To render the map so that it fills the full body of the page, add the following `<style>` element to the `<head>` element.</span></span>

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

4. <span data-ttu-id="551ff-118">In the body of the page, add a `<div>` element and give it an `id` of **myMap**.</span><span class="sxs-lookup"><span data-stu-id="551ff-118">In the body of the page, add a `<div>` element and give it an `id` of **myMap**.</span></span>

    ```HTML
    <body>
        <div id="myMap"></div>
    </body>
    ```

5. <span data-ttu-id="551ff-119">To initialize the map control, define a new section in the html body and create a script.</span><span class="sxs-lookup"><span data-stu-id="551ff-119">To initialize the map control, define a new section in the html body and create a script.</span></span> <span data-ttu-id="551ff-120">Use your own Azure Maps account key or Azure Active Directory (AAD) credentials to authenticate the map using [authentication options](https://docs.microsoft.com/javascript/api/azure-maps-control/atlas.authenticationoptions).</span><span class="sxs-lookup"><span data-stu-id="551ff-120">Use your own Azure Maps account key or Azure Active Directory (AAD) credentials to authenticate the map using [authentication options](https://docs.microsoft.com/javascript/api/azure-maps-control/atlas.authenticationoptions).</span></span> <span data-ttu-id="551ff-121">If you need to create an account or find your key, see [How to manage your Azure Maps account and keys](how-to-manage-account-keys.md).</span><span class="sxs-lookup"><span data-stu-id="551ff-121">If you need to create an account or find your key, see [How to manage your Azure Maps account and keys](how-to-manage-account-keys.md).</span></span> <span data-ttu-id="551ff-122">The **language** option specifies the language to be used for map labels and controls.</span><span class="sxs-lookup"><span data-stu-id="551ff-122">The **language** option specifies the language to be used for map labels and controls.</span></span> <span data-ttu-id="551ff-123">For more information on supported languages, see [supported languages](supported-languages.md).</span><span class="sxs-lookup"><span data-stu-id="551ff-123">For more information on supported languages, see [supported languages](supported-languages.md).</span></span> <span data-ttu-id="551ff-124">If using a subscription key for authentication.</span><span class="sxs-lookup"><span data-stu-id="551ff-124">If using a subscription key for authentication.</span></span>

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

    <span data-ttu-id="551ff-125">If using Azure Active Directory (AAD) for authentication:</span><span class="sxs-lookup"><span data-stu-id="551ff-125">If using Azure Active Directory (AAD) for authentication:</span></span>

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

    <span data-ttu-id="551ff-126">For more information, see [Authentication with Azure Maps](azure-maps-authentication.md) for more details.</span><span class="sxs-lookup"><span data-stu-id="551ff-126">For more information, see [Authentication with Azure Maps](azure-maps-authentication.md) for more details.</span></span>

6. <span data-ttu-id="551ff-127">Optionally, you may find adding the following meta tag elements to the head of your page helpful:</span><span class="sxs-lookup"><span data-stu-id="551ff-127">Optionally, you may find adding the following meta tag elements to the head of your page helpful:</span></span>

    ```HTML
    <!-- Ensures that IE and Edge uses the latest version and doesn't emulate an older version -->
    <meta http-equiv="x-ua-compatible" content="IE=Edge">

    <!-- Ensures the web page looks good on all screen sizes. -->
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    ```

7. <span data-ttu-id="551ff-128">Putting it all together your HTML file should look something like the following code:</span><span class="sxs-lookup"><span data-stu-id="551ff-128">Putting it all together your HTML file should look something like the following code:</span></span>

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
        <link rel="stylesheet" href="https://atlas.microsoft.com/sdk/javascript/mapcontrol/2/atlas.min.css" type="text/css">
        <script src="https://atlas.microsoft.com/sdk/javascript/mapcontrol/2/atlas.min.js"></script>

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

8. <span data-ttu-id="551ff-129">Open the file in your web browser and view the rendered map.</span><span class="sxs-lookup"><span data-stu-id="551ff-129">Open the file in your web browser and view the rendered map.</span></span> <span data-ttu-id="551ff-130">It should look like the following code:</span><span class="sxs-lookup"><span data-stu-id="551ff-130">It should look like the following code:</span></span>

    <iframe height="700" style="width: 100%;" scrolling="no" title="How to use the map control" src="//codepen.io/azuremaps/embed/yZpEYL/?height=557&theme-id=0&default-tab=html,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
<span data-ttu-id="551ff-132">See the Pen <a href='https://codepen.io/azuremaps/pen/yZpEYL/'>How to use the map control</a> by Azure Maps (<a href='https://codepen.io/azuremaps'>@azuremaps</a>) on <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="551ff-132">See the Pen <a href='https://codepen.io/azuremaps/pen/yZpEYL/'>How to use the map control</a> by Azure Maps (<a href='https://codepen.io/azuremaps'>@azuremaps</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
    </iframe>

## <a name="next-steps"></a><span data-ttu-id="551ff-133">Next steps</span><span class="sxs-lookup"><span data-stu-id="551ff-133">Next steps</span></span>

<span data-ttu-id="551ff-134">Learn how to create and interact with a map:</span><span class="sxs-lookup"><span data-stu-id="551ff-134">Learn how to create and interact with a map:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="551ff-135">Create a map</span><span class="sxs-lookup"><span data-stu-id="551ff-135">Create a map</span></span>](map-create.md)

<span data-ttu-id="551ff-136">Learn how to style a map:</span><span class="sxs-lookup"><span data-stu-id="551ff-136">Learn how to style a map:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="551ff-137">Choose a map style</span><span class="sxs-lookup"><span data-stu-id="551ff-137">Choose a map style</span></span>](choose-map-style.md)
