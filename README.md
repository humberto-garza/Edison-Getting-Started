# Edison Getting Started (Windows)
It is important to mention that this board works without problems in a Linux Environment as well; but this tutorial focuses in Windows.  

First of all, you will need to get some drivers installed so you don't have any issues. 
> Do this **BEFORE** you plug your board in!

#### SETUP
> - Go to [This](https://software.intel.com/en-us/iot/hardware/edison/downloads) page and get the **[Driver Software](http://downloadmirror.intel.com/24909/eng/IntelEdisonDriverSetup1.2.1.exe)**. It is the file: **IntelEdisonDriverSetup1.2.1.exe**
> Follow These Steps: <br/>
> ![alt tag](Diagrams/1.PNG) <br/>
----------
> ![alt tag](Diagrams/2.PNG) <br/>
----------
> ![alt tag](Diagrams/3.PNG) <br/>
----------
> ![alt tag](Diagrams/4.PNG) <br/>
----------
> ![alt tag](Diagrams/5.PNG) <br/>
----------

> - Download the **[CDM FTDI Driver](http://www.ftdichip.com/Drivers/CDM/CDM%20v2.10.00%20WHQL%20Certified.exe)** 
> Follow These Steps: <br/>
> ![alt tag](Diagrams/6.PNG) <br/>
----------
> ![alt tag](Diagrams/7.PNG) <br/>
----------

> - Connect Both USB Cables to The Board
> - Open Windows **Device Manager**
> - Under **Ports (COM & LPT)** you should see the COM of your EDISON
> If you cannot see the Proper COM as in the last picture try the following: <br/>
> ![alt tag](Diagrams/8.PNG) <br/>
----------
> ![alt tag](Diagrams/9.PNG) <br/>
----------
> ![alt tag](Diagrams/10.PNG) <br/>
----------
> ![alt tag](Diagrams/11.PNG) <br/>
----------
> ![alt tag](Diagrams/12.PNG) <br/>
----------
> ![alt tag](Diagrams/13.PNG) <br/>
----------

> - Under **Network Adapters** you should see the Intel Edison **RNDIS** Adapter
> If you cannot see the Proper COM as in the last picture try the following: <br/>
> ![alt tag](Diagrams/14.PNG) <br/>
----------
> ![alt tag](Diagrams/15.PNG) <br/>
----------
> ![alt tag](Diagrams/16.PNG) <br/>
----------
> ![alt tag](Diagrams/17.PNG) <br/>
----------
> ![alt tag](Diagrams/18.PNG) <br/>
----------


#### Flash New Image
When working with the Edison, you may find convenient knowing a way to completely flash the Board:

> - Download the [Phone Flash Tool Lite For Windows](https://01.org/android-ia/downloads/intel-phone-flash-tool-lite):<br/>

> - Download [Zadig](http://zadig.akeo.ie/downloads/):<br/>

> - Reboot your Computer<br/>

> - Open Zadig<br/>

> - **Options>List all Drivers**<br/>

> - Select **RNDIS (Interface 0)** and Replace Driver to **libusbK (v3.0.7.0)**<br/>

> ![alt tag](Diagrams/a.PNG) <br/>
----------

> - Download the [Latest Board Firmware Version](https://software.intel.com/en-us/iot/hardware/edison/downloads) (Release 2.1 Yocto* complete image):<br/>

> - Unzip The file To any Folder with no spaces that you wish:<br/>

> - CD to that folder and execute **flashall** and follow the instructions in the screen (this may take up to 15 minutes, be patient):<br/>

> ![alt tag](Diagrams/b.PNG) <br/>
----------

> -When it is over, make sure you **leave it connected** for at least **2 minutes** so it reboots properly:<br/>

#### Serial Connection
> - Open Putty, under the serial Connection Write the **COM** That was assigned to the edison FTDI adapter. We must use the **USB Serial PORT**; not the **Virtual COM Port** since this is the one that the Arduino IDE uses. The BAUD is **115200** 
>Reference: <br/>
> ![alt tag](Diagrams/19.PNG) <br/>
----------

> - Edison login: **root** 
> - Now you can have access to the Linux Yocto OS

#### SSH Connection (RNDIS)
> - Open Network and Sharing Center<br/>
> ![alt tag](Diagrams/20.PNG) <br/>
----------

> - Change adapter settings<br/>
> ![alt tag](Diagrams/21.PNG) <br/>
----------

> - If Disabled, **Enable** the RNDIS Network Adapter<br/>
> ![alt tag](Diagrams/22.PNG) <br/>
----------

> - Go To The Adapter Properties and double click the **Internet Protocol Version 4 (TCP/IPv4)** option<br/>
> ![alt tag](Diagrams/23.PNG) <br/>
----------

> -  Use These parameters for the **Static IPv4** Address and click OK<br/>
> ![alt tag](Diagrams/24.PNG) <br/>
----------

> -  Go to Putty and Select SSH Configuration using these Parameters<br/>
> ![alt tag](Diagrams/25.PNG) <br/>
----------

> -  Click YES<br/>
> ![alt tag](Diagrams/26.PNG) <br/>
----------

> - Edison login: **root** 
> - Now you can have access to the Linux Yocto OS

#### SSH File Explorer
> - Download [WinSCP](https://winscp.net/eng/download.php)
> - Open WinSCP and add a New Site with these Parameters (If your Edison has no password, leave that field blank)<br/>
> ![alt tag](Diagrams/27.PNG) <br/>
----------

> - Add This Key to WinSCP<br/>
> ![alt tag](Diagrams/28.PNG) <br/>
----------

> - You Should now have access to the Files with GUI<br/>
> ![alt tag](Diagrams/29.PNG) <br/>
----------

#### Android/Windows - Wifi SSH 

> - Download the App JuiceSSH
> - Configure The Edison Name and Password. I suggest you only change to password to **password**
```
configure_edison --setup
```

> - Start AP Mode. The Second command is to stop that service
```
systemctl start hostapd
systemctl stop hostapd
```

> Because the Broadcom module does not support STA/AP concurrently, hostapd and wpa_supplicant
cannot run simultaneously. Use the following commands to start/stop wpa_supplicant manually: 
```
systemctl start wpa_supplicant
systemctl stop wpa_supplicant
```

> - Scan with yout Phone (or computer) for WIFI
> - It should be called Something like EDISON:XX:XX
> - The password is the same one as assigned in step **2**

> In case you want to know the default wifi password before you set it up you must use your Edison Serial number, and it should be something like this: **FZED443D01RNZ501**. This can be found in the Box or:
```
cat /etc/hostapd/hostapd.conf | grep wpa_passphrase
```

> - Now you need to know the Edison IP to access by SSH
```
ifconfig
```

> ![alt tag](Diagrams/30.PNG) <br/>
----------

> - Open JuiceSSH and connect like this:

> ![alt tag](Diagrams/31.PNG) <br/>
----------

> Instead of using JuiceSSH you can just use Putty in Windows

> - You can as well access the archives with a GUI in Android. Donwload **File Explorer** App
> - Follow These Steps:<br/>

> ![alt tag](Diagrams/32.PNG) <br/>
----------

#### Interact with Serial 2
As you should know, the Edison's **SERIAL2** is actually the **Linux Serial terminal**; it is connected to the uUSB connector with an FTDI chip, so if you are planning in using the SERIAL2, things might get a bit complicated. I will explain how can you achieve such connection and get the right communication noise free!<br/>
Just as a FYI, you should know how to change the BAUD of any Serial /dev/<br/>

```
stty -F /dev/ttyMFD1 [baud]
```

> - Connect both uUSB cables to your computer. <br/>
> - Connect the Edison through COM and SSH in 2 Putty sessions<br/>

> ![alt tag](Diagrams/33.PNG) <br/>
----------

> - Type these Commands in the SSH Session (it has to be in the SSH session because once the first command is executed, the terminal will be disabled and you will not be able to input the second one):
```
systemctl stop serial-getty@ttyMFD2.service
dmesg -n 1
```

> - Test your connection with an echo, you should see something like this (rememebr that the serial2 is in **/dev/ttyMFD2**):
```
echo Hello World > /dev/ttyMFD2
```

> ![alt tag](Diagrams/34.PNG) <br/>
----------

> - Test the connection from the Device to the Edison:<br/>

> ![alt tag](Diagrams/35.PNG) <br/>
----------

#### Intel Analytics Platform
IoT Analytics includes resources for the collection and analysis of sensor data that the Intel® IoT Developer Kit provides without having to invest in large-scale storage and processing capacity. While it is possible to store sensor values directly on an Intel® Edison board, IoT Analytics is the preferred, convenient location for storing sensor values for safekeeping and future manipulation.<br/>
> - Connect your Edison to Internet:<br/>
```
configure_edison --wifi
```

> - Make a ping to test your connection:<br/>

> ![alt tag](Diagrams/36.PNG) <br/>
----------

There are certain commands to interact with the platform:<br/>
> - Make sure that you hace the appropriate version >= **1.7.0**<br/>
```
iotkit-admin version  
```

> - If you do **not** have this version try these commands to update your toolset:<br/>
```
npm install -g npm
npm install iotkit-agent
npm install mraa
npm update -g iotkit-agent 
```

> - First you hace to test it works<br/>
```
iotkit-admin test
```

> - If you are having issues with this, try these commands:<br/>
```
iotkit-admin reset-code
iotkit-admin reset-components
iotkit-admin initialize
```

When you Register your device in the Platform, it will "belong" to the account that registered it. So if you want to register it in a new account but you did not remove it from the previous account, it will say it is not available. In order to avoid that, you can choose the ID for your device.<br/>

> - Choose a new ID fot your Device in this format **XX-XX-XX-XX-XX-XX-XX**. **If you are the owner of this Edison you can skip this step**, if you are **sharing it** you may do this for good. (I recommend you split your phone number to make it fit there and make sure it cannot be repeated by other users in the world); the second command will return the ID and make sure it was accepted:<br/>
```
iotkit-admin set-device-id XX-XX-XX-XX-XX-XX-XX
iotkit-admin device-id
```

> - Go to [IoT Analytics Platform](enableiot.com) and create an account:<br/>

> ![alt tag](Diagrams/37.PNG) <br/>
----------

> - Once you did this, go to: **menu>Devices>Add a New Device**:<br/>

> ![alt tag](Diagrams/38.PNG) <br/>
----------

> - Go to: **menu>Account>Activation Code**:<br/>

> ![alt tag](Diagrams/39.PNG) <br/>
----------

> - Activate your Device with the Code you just got:<br/>
```
iotkit-admin activate [activation_code]
```

> - By Default your new account hase some sensors registered, you can check them out like this:<br/>
```
iotkit-admin catalog
```

> ![alt tag](Diagrams/40.PNG) <br/>
----------

> - For this test, we will try the temperature one and add the powerswitch as well:<br/>
```
iotkit-admin register temperature temperature.v1.0
```

> - Make sure the register was successful, you should see something like this:<br/>
```
iotkit-admin components
```

> ![alt tag](Diagrams/41.PNG) <br/>
----------

> - Set the Communication protocol to mqtt and start the service :<br/>
```
iotkit-admin protocol mqtt
systemctl start iotkit-agent
```

> - Test sending sensor data to the cloud:<br/>
```
iotkit-admin observation temperature 40
```

> ![alt tag](Diagrams/42.PNG) <br/>
----------

> - Go to the Platform **menu>charts** Select your device and you should see in the graph the 40 degrees we just sent:<br/>

> ![alt tag](Diagrams/43.PNG) <br/>
----------

You can go further and control your board with this platform <br/>
> - We will test this in Arduino To Make Sure it all works, and understand the program flow. Download the [Library](https://github.com/enableiot/iotkit-samples/raw/master/arduino/IoTkit.zip) and add it to your [Intel Arduino IDE](https://software.intel.com/en-us/iot/hardware/edison/downloads)<br/>

> - You should see the examples in your IDE Like this <br/>

> ![alt tag](Diagrams/44.PNG) <br/>
----------

> - Register the Powerswitch and test it:<br/>
```
$ iotkit-admin register power powerswitch.v1.0
$ iotkit-admin observation power 1
```

Make sure that there is no other process “listening” to the port UDP41235 or UDP41234 before you run it (kill -9 if necessary)<br/>

> - Leave running the **IoTKitActuationExample.ino**<br/>

> - Go to **menu>control**, select your device, select **power** component and follow these steps:<br/>

> ![alt tag](Diagrams/45.PNG) <br/>
----------

> - See the message in the Arduino **serial monitor**<br/>

To Go even further you can explore the platform rules!<br/>

> - Go to **menu>control** and instead of sending all valid actions, save them as complex command <br/>

> ![alt tag](Diagrams/46.PNG) <br/>
----------

> - Go to **menu>rules>Add a Rule**, The Priority will not modify the behavior of the actuation; this just helps the sorting<br/>

> ![alt tag](Diagrams/47.PNG) <br/>
----------

> ![alt tag](Diagrams/48.PNG) <br/>
----------

> ![alt tag](Diagrams/49.PNG) <br/>
----------

> - When a rule's condition is met, you can see it in your dashboard. Remember you are responsible for the code that listens to the platform's notifications<br/>

> ![alt tag](Diagrams/50.PNG) <br/>
----------

####Configure your MCU launching service to run scripts automatically 
Doing this with the new Yocto Image is quite simple, all you have to do is follow these instructions this was taken from the official [Intel Edison MCU Setup guide](https://software.intel.com/en-us/node/545143):<br/>

Just as a FYI, you should know how to keep the WiFi up even after reboot so it will reconnect automatically /dev/<br/>

```
systemctl start connman
systemctl enable wpa_supplicant
systemctl start wpa_supplicant
#In this file you can see the WiFi configuration:
vi /etc/wpa_supplicant/wpa_supplicant.conf 
``
`
> - In a serial communication session with your board, open the mcu_fw_loader.sh file using a text editor such as vi.<br/>

```
vi /etc/intel_mcu/mcu_fw_loader.sh
```

For each script that you want to run, type /folderpath/scriptname.sh, where folderpath is the location where the script is stored and scriptname is the name of the script, as shown in the example below. Each script should be on its own line. Be sure to include any required arguments for running the script.
For example, the following file is configured to run **init_i2c8.sh** and **init_DIG.sh**:<br/>

> ![alt tag](Diagrams/51.PNG) <br/>
----------

#### MCU SDK
In order to get the MCU to work, you can follow this [guide](https://software.intel.com/en-us/node/545143)
