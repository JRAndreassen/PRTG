Powershell script to get information from Paessler PRTG’s database for ’system information’
=====================================================

This script gets information from ‘system information’ and export this information into a compiled data dump that can be further analyzed and sorted from e.g. Microsoft Power BI or Microsoft Excel. 

The information can be used to populate a CMDB.

The script can also be used as a base to directly sort specific values or classes for further automation.

## Version
Version 1 2018-09-18 [Klas Pihl](Klas.Pihl@atea.se) – Paessler certified monitoring expert 2018

## Use cases can be
* Find devices that has a specific service running and add a sensor to all of these devices.
* Get a list of device names and serial number.
* Find windows servers that have a specific application installed or Not installed. 
* Inventory number of Windows licenses needed. 

The output data from ‘systems information’ can be presented in PRTG as a custom sensor. 
Example;  

* Get a view in PRTG on the used IP addresses on different subnets.   
![Used IP Adresses](./Images/CMDB_KlasPihl_1.png)  

* Number of Windows systems and version.
![ Number of Windows systems and version](./Images/CMDB_KlasPihl_2.png)

* Installed software
![ Installed software](./Images/CMDB_KlasPihl_3.png)

* Device ID of virtual machines
![Devices ID of virtual machines](./Images/CMDB_KlasPihl_4.png)
  

## Dependencies
Powershell module [‘PRTGAdminModule.psm1’](https://github.com/AndrewG-1234/PRTG) from AndrewG.

## Setup Instructions

In the PRTGAdminModule.psm1 you have to change the address to your PRTG core server, the url is reoccurring so be wary to change all of them and also select http or https depending on your PRTG installation.

The get-systemInformationDatabaseItem.psm1 module need correct paths to:

* PRTGAdminModule – module
* PRTGCoreServer DNS or IP address.
* Filepath to place the compiled and exported data.
* FIlepath to PRTG DataPath, Default C:\ProgramData a hidden catalogue. 

## Running tips
Depending on how many devices your PRTG installation is running and the amount of data gathered in system information there can be a lot of objects. It can consume memory and run for hours.  

Run the script remotely and not on the Core server.

Minimize the number of classes to load, i.e. If you want to find a specific application only select ‘Software’ class.
