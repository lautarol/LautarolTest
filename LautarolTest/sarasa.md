---
title: Walkthrough - Using Background Location
ms.topic: article
ms.prod: xamarin
ms.assetid: F8EEA0FD-5614-47FE-ADAC-80A5BCA6EB5F
ms.technology: xamarin-ios
author: bradumbaugh
ms.author: brumbaug
ms.date: 03/18/2017
---

# <a name="walkthrough---using-background-location"></a><span data-ttu-id="cd558-102">Walkthrough - Using Background Location</span><span class="sxs-lookup"><span data-stu-id="cd558-102">Walkthrough - Using Background Location</span></span>

<span data-ttu-id="cd558-103">In this example, we are going to build an iOS Location application that prints information about our current location: latitude, longitude, and other parameters to the screen.</span><span class="sxs-lookup"><span data-stu-id="cd558-103">In this example, we are going to build an iOS Location application that prints information about our current location: latitude, longitude, and other parameters to the screen.</span></span> <span data-ttu-id="cd558-104">This application will demonstrate how to properly perform location updates while the application is either Active or Backgrounded.</span><span class="sxs-lookup"><span data-stu-id="cd558-104">This application will demonstrate how to properly perform location updates while the application is either Active or Backgrounded.</span></span>

<span data-ttu-id="cd558-105">This walkthrough explains some key backgrounding concepts, including registering an app as a background-necessary application, suspending UI updates when the app is backgrounded, and working with the `WillEnterBackground` and `WillEnterForeground` `AppDelegate` methods.</span><span class="sxs-lookup"><span data-stu-id="cd558-105">This walkthrough explains some key backgrounding concepts, including registering an app as a background-necessary application, suspending UI updates when the app is backgrounded, and working with the `WillEnterBackground` and `WillEnterForeground` `AppDelegate` methods.</span></span>

## <a name="application-set-up"></a><span data-ttu-id="cd558-106">Application set up</span><span class="sxs-lookup"><span data-stu-id="cd558-106">Application set up</span></span>


