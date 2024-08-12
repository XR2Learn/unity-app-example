# XR2Learn Unity App Example (Integration Personalization Enablers and Unity Applications)

This is an example app of how to communicate a Unity Application with Personalization Enablers.
Personalization Enablers and Unity application to communicate by exchanging messages using Pub/Sub protocol.

Redis is used as a message broker for the message exchange. Thus, this example includes:

- Code to connect to Redis in Unity,
- Code to create a publisher and a subscriber in Unity
- Code with the sending and receiving message formats to communicate with the Personalization Enablers.

This example app includes a simple graphic interface as depicted below.

![Screenshot](screen-test.png?raw=true)
(Screenshot of the Unity application)

## Installing Redis Lib

### Installing NuGets in Unity

*[Docs on installation](https://github.com/GlitchEnzo/NuGetForUnity?tab=readme-ov-file#unity-20193-or-newer)*

### Overview install instructions:

In the project, go to `Window->Package Manager->[+]->Add Package From git URL`.

and paste the url for the NuGetForUnity: `https://github.com/GlitchEnzo/NuGetForUnity.git?path=/src/NuGetForUnity`

### Install NRedisStack NuGets

Go to `NuGet For Unity->Online (tab)` and search for `NRedisStack`. Select this package and click
in `Install All Selected`.

## Redis Connection

The `UIExample.cs` script contains a script with a simple example of how to connect with Redis as both a publisher and
subscriber and how to translate the Redis messages into Unity internal variables.

### Important Point

Running complex unity code in the method used for handling the subscribed Redis messages can be complicated to debug in
Unity (i.e. `ProcessMessageNextActivityLevel` in the `UIExample.cs`). It is best for the methods that handle the
subscribed messages to only update primitive variables and have the `update` or other standard Unity method update more
complex components based on the primitive variables just populated.

## Running the App

- Set the Redis connection string to the `ip:port` where the Redis instance is running.

- Then click on `Connect`.
- Select `User Level` and `Activity Level`
- Click on `Start Activity` to publish the message that will start an activity
- Click on `Stop activity` to publish the message that will stop the current activity
- You will be able to see the Next suggested activity level on the Dropdown to the right.
- Clicking on `Disconnect` will end the connection to the Redis instance.

## Builds

We are making available a compiled build that you can download and run to see this example functionalities.

- [Builds Link](https://drive.google.com/drive/folders/1y3j8F7yACtt1lwrk7ARYgFjxEEVgG4f6?usp=drive_link) (Currently
  Linux x86_64 architecture)

## Message Formats
####  Unity as publisher:

**Channel**: `start_activity`

**Message**: 
    `{
        'id': id_activity, 
        'user_level': user_level,
        'activity_level': activity_level
    }`
---

**Channel**: `stop_activity`

**Message**: 
    `{
        'id': 0,
        'timestamp': Date.now()
        }`

---
#### Unity as subscriber:

**Channel**: `next_activity_level`

**Message**: 
      `{
        'id': id_previous_activity,
        'next_activity_level': next_activity_level (int values, 0, 1 or 2)
        }`

## License

Copyright © 2024, Maastricht University

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
