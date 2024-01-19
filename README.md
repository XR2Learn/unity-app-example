# XR2Learn Unity App Example
This is an example app of how to connect to Redis in Unity (to connect Beacon Apps to Enablers).

![Screenshot](https://github.com/um-xr2learn-enablers/XR2Learn-Unity-App-Example/blob/master/screen-test.png?raw=true)
(Screenshot of the Unity application)

![Screenshot](https://github.com/um-xr2learn-enablers/XR2Learn-Unity-App-Example/blob/master/screen-test.png?raw=true)
(Screenshot)

# Installing Redis Lib
## Installing NuGets in Unity
*[Docs on installation](https://github.com/GlitchEnzo/NuGetForUnity?tab=readme-ov-file#unity-20193-or-newer)*

## Overview install instructions:

In the project, go to `Window->Package Manager->[+]->Add Package From git URL`.

and paste the url for the NuGetForUnity: `https://github.com/GlitchEnzo/NuGetForUnity.git?path=/src/NuGetForUnity`

## Install NRedisStack NuGets
Go to `NuGet For Unity->Online (tab)` and search for `NRedisStack`. Select this package and click in `Install All Selected`.

# Redis Connection
The `UIExample.cs` script contains a script with a simple example of how to connect with Redis as both a publisher and subscriber and how to translate the Redis messages into Unity internal variables.

## Important Point
Running complex unity code in the method used for handling the subscribed Redis messages can be complicated to debug in Unity (i.e. `ProcessMessageNextActivityLevel` in the `UIExample.cs`). It is best for the methods that handle the subscribed messages to only update primitive variables and have the `update` or other standard Unity method update more complex components based on the primitive variables just populated.


# Running the App
 - Set the Redis connection string to the `ip:port` where the Redis instance is running.

 - Then click on `Connect`.
 - Select `User Level` and `Activity Level`
 - Click on `Start Activity` to publish the message that will start an activity
 - Click on `Stop activity` to publish the message that will stop the current activity
 - You will be able to see the Next suggested activity level on the Dropdown to the right.
 - Clicking on `Disconnect` will end the connection to the Redis instance.

# Builds
- [Build Links](https://drive.google.com/drive/folders/1y3j8F7yACtt1lwrk7ARYgFjxEEVgG4f6?usp=drive_link)