1. <span data-ttu-id="cd558-107">First, create a new **iOS > App > Single View Application (C#)**.</span><span class="sxs-lookup"><span data-stu-id="cd558-107">First, create a new **iOS > App > Single View Application (C#)**.</span></span> <span data-ttu-id="cd558-108">Call it _Location_ and ensure that both iPad and iPhone have been selected.</span><span class="sxs-lookup"><span data-stu-id="cd558-108">Call it _Location_ and ensure that both iPad and iPhone have been selected.</span></span>

1. <span data-ttu-id="cd558-109">A location application qualifies as a background-necessary application in iOS.</span><span class="sxs-lookup"><span data-stu-id="cd558-109">A location application qualifies as a background-necessary application in iOS.</span></span> <span data-ttu-id="cd558-110">Register the application as a Location application by editing the **Info.plist** file for the project.</span><span class="sxs-lookup"><span data-stu-id="cd558-110">Register the application as a Location application by editing the **Info.plist** file for the project.</span></span>

    <span data-ttu-id="cd558-111">Under Solution Explorer, double click on the **Info.plist** file to open it, and scroll to the bottom of the list.</span><span class="sxs-lookup"><span data-stu-id="cd558-111">Under Solution Explorer, double click on the **Info.plist** file to open it, and scroll to the bottom of the list.</span></span> <span data-ttu-id="cd558-112">Place a check by both the **Enable Background Modes** and the **Location Updates** checkboxes.</span><span class="sxs-lookup"><span data-stu-id="cd558-112">Place a check by both the **Enable Background Modes** and the **Location Updates** checkboxes.</span></span>

    <span data-ttu-id="cd558-113">In Visual Studio for Mac, it will look like something like this:</span><span class="sxs-lookup"><span data-stu-id="cd558-113">In Visual Studio for Mac, it will look like something like this:</span></span>

    <span data-ttu-id="cd558-114">[![](location-walkthrough-images/image7.png "Place a check by both the Enable Background Modes and the Location Updates checkboxes")](location-walkthrough-images/image7.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="cd558-114">[![](location-walkthrough-images/image7.png "Place a check by both the Enable Background Modes and the Location Updates checkboxes")](location-walkthrough-images/image7.png#lightbox)</span></span>

    <span data-ttu-id="cd558-115">In Visual Studio, **Info.plist** needs to be updated manually by adding the following key/value pair:</span><span class="sxs-lookup"><span data-stu-id="cd558-115">In Visual Studio, **Info.plist** needs to be updated manually by adding the following key/value pair:</span></span>

    ```xml
    <key>UIBackgroundModes</key>
    <array>
        <string>location</string>
    </array>
    ```

1. <span data-ttu-id="cd558-116">Now that the application is registered, it can get location data from the device.</span><span class="sxs-lookup"><span data-stu-id="cd558-116">Now that the application is registered, it can get location data from the device.</span></span> <span data-ttu-id="cd558-117">In iOS, the `CLLocationManager` class is used to access location information, and can raise events that provide location updates.</span><span class="sxs-lookup"><span data-stu-id="cd558-117">In iOS, the `CLLocationManager` class is used to access location information, and can raise events that provide location updates.</span></span>

1. <span data-ttu-id="cd558-118">In the code, create a new class called `LocationManager` that provides a single place for various screens and code to subscribe to location updates.</span><span class="sxs-lookup"><span data-stu-id="cd558-118">In the code, create a new class called `LocationManager` that provides a single place for various screens and code to subscribe to location updates.</span></span> <span data-ttu-id="cd558-119">In the `LocationManager` class, make an instance of the `CLLocationManager` called `LocMgr`:</span><span class="sxs-lookup"><span data-stu-id="cd558-119">In the `LocationManager` class, make an instance of the `CLLocationManager` called `LocMgr`:</span></span>

    ```csharp
    public class LocationManager
    {
        protected CLLocationManager locMgr;

        public LocationManager () {
            this.locMgr = new CLLocationManager();
            this.locMgr.PausesLocationUpdatesAutomatically = false;

            // iOS 8 has additional permissions requirements
            if (UIDevice.CurrentDevice.CheckSystemVersion (8, 0)) {
                locMgr.RequestAlwaysAuthorization (); // works in background
                //locMgr.RequestWhenInUseAuthorization (); // only in foreground
            }

            if (UIDevice.CurrentDevice.CheckSystemVersion (9, 0)) {
                locMgr.AllowsBackgroundLocationUpdates = true;
            }
        }

        public CLLocationManager LocMgr {
            get { return this.locMgr; }
        }
    }
    ```

    <span data-ttu-id="cd558-120">The code above sets a number of properties and permissions on the [CLLocationManager](https://developer.xamarin.com/api/type/CoreLocation.CLLocationManager/) class:</span><span class="sxs-lookup"><span data-stu-id="cd558-120">The code above sets a number of properties and permissions on the [CLLocationManager](https://developer.xamarin.com/api/type/CoreLocation.CLLocationManager/) class:</span></span>

    - <span data-ttu-id="cd558-121">`PausesLocationUpdatesAutomatically` – This is a Boolean that can be set depending on whether the system is allowed to pause location updates.</span><span class="sxs-lookup"><span data-stu-id="cd558-121">`PausesLocationUpdatesAutomatically` – This is a Boolean that can be set depending on whether the system is allowed to pause location updates.</span></span> <span data-ttu-id="cd558-122">On some device it defaults to `true`, which can cause the device to stop getting background location updates after about 15 minutes.</span><span class="sxs-lookup"><span data-stu-id="cd558-122">On some device it defaults to `true`, which can cause the device to stop getting background location updates after about 15 minutes.</span></span>
    - <span data-ttu-id="cd558-123">`RequestAlwaysAuthorization` - You should pass this method to give the app user the option to allow the location to be accessed in the background.</span><span class="sxs-lookup"><span data-stu-id="cd558-123">`RequestAlwaysAuthorization` - You should pass this method to give the app user the option to allow the location to be accessed in the background.</span></span> <span data-ttu-id="cd558-124">`RequestWhenInUseAuthorization` can also be passed if you wish to give the user the option to allow the location to be accessed only when the app is in the foreground.</span><span class="sxs-lookup"><span data-stu-id="cd558-124">`RequestWhenInUseAuthorization` can also be passed if you wish to give the user the option to allow the location to be accessed only when the app is in the foreground.</span></span>
    - <span data-ttu-id="cd558-125">`AllowsBackgroundLocationUpdates` – This is a Boolean property, introduced in iOS 9 that can be set to allow an app to receive location updates when suspended.</span><span class="sxs-lookup"><span data-stu-id="cd558-125">`AllowsBackgroundLocationUpdates` – This is a Boolean property, introduced in iOS 9 that can be set to allow an app to receive location updates when suspended.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="cd558-126">**WARNING**: iOS 8 (and greater) also requires an entry in the **Info.plist** file to show the user as part of the authorization request.</span><span class="sxs-lookup"><span data-stu-id="cd558-126">**WARNING**: iOS 8 (and greater) also requires an entry in the **Info.plist** file to show the user as part of the authorization request.</span></span>

1. <span data-ttu-id="cd558-127">Add a key `NSLocationAlwaysUsageDescription` or `NSLocationWhenInUseUsageDescription` with a string that will be displayed to the user in the alert that requests location data access.</span><span class="sxs-lookup"><span data-stu-id="cd558-127">Add a key `NSLocationAlwaysUsageDescription` or `NSLocationWhenInUseUsageDescription` with a string that will be displayed to the user in the alert that requests location data access.</span></span>

1. <span data-ttu-id="cd558-128">iOS 9 requires that when using `AllowsBackgroundLocationUpdates` the **Info.plist** includes the key `UIBackgroundModes` with the value `location`.</span><span class="sxs-lookup"><span data-stu-id="cd558-128">iOS 9 requires that when using `AllowsBackgroundLocationUpdates` the **Info.plist** includes the key `UIBackgroundModes` with the value `location`.</span></span> <span data-ttu-id="cd558-129">If you have completed step 2 of this walkthrough, this should already been in your Info.plist file.</span><span class="sxs-lookup"><span data-stu-id="cd558-129">If you have completed step 2 of this walkthrough, this should already been in your Info.plist file.</span></span>


1. <span data-ttu-id="cd558-130">Inside the `LocationManager` class, create a method called `StartLocationUpdates` with the following code.</span><span class="sxs-lookup"><span data-stu-id="cd558-130">Inside the `LocationManager` class, create a method called `StartLocationUpdates` with the following code.</span></span> <span data-ttu-id="cd558-131">This code shows the how to start receiving location updates from the   `CLLocationManager`:</span><span class="sxs-lookup"><span data-stu-id="cd558-131">This code shows the how to start receiving location updates from the   `CLLocationManager`:</span></span>

    ```csharp
    if (CLLocationManager.LocationServicesEnabled) {
        //set the desired accuracy, in meters
        LocMgr.DesiredAccuracy = 1;
        LocMgr.LocationsUpdated += (object sender, CLLocationsUpdatedEventArgs e) =>
        {
            // fire our custom Location Updated event
            LocationUpdated (this, new LocationUpdatedEventArgs (e.Locations [e.Locations.Length - 1]));
        };
        LocMgr.StartUpdatingLocation();
    }
    ```

    <span data-ttu-id="cd558-132">There are several important things happening in this method.</span><span class="sxs-lookup"><span data-stu-id="cd558-132">There are several important things happening in this method.</span></span> <span data-ttu-id="cd558-133">First, we perform a check to see if the application has access to location data on the device.</span><span class="sxs-lookup"><span data-stu-id="cd558-133">First, we perform a check to see if the application has access to location data on the device.</span></span> <span data-ttu-id="cd558-134">We verify this by calling `LocationServicesEnabled` on the `CLLocationManager`.</span><span class="sxs-lookup"><span data-stu-id="cd558-134">We verify this by calling `LocationServicesEnabled` on the `CLLocationManager`.</span></span> <span data-ttu-id="cd558-135">This method will return **false** if the user has denied the application access to location information.</span><span class="sxs-lookup"><span data-stu-id="cd558-135">This method will return **false** if the user has denied the application access to location information.</span></span>

1. <span data-ttu-id="cd558-136">Next, tell the location manager how often to update.</span><span class="sxs-lookup"><span data-stu-id="cd558-136">Next, tell the location manager how often to update.</span></span> <span data-ttu-id="cd558-137">`CLLocationManager` provides many options for filtering and configuring location data, including the frequency of updates.</span><span class="sxs-lookup"><span data-stu-id="cd558-137">`CLLocationManager` provides many options for filtering and configuring location data, including the frequency of updates.</span></span> <span data-ttu-id="cd558-138">In this example, set the `DesiredAccuracy` to update whenever the location changes by a meter.</span><span class="sxs-lookup"><span data-stu-id="cd558-138">In this example, set the `DesiredAccuracy` to update whenever the location changes by a meter.</span></span> <span data-ttu-id="cd558-139">For more information on configuring location update frequency and other preferences, refer to the [CLLocationManager Class Reference](http://developer.apple.com/library/ios/#documentation/CoreLocation/Reference/CLLocationManager_Class/CLLocationManager/CLLocationManager.html) in the Apple documentation.</span><span class="sxs-lookup"><span data-stu-id="cd558-139">For more information on configuring location update frequency and other preferences, refer to the [CLLocationManager Class Reference](http://developer.apple.com/library/ios/#documentation/CoreLocation/Reference/CLLocationManager_Class/CLLocationManager/CLLocationManager.html) in the Apple documentation.</span></span>

1. <span data-ttu-id="cd558-140">Finally, call `StartUpdatingLocation` on the `CLLocationManager` instance.</span><span class="sxs-lookup"><span data-stu-id="cd558-140">Finally, call `StartUpdatingLocation` on the `CLLocationManager` instance.</span></span> <span data-ttu-id="cd558-141">This tells the location manager to get an initial fix on the current location, and to start sending updates</span><span class="sxs-lookup"><span data-stu-id="cd558-141">This tells the location manager to get an initial fix on the current location, and to start sending updates</span></span>

<span data-ttu-id="cd558-142">So far, the location manager has been created, configured with the kinds of data we want to receive, and has determined the initial location.</span><span class="sxs-lookup"><span data-stu-id="cd558-142">So far, the location manager has been created, configured with the kinds of data we want to receive, and has determined the initial location.</span></span> <span data-ttu-id="cd558-143">Now the code needs to render the location data to the user interface.</span><span class="sxs-lookup"><span data-stu-id="cd558-143">Now the code needs to render the location data to the user interface.</span></span> <span data-ttu-id="cd558-144">We can do this with a custom event that takes a `CLLocation` as an argument:</span><span class="sxs-lookup"><span data-stu-id="cd558-144">We can do this with a custom event that takes a `CLLocation` as an argument:</span></span>

```csharp
// event for the location changing
public event EventHandler<LocationUpdatedEventArgs>LocationUpdated = delegate { };
```

<span data-ttu-id="cd558-145">The next step is to subscribe to location updates from the `CLLocationManager`, and raise the custom `LocationUpdated` event when new location data becomes available, passing in the location as an argument.</span><span class="sxs-lookup"><span data-stu-id="cd558-145">The next step is to subscribe to location updates from the `CLLocationManager`, and raise the custom `LocationUpdated` event when new location data becomes available, passing in the location as an argument.</span></span> <span data-ttu-id="cd558-146">To do this, create a new class **LocationUpdateEventArgs.cs**.</span><span class="sxs-lookup"><span data-stu-id="cd558-146">To do this, create a new class **LocationUpdateEventArgs.cs**.</span></span> <span data-ttu-id="cd558-147">This code is accessible within the main application and returns the device location when the event is raised:</span><span class="sxs-lookup"><span data-stu-id="cd558-147">This code is accessible within the main application and returns the device location when the event is raised:</span></span>

```csharp
public class LocationUpdatedEventArgs : EventArgs
{
    CLLocation location;

    public LocationUpdatedEventArgs(CLLocation location)
    {
       this.location = location;
    }

    public CLLocation Location
    {
       get { return location; }
    }
}
```

## <a name="user-interface"></a><span data-ttu-id="cd558-148">User Interface</span><span class="sxs-lookup"><span data-stu-id="cd558-148">User Interface</span></span>

1. <span data-ttu-id="cd558-149">Use the iOS designer to build the screen that will display location information.</span><span class="sxs-lookup"><span data-stu-id="cd558-149">Use the iOS designer to build the screen that will display location information.</span></span> <span data-ttu-id="cd558-150">Double-click on the **Main.storyboard** file to begin.</span><span class="sxs-lookup"><span data-stu-id="cd558-150">Double-click on the **Main.storyboard** file to begin.</span></span>

    <span data-ttu-id="cd558-151">On the storyboard, drag several labels onto the screen to act as placeholders for the location information.</span><span class="sxs-lookup"><span data-stu-id="cd558-151">On the storyboard, drag several labels onto the screen to act as placeholders for the location information.</span></span> <span data-ttu-id="cd558-152">In this example, there are labels for latitude, longitude, altitude, course, and speed.</span><span class="sxs-lookup"><span data-stu-id="cd558-152">In this example, there are labels for latitude, longitude, altitude, course, and speed.</span></span>

    <span data-ttu-id="cd558-153">The layout should resemble the following:</span><span class="sxs-lookup"><span data-stu-id="cd558-153">The layout should resemble the following:</span></span>

    <span data-ttu-id="cd558-154">![](location-walkthrough-images/image8.png "An example UI layout in the iOS Designer")</span><span class="sxs-lookup"><span data-stu-id="cd558-154">![](location-walkthrough-images/image8.png "An example UI layout in the iOS Designer")</span></span>

1. <span data-ttu-id="cd558-155">In the Solution Pad, double-click the `ViewController.cs` file and edit it to create a new instance of the LocationManager and call `StartLocationUpdates`on it.</span><span class="sxs-lookup"><span data-stu-id="cd558-155">In the Solution Pad, double-click the `ViewController.cs` file and edit it to create a new instance of the LocationManager and call `StartLocationUpdates`on it.</span></span>
  <span data-ttu-id="cd558-156">Change the code to look like the following:</span><span class="sxs-lookup"><span data-stu-id="cd558-156">Change the code to look like the following:</span></span>

    ```csharp
    #region Computed Properties
    public static bool UserInterfaceIdiomIsPhone {
                get { return UIDevice.CurrentDevice.UserInterfaceIdiom == UIUserInterfaceIdiom.Phone; }
            }

    public static LocationManager Manager { get; set;}
    #endregion

    #region Constructors
    public ViewController (IntPtr handle) : base (handle)
    {
    // As soon as the app is done launching, begin generating location updates in the location manager
        Manager = new LocationManager();
        Manager.StartLocationUpdates();
    }

    #endregion
    ```

    <span data-ttu-id="cd558-157">This will start the location updates on application start-up, although no data will be displayed.</span><span class="sxs-lookup"><span data-stu-id="cd558-157">This will start the location updates on application start-up, although no data will be displayed.</span></span>

1. <span data-ttu-id="cd558-158">Now that the location updates are received, update the screen with the location information.</span><span class="sxs-lookup"><span data-stu-id="cd558-158">Now that the location updates are received, update the screen with the location information.</span></span> <span data-ttu-id="cd558-159">The following method gets the location from our `LocationUpdated` event and shows it in the UI:</span><span class="sxs-lookup"><span data-stu-id="cd558-159">The following method gets the location from our `LocationUpdated` event and shows it in the UI:</span></span>

    ```csharp
    #region Public Methods
    public void HandleLocationChanged (object sender, LocationUpdatedEventArgs e)
    {
        // Handle foreground updates
        CLLocation location = e.Location;

        LblAltitude.Text = location.Altitude + " meters";
        LblLongitude.Text = location.Coordinate.Longitude.ToString ();
        LblLatitude.Text = location.Coordinate.Latitude.ToString ();
        LblCourse.Text = location.Course.ToString ();
        LblSpeed.Text = location.Speed.ToString ();

        Console.WriteLine ("foreground updated");
    }
    #endregion
    ```

<span data-ttu-id="cd558-160">We still need to subscribe to the `LocationUpdated` event in our AppDelegate, and call the new method to update the UI.</span><span class="sxs-lookup"><span data-stu-id="cd558-160">We still need to subscribe to the `LocationUpdated` event in our AppDelegate, and call the new method to update the UI.</span></span> <span data-ttu-id="cd558-161">Add the following code in `ViewDidLoad,` right after the `StartLocationUpdates` call:</span><span class="sxs-lookup"><span data-stu-id="cd558-161">Add the following code in `ViewDidLoad,` right after the `StartLocationUpdates` call:</span></span>

```csharp
public override void ViewDidLoad ()
{
    base.ViewDidLoad ();

    // It is better to handle this with notifications, so that the UI updates
    // resume when the application re-enters the foreground!
    Manager.LocationUpdated += HandleLocationChanged;

}
```


<span data-ttu-id="cd558-162">Now, when the application is run, it should look something like this:</span><span class="sxs-lookup"><span data-stu-id="cd558-162">Now, when the application is run, it should look something like this:</span></span>

<span data-ttu-id="cd558-163">[![](location-walkthrough-images/image5.png "An example app run")](location-walkthrough-images/image5.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="cd558-163">[![](location-walkthrough-images/image5.png "An example app run")](location-walkthrough-images/image5.png#lightbox)</span></span>

## <a name="handling-active-and-background-states"></a><span data-ttu-id="cd558-164">Handling Active and Background states</span><span class="sxs-lookup"><span data-stu-id="cd558-164">Handling Active and Background states</span></span>

1. <span data-ttu-id="cd558-165">The application is outputting location updates while it is in the foreground and active.</span><span class="sxs-lookup"><span data-stu-id="cd558-165">The application is outputting location updates while it is in the foreground and active.</span></span> <span data-ttu-id="cd558-166">To demonstrate what happens when the app enters the background, override the `AppDelegate` methods that track application state changes so that the application writes to the console when it transitions between the foreground and the background:</span><span class="sxs-lookup"><span data-stu-id="cd558-166">To demonstrate what happens when the app enters the background, override the `AppDelegate` methods that track application state changes so that the application writes to the console when it transitions between the foreground and the background:</span></span>

    ```csharp
    public override void DidEnterBackground (UIApplication application)
    {
        Console.WriteLine ("App entering background state.");
    }

    public override void WillEnterForeground (UIApplication application)
    {
        Console.WriteLine ("App will enter foreground");
    }
    ```

    <span data-ttu-id="cd558-167">Add the following code in the `LocationManager` to continuously print updated location data to the application output, to verify the location information is still available in the background:</span><span class="sxs-lookup"><span data-stu-id="cd558-167">Add the following code in the `LocationManager` to continuously print updated location data to the application output, to verify the location information is still available in the background:</span></span>

    ```csharp
    public class LocationManager
    {
        public LocationManager ()
        {
        ...
        LocationUpdated += PrintLocation;
        }
        ...

        //This will keep going in the background and the foreground
        public void PrintLocation (object sender, LocationUpdatedEventArgs e) {
        CLLocation location = e.Location;
        Console.WriteLine ("Altitude: " + location.Altitude + " meters");
        Console.WriteLine ("Longitude: " + location.Coordinate.Longitude);
        Console.WriteLine ("Latitude: " + location.Coordinate.Latitude);
        Console.WriteLine ("Course: " + location.Course);
        Console.WriteLine ("Speed: " + location.Speed);
        }
    }
    ```

1. <span data-ttu-id="cd558-168">There is one remaining issue with the code: attempting to update the UI when the app is backgrounded will cause iOS will terminate it.</span><span class="sxs-lookup"><span data-stu-id="cd558-168">There is one remaining issue with the code: attempting to update the UI when the app is backgrounded will cause iOS will terminate it.</span></span> <span data-ttu-id="cd558-169">When the app goes into the background, the code needs to unsubscribe from location updates and stop updating the UI.</span><span class="sxs-lookup"><span data-stu-id="cd558-169">When the app goes into the background, the code needs to unsubscribe from location updates and stop updating the UI.</span></span>

    <span data-ttu-id="cd558-170">iOS provides us notifications when the app is about to transition to a different application states.</span><span class="sxs-lookup"><span data-stu-id="cd558-170">iOS provides us notifications when the app is about to transition to a different application states.</span></span> <span data-ttu-id="cd558-171">In this case, we can subscribe to the `ObserveDidEnterBackground` Notification.</span><span class="sxs-lookup"><span data-stu-id="cd558-171">In this case, we can subscribe to the `ObserveDidEnterBackground` Notification.</span></span>

    <span data-ttu-id="cd558-172">The following code snippet shows how to use a notification to let the view know when to halt UI updates.</span><span class="sxs-lookup"><span data-stu-id="cd558-172">The following code snippet shows how to use a notification to let the view know when to halt UI updates.</span></span> <span data-ttu-id="cd558-173">This will go in `ViewDidLoad`:</span><span class="sxs-lookup"><span data-stu-id="cd558-173">This will go in `ViewDidLoad`:</span></span>

    ```csharp
    UIApplication.Notifications.ObserveDidEnterBackground ((sender, args) => {
        Manager.LocationUpdated -= HandleLocationChanged;
    });
    ```

    <span data-ttu-id="cd558-174">When the app is running, the output will look something like this:</span><span class="sxs-lookup"><span data-stu-id="cd558-174">When the app is running, the output will look something like this:</span></span>

    <span data-ttu-id="cd558-175">![](location-walkthrough-images/image6.png "Example of the location output in the console")</span><span class="sxs-lookup"><span data-stu-id="cd558-175">![](location-walkthrough-images/image6.png "Example of the location output in the console")</span></span>

1. <span data-ttu-id="cd558-176">The application prints location updates to the screen when operating in the foreground, and continues to print data to the application output window while operating in the background.</span><span class="sxs-lookup"><span data-stu-id="cd558-176">The application prints location updates to the screen when operating in the foreground, and continues to print data to the application output window while operating in the background.</span></span>

<span data-ttu-id="cd558-177">Only one outstanding issue remains: the screen starts UI updates when the app is first loaded, but it has no way of knowing when the app has re-entered the foreground.</span><span class="sxs-lookup"><span data-stu-id="cd558-177">Only one outstanding issue remains: the screen starts UI updates when the app is first loaded, but it has no way of knowing when the app has re-entered the foreground.</span></span> <span data-ttu-id="cd558-178">If the backgrounded application is brought back into the foreground, UI updates won’t resume.</span><span class="sxs-lookup"><span data-stu-id="cd558-178">If the backgrounded application is brought back into the foreground, UI updates won’t resume.</span></span>

<span data-ttu-id="cd558-179">To fix this, nest a call to start UI updates inside another Notification, which will fire when the application enters the Active state:</span><span class="sxs-lookup"><span data-stu-id="cd558-179">To fix this, nest a call to start UI updates inside another Notification, which will fire when the application enters the Active state:</span></span>

```csharp
UIApplication.Notifications.ObserveDidBecomeActive ((sender, args) => {
  Manager.LocationUpdated += HandleLocationChanged;
});
```

<span data-ttu-id="cd558-180">Now the UI will begin updating when the application is first started, and resume updating any time the app comes back into the foreground.</span><span class="sxs-lookup"><span data-stu-id="cd558-180">Now the UI will begin updating when the application is first started, and resume updating any time the app comes back into the foreground.</span></span>

<span data-ttu-id="cd558-181">In this walkthrough, we built a well-behaved, background-aware iOS application that prints location data to both the screen and the application output window.</span><span class="sxs-lookup"><span data-stu-id="cd558-181">In this walkthrough, we built a well-behaved, background-aware iOS application that prints location data to both the screen and the application output window.</span></span>


## <a name="related-links"></a><span data-ttu-id="cd558-182">Related Links</span><span class="sxs-lookup"><span data-stu-id="cd558-182">Related Links</span></span>

- [<span data-ttu-id="cd558-183">Location (Part 4) (sample)</span><span class="sxs-lookup"><span data-stu-id="cd558-183">Location (Part 4) (sample)</span></span>](https://developer.xamarin.com/samples/monotouch/Location/)
- [<span data-ttu-id="cd558-184">Core Location Framework Reference</span><span class="sxs-lookup"><span data-stu-id="cd558-184">Core Location Framework Reference</span></span>](https://developer.apple.com/library/ios/documentation/CoreLocation/Reference/CoreLocation_Framework/_index.html)
