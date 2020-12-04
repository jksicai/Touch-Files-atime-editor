# Touch-Files-atime-editor (not written by me)
Overview
Sometimes test data needs to have the last accessed times and/or last modified times adjusted so that the data appears old enough to move.

You can use the tools mentioned below to adjust the last accessed times and last modified times of files.

Adjusting file times on SMB
Komprise Data Proxy installer should place the Windows PowerShell script Touch-Files.ps1 in:

     C:\Program Files\Komprise\Proxy\Scripts. 

You can also download the script from:

     https://komprise.s3-us-west-2.amazonaws.com/Artifacts/Scripts/Touch-Files.ps1



The script, by default, will set last accessed times to 9 Feb 2007 11:31:23 AM and last modified times to 4 July 2005 05:12:44 PM. You can adjust these times by editing the script.



Run the script in Windows PowerShell as follows: 

     .\Touch-Files.ps1 -Path <directory or file path> 



Example:

     .\Touch-Files.ps1 -Path \\10.1.10.54 



Verify that it sets the last accessed and last modified times of all non-stub and non-link files to the desired older date.



For adjusting file last accessed times, last modified times, and created times on Windows, there is also a free utility call BulkFileChanger that runs on Windows 2000 to Windows 10.



Adjusting file times on NFS
Mount the NFS export somewhere, go into the folder and run:

     find . -exec touch -a [-m] -t <date-time-string> {} +



where:

     -a    change the access time

     -m   change the modified time

     -t     set time to: [[CC]YY]MMDDhhmm[.ss] instead of current time



Example:

     find . -exec touch -a -m -t 201212211111 {} +

will set both the last accessed times and last modified times of all files to 21 Dec 2012 11:11.
