# Edison Getting Started (Windows)
It is important to mention that this board works without problems in a Linux Environment as well; but this tutorial focuses in Windows.  

First of all, you will need to get some drivers installed so you don't have any issues. 
> Do this **BEFORE** you plug your board in!

#### SETUP
1. Go to [This](https://software.intel.com/en-us/iot/hardware/edison/downloads) page and get the **[Driver Software](http://downloadmirror.intel.com/24909/eng/IntelEdisonDriverSetup1.2.1.exe)**. It is the file: **IntelEdisonDriverSetup1.2.1.exe**
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

2. Download the **[CDM FTDI Driver](http://www.ftdichip.com/Drivers/CDM/CDM%20v2.10.00%20WHQL%20Certified.exe)** 
> Follow These Steps: <br/>
> ![alt tag](Diagrams/6.PNG) <br/>
----------
> ![alt tag](Diagrams/7.PNG) <br/>
----------

3. Connect Both USB Cables to The Board
4. Open Windows **Device Manager**
5. Under **Ports (COM & LPT)** you should see the COM of your EDISON
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

6. Under **Network Adapters** you should see the Intel Edison **RNDIS** Adapter
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

#### Serial Connection
1. Open Putty, under the serial Connection Write the **COM** That was assigned to the edison FTDI adapter. We must use the **USB Serial PORT**; not the **Virtual COM Port** since this is the one that the Arduino IDE uses. The BAUD is **115200** 
>Reference: <br/>
> ![alt tag](Diagrams/19.PNG) <br/>
----------

2. Edison login: **root** 
3. Now you can have access to the Linux Yocto OS

#### SSH Connection (RNDIS)
1. Open Network and Sharing Center<br/>
> ![alt tag](Diagrams/20.PNG) <br/>
----------

2. Change adapter settings<br/>
> ![alt tag](Diagrams/21.PNG) <br/>
----------

3. If Disabled, **Enable** the RNDIS Network Adapter<br/>
> ![alt tag](Diagrams/22.PNG) <br/>
----------

4. Go To The Adapter Properties and double click the **Internet Protocol Version 4 (TCP/IPv4)** option<br/>
> ![alt tag](Diagrams/23.PNG) <br/>
----------

5.  Use These parameters for the **Static IPv4** Address and click OK<br/>
> ![alt tag](Diagrams/24.PNG) <br/>
----------

5.  Go to Putty and Select SSH Configuration using these Parameters<br/>
> ![alt tag](Diagrams/25.PNG) <br/>
----------

6.  Click YES<br/>
> ![alt tag](Diagrams/26.PNG) <br/>
----------

7. Edison login: **root** 
8. Now you can have access to the Linux Yocto OS

#### SSH File Explorer
1. Download [WinSCP](https://winscp.net/eng/download.php)
2. Open WinSCP and add a New Site with these Parameters (If your Edison has no password, leave that field blank)<br/>
> ![alt tag](Diagrams/27.PNG) <br/>
----------

3. Add This Key to WinSCP<br/>
> ![alt tag](Diagrams/28.PNG) <br/>
----------

3. You Should now have access to the Files with GUI<br/>
> ![alt tag](Diagrams/29.PNG) <br/>
----------