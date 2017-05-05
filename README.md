# Sensor > Node > Gateway > TTN > Database/Server > Webapp
This intro provides all the information necessary to enable your self assembled node reading sensory data, sending it to The Things Network via an existing gateway and making sense of the data you'll see in the TTN console.
## Pre-requisites
#### (the provided code was tested only with this particular hardware/softwarelibrary combination)

1. Arduino Uno
2. Dragino LoRa GPS Shield + Dragino LoRa Bee
2. USB cable
3. Updated IDE (Arduino, Atom, ..)
4. basic understanding of what Arduino is and does
3. Sensors, jumpers and optional breadboard (in this case we're using a proximity sensor, 9v battery)
4. Computer running Windows 7 or higher, Mac OS X or Linux
5. A running TTN Gateway with full online access to its console

## Installing the libraries

In order to use the **sendingecho.ino** you'll need the following libraries:

 #include <TheThingsNetwork.h> [link to ttn lib] (communication with ttn)

 #include <NewPing.h> [link to NewPing lib] (using the ultrasound sensor)

 #include <lmic.h> [link to lmic lib] (using LoRaWAN radio communication)

 #include <hal/hal.h> [link to HAL lib] (extends the arduino IDE in order to interfacing with additional hardware)


    > On Windows, you might need to [install drivers](https://www.arduino.cc/en/Guide/ArduinoLeonardoMicro#toc2).

## Testing the sensor

It's important to make sure that our setup is actually reading sensory data. For testing purposes you can use the NewPing Library example called **NewPingExample** and watch what happens in the monitor. Make sure the pin connections match the Example.

## >> All the Next Steps <<

follow the next steps in [Creating a TTN Node]. Please note the following custom steps to make this use cases work.

## Payload Function
In order to make sense of the data we recommend changing the Payload Function in ""Decoding" to:

    function Decoder(bytes) {
    var decodedValue = (bytes[0]<<8) | bytes[1];
    return {
    value: decodedValue,
    };
    }

## Node.js Server for web API
This guide will walk you through setting up a Node.js project that listens to device activations and messages and responds to every 3rd message.

[Link to Node.js Server Setup]

[Link to our Node.js backend implementation]

## Web Applications
Take the data and go crazy! Have a look at our first [frontend prototype]

## Future Steps
We won't stop here. For us this prototype means there is even more cool work ahead of us. We will give talks, host workshops and develop prototypes of real life applications, in order to start discussions of meaning and possibilities of the LoRaWAN Technology. We believe this little boost in the IoT technology sector hides a great potential that can be used by a wide range of people and businesses.


## Authors
- https://twitter.com/bnjmnsbl
- https://twitter.com/sebimweb

## License
**The MIT License**

Copyright 2017 Technologiestiftung Berlin

This project is licensed under the MIT License

## Acknowledgments
Matthijs Kooijman (Providing the LMIC Library)
https://github.com/matthijskooijman

[Link to Node.js Server Setup]: https://www.thethingsnetwork.org/docs/applications/nodejs/quick-start.html
[frontend prototype]: https://github.com/technologiestiftung/LoRaWAN-Frontend
[Link to our Node.js backend implementation]: https://github.com/technologiestiftung/LoRaWAN-Server
[Creating a TTN Node]:	https://www.thethingsnetwork.org/docs/devices/uno/quick-start.html
[link to HAL lib]: http://playground.arduino.cc/Code/HardwareAbstraction
[link to lmic lib]:	https://github.com/matthijskooijman/arduino-lmic
[link to NewPing lib]:	http://playground.arduino.cc/Code/NewPing
[link to ttn lib]:	https://github.com/TheThingsNetwork/arduino-device-lib
[account]:         https://account.thethingsnetwork.org
[create-account]:  https://account.thethingsnetwork.org/register
[profile]:         https://account.thethingsnetwork.org/users/profile
[console]:         https://console.thethingsnetwork.org
[settings]:        https://console.thethingsnetwork.org/settings
[add-application]: https://console.thethingsnetwork.org/applications/add
