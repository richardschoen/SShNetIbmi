# SShNetIbmi - .Net/.Net Core Class Library for IBM i Database and Program Access over SSH
This .Net Standard class library is used to interface with an IBM i system over SSH. Can interface to the IBM i database via SQL, program calls, CL commands, service programs and data queues via the PASE based xmlservice-cli PASE command program (part of itoolkit-utilities). Regular qsh/bash commands can also be run to interface with utilities such as the [IBM i db2util utility](https://github.com/IBM/ibmi-db2util) or programs written in languages such as Java, Python, PHP, Node.js and more.

IBM i C# and VB.Net PASE, bash, SSH and XMLSERVICE Data Access Service Wrapper for .Net and .Net Core

Return data is returned in a usable .Net DataTable format or you can process the raw XML responses yourself.
 
This class library should work with V7R2 and above of the OS400/IBM i operating system with the SSH server enabled. 

The XMLSERVICE related methods require XMLSERVICE and the IBM ACS Package xmlservice-cli installed in /QOpenSys/pkgs/bin. (part of itoolkit-utilities)
 
 
# IBM i System Requirements:
 ● Requires xmlservice-cli package installed on the target system via yum packages (/QOpenSys/pkgs.bin/xmlservice-cli)
 
 ● Uses SSH for security
 
 ● The XMLSERVICE service program library QXMLSERV must also exist on the system, This library is installed as part of the IBM i operating system
 
 ● Make sure the IBM i user you will be using for SSH access has /QOpenSys/pkgs/bin in the user search path ```export PATH=/QOpenSys/pkgs/bin:$PATH```
 
**Note: For appropriate security you should configure your SSH users for appropriate security limitations in the IFS and for libraries and commands that may be accessed over an SSH connection to IBM i.**

XMLSERVICE is now typically packaged on the IBMi in library: **QXMLSERV** as part of the operating system, but if you want to play with the code, here's the current Github location as of 1/23/2019

https://github.com/IBM/xmlservice
