# Sensor > Node > Gateway > TTN > Database/Server > Webapp
This intro provides all the information neccessary to enable your self assembled node reading sensory data, sending it to The Things Network via an existing gateway and making sense of the data you'll see in the TTN console.
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

## Future Steps
We won't stop here. For us this prototype means there is even more cool work ahead of us. We will give talks, host workshops and develop prototypes of real life applications, in order to start discussions of meaning and possibilities of the LoRaWAN Technology. We believe this little boost in the IoT technology sector hides a great potential that can be used by a wide range of people and businesses.


## Authors
- https://twitter.com/bnjmnsbl 
- https://twitter.com/sebimweb

## License
**The MIT License**

Copyright 2017 Technologiestiftung Berlin

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## Acknowledgments
Matthijs Kooijman (Providing the LMIC Library)
https://github.com/matthijskooijman

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
