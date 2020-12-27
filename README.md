# SShNetIbmi - .Net/.Net Core Class Library for Database and Program Access over SSH
This class library is used to interface with existing IBM i database, program calls, CL commands, service programs and 
data queues via the PASE based xmlservice-cli PASE command program or regular qsh/bash commands. qsh/bash commands can be used to interface with utilities such as the [IBM i db2util utility](https://github.com/IBM/ibmi-db2util)

IBM i C# and VB.Net PASE, bash, SSH and XMLSERVICE Data Access Service Wrapper for .Net and .Net Core

Return data is returned in a usable .Net DataTable format or you can process the raw XML responses yourself.
 
This class should work with V7R2 and above of the OS400/IBM i operating system running XMLSERVICE and with the IBM ACS Package xmlservice-cli installed in /QOpenSys/pkgs/bin.
 
# IBM i System Requirements:
 ● Requires xmlservice-cli package installed on the target system via yum packages (/QOpenSys/pkgs.bin/xmlservice-cli)
 
 ● Uses SSH for security
 
 ● The XMLSERVICE service program library QXMLSERV must also exist on the system, This library is installed as part of the IBM i operating system
 
Note: For appropriate security you should configure your SSH users for appropriate security limitations in the IFS and for libraries and commands that may be accessed over an SSH connection to IBM i.

XMLSERVICE is now typically packaged on the IBMi in library: **QXMLSERV** as part of the operating system, but if you want to play with the code, here's the current Github location as of 1/23/2019

https://github.com/IBM/xmlservice
