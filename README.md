#MegaTUI

Wrote this to make life easier for sysadmins that manage LSI MegaRaid
controllers. It's text based menu frontend to MegaCLI, which is a quite arcane
tool. 

MegaTUI is dynamic, so some menus are hidden until you start configuring. For
example you will not see the foreign disk menu unless there are foreign disks
on the system. Likewise you will not be able to delete arrays unless there are
some that can be deleted. 

Top level (with all possible menus enabled)

 Pr) Print Raid Configuration
 Cr) Create Array
 De) Delete Existing Array(s)
 Co) Configure Array(s)
 Ht) Hotspare Management
 Fd) Foreign Disk Management
 Ma) Manage Disks
 Sc) Rescan controller

 Quit) Quit

You can always use Q/Quit to cancel your choice and step back one menu level
Most things are self explanatory. But I thought I could step through some of
it.

[172.21.13.89]> Pr 
-- Controller Information --
ID  | H/W Model         | RAM    | Temp | Firmware     
c0  | PERC H730 Mini    | 1024MB | 63C  | FW: 25.2.1.0037 
c1  | PERC H830 Adapter | 2048MB | 84C  | FW: 25.2.1.0032 

-- Array Information --
-- ID | Type    |    Size |  Strpsz |      Flags | DskCache |   Status |  OS Disk | InProgress   
c0a0  | RAID-1  |    931G |   64 KB |    ADRA,WB |  Default |  Optimal |      sda | None         
-- ID    | Type | Size Gb  | Status          | Speed    | Slot ID  | Disk ID 
c0a0s0a0 | HDD  | 931      | Online, Spun Up | 6.0Gb/s  | [32:0]   | 0       
c0a0s0a1 | HDD  | 931      | Online, Spun Up | 6.0Gb/s  | [32:1]   | 1       

-- ID | Type    |    Size |  Strpsz |      Flags | DskCache |   Status |  OS Disk | InProgress   
c1a0  | RAID-1  |   3637G |   64 KB |    ADRA,WT |  Default |  Optimal |      sdb | None         
-- ID    | Type | Size Gb  | Status          | Speed    | Slot ID  | Disk ID 
c1a0s0a0 | HDD  | 3637     | Online, Spun Up | 6.0Gb/s  | [50:0]   | 55      
c1a0s0a1 | HDD  | 3637     | Online, Spun Up | 6.0Gb/s  | [50:1]   | 57      

-- ID | Type    |    Size |  Strpsz |      Flags | DskCache |   Status |  OS Disk | InProgress   
c1a1  | RAID-1  |   3637G |   64 KB |    ADRA,WB |  Default |  Optimal |      sdc | None         
-- ID    | Type | Size Gb  | Status          | Speed    | Slot ID  | Disk ID 
c1a1s0a0 | HDD  | 3637     | Online, Spun Up | 6.0Gb/s  | [50:2]   | 59      
c1a1s0a1 | HDD  | 3637     | Online, Spun Up | 6.0Gb/s  | [50:3]   | 52      
c1a1sXaY | HDD  | 3637     | HotSP, Spun Up  | 6.0Gb/s  | [50:10]  | 56      

-- ID | Type    |    Size |  Strpsz |      Flags | DskCache |   Status |  OS Disk | InProgress   
c1a2  | RAID-1  |   3637G |   64 KB |    ADRA,WB |  Default |  Optimal |      sdd | None         
-- ID    | Type | Size Gb  | Status          | Speed    | Slot ID  | Disk ID 
c1a2s0a0 | HDD  | 3637     | Online, Spun Up | 6.0Gb/s  | [50:4]   | 62      
c1a2s0a1 | HDD  | 3637     | Online, Spun Up | 6.0Gb/s  | [50:5]   | 54      

-- ID | Type    |    Size |  Strpsz |      Flags | DskCache |   Status |  OS Disk | InProgress   
c1a3  | RAID-0  |   3637G |   64 KB |    ADRA,WB |  Default |  Optimal |      sde | None         
-- ID    | Type | Size Gb  | Status          | Speed    | Slot ID  | Disk ID 
c1a3s0a0 | HDD  | 3637     | Online, Spun Up | 6.0Gb/s  | [50:9]   | 51      


-- Unconfigured Disk Information --
-- ID    | Type | Size Gb  | Status          | Speed    | Slot ID  | Disk ID  
c0aXsYaZ | HDD  | 1090     | Unconf, Spun Up | 6.0Gb/s  | [32:2]   | 2        
c0aXsYaZ | HDD  | 1090     | Unconf, Spun Up | 6.0Gb/s  | [32:3]   | 3        
c0aXsYaZ | HDD  | 3637     | Unconf, Spun Up | 6.0Gb/s  | [32:4]   | 4        
c0aXsYaZ | HDD  | 3637     | Unconf, Spun Up | 6.0Gb/s  | [32:5]   | 5        
c0aXsYaZ | HDD  | 3637     | Unconf, Spun Up | 6.0Gb/s  | [32:6]   | 6        
c0aXsYaZ | HDD  | 3637     | Unconf, Spun Up | 6.0Gb/s  | [32:7]   | 7        
-- ID    | Type | Size Gb  | Status          | Speed    | Slot ID  | Disk ID  
c1aXsYaZ | HDD  | 3637     | Unconf, Spun Up | 6.0Gb/s  | [50:6]   | 58       
c1aXsYaZ | HDD  | 1090     | Unconf, Spun Up | 6.0Gb/s  | [50:7]   | 66       
c1aXsYaZ | HDD  | 3637     | Unconf, Spun Up | 6.0Gb/s  | [50:8]   | 53       
c1aXsYaZ | HDD  | 1090     | Unconf, Spun Up | 6.0Gb/s  | [50:11]  | 65       

 Pr) Print Raid Configuration
 Cr) Create Array
 De) Delete Existing Array(s)
 Co) Configure Array(s)
 Ht) Hotspare Mangement
 Fd) Foreign Disk Management
 Ma) Manage Disks
 Sc) Rescan controller

 Quit) Quit

[172.21.13.89]> Cr

Select controller to create array on

-- No | ID | H/W Model            | # Avail Disk    
    0 | c0 | PERC H730 Mini       | 6               
    1 | c1 | PERC H830 Adapter    | 4               

Quit) Quit

[172.21.13.89]> 1

Select disks to create array from as comma separated list of Disk ID
All will select all disks

-- Disk ID | ID       | Type | Size Gb  | Status          | Speed    | Slot ID  
58         | c1aXsYaZ | HDD  | 3637     | Unconf, Spun Up | 6.0Gb/s  | [50:6]   
66         | c1aXsYaZ | HDD  | 1090     | Unconf, Spun Up | 6.0Gb/s  | [50:7]   
53         | c1aXsYaZ | HDD  | 3637     | Unconf, Spun Up | 6.0Gb/s  | [50:8]   
65         | c1aXsYaZ | HDD  | 1090     | Unconf, Spun Up | 6.0Gb/s  | [50:11]  

All) All disks above
Quit) Quit

I will not show all the steps here but in essence you select the disks you want
and depending on what raid levels that this can support you will get a choice
what raid you want to create. Note that I don't probe the controller (yet) for
what types it supports so please even if the MegaTUI supports say Raid-60 your
controller might not. When your about to create the raid array you will also
get an option to set any config parameters such as strip size and others. 

You can configure arrays later on with the Co command but remember some
settings can only be set during the creation of the array,

[172.21.13.89]> Co

Select array to configure

-- Array Information --
-- ID | Type    |    Size |  Strpsz |      Flags | DskCache |   Status |  OS Disk | InProgress   
c0a0  | RAID-1  |    931G |   64 KB |    ADRA,WB |  Default |  Optimal |      sda | None         
-- ID | Type    |    Size |  Strpsz |      Flags | DskCache |   Status |  OS Disk | InProgress   
c1a0  | RAID-1  |   3637G |   64 KB |    ADRA,WT |  Default |  Optimal |      sdb | None         
c1a1  | RAID-1  |   3637G |   64 KB |    ADRA,WB |  Default |  Optimal |      sdc | None         
c1a2  | RAID-1  |   3637G |   64 KB |    ADRA,WB |  Default |  Optimal |      sdd | None         
c1a3  | RAID-0  |   3637G |   64 KB |    ADRA,WB |  Default |  Optimal |      sde | None         


Here is a quick view of the HotSpare functions

[172.21.13.89]> Ht

 Pr) Print HotSpares
 Cr) Create HotSpares
 De) Delete HotSpares

 Quit) Quit

[172.21.13.89]> Pr

-- ID    | Type | Size Gb | Status          | Speed    | Slot ID  | Disk ID | HotSpare Type
c1a1sXaY | HDD  | 3637    | HotSP, Spun Up  | 6.0Gb/s  | [50:10]  | 56      | Dedicated

Foreign disk, Note when executing the Fd command it will take a brief moment
before the prompt returns. This is due to the fact that we are scanning the
system for how it will look if we would import some foreign disks.

[172.21.13.89]> Pr

-- Foreign Disk Arrays on Controller c0 --
-- ID | Type    |    Size |  Status 
c0a1  | RAID-5  |   7276G | Offline 
-- ID | Type | Size Gb | Status               | Slot ID  | Disk ID 
c0a1d0 | HDD  | 3637    | Rebuild              | [32:4]   | 4       
c0a1d1 | HDD  | 3637    | Online, Spun Up      | [32:5]   | 5       
c0a1d2 | N/A  | 0       | Missing              | [0:0]    | 0       

-- ID | Type    |    Size |  Status 
c0a2  | RAID-1  |   3637G | Optimal 
-- ID | Type | Size Gb | Status               | Slot ID  | Disk ID 
c0a2d0 | HDD  | 3637    | Online, Spun Up      | [32:6]   | 6       
c0a2d1 | HDD  | 3637    | Online, Spun Up      | [32:7]   | 7       


-- Foreign Disk Arrays on Controller c1 --
-- ID | Type    |    Size |  Status 
c1a4  | RAID-5  |   7636G | Offline 
-- ID | Type | Size Gb | Status               | Slot ID  | Disk ID 
c1a4d0 | HDD  | 1090    | Online, Spun Up      | [50:11]  | 65      
c1a4d1 | HDD  | 1090    | Online, Spun Up      | [50:7]   | 66      
c1a4d2 | N/A  | 0       | Missing              | [0:0]    | 0       
c1a4d3 | N/A  | 0       | Missing              | [0:0]    | 0       
c1a4d4 | N/A  | 0       | Missing              | [0:0]    | 0       
c1a4d5 | N/A  | 0       | Missing              | [0:0]    | 0       
c1a4d6 | N/A  | 0       | Missing              | [0:0]    | 0       
c1a4d7 | N/A  | 0       | Missing              | [0:0]    | 0 


Note: Pr is printing what is and isn't possible to import, how the arrays of
the foreign disks looks. So in the c0a2 array above it doesn't mean it's online
now but that if we did import it would come online with out hiccups. As you can
see this would not be the case with c1a4 since we are lacking several of the
disks that makes up this array.


Manage disks, this example will show the dynamic menus in action.


 [172.21.13.89]> Ma

 Of) Offline Disk
 Rm) Replace Missing Disk

 Quit) Quit

[172.21.13.89]> Of

Select controller  to off line disks on

-- No | ID | H/W Model            | # Avail Disk    
    0 | c0 | PERC H730 Mini       | 6               
    1 | c1 | PERC H830 Adapter    | 4               

Quit) Quit

[172.21.13.89]> 1

Select array to off line disks on

-- ID | Type    |    Size |  Strpsz |      Flags | DskCache |   Status |  OS Disk | InProgress   
c1a0  | RAID-1  |   3637G |   64 KB |    ADRA,WT |  Default |  Optimal |      sdb | None         
c1a1  | RAID-1  |   3637G |   64 KB |    ADRA,WB |  Default |  Optimal |      sdc | None         
c1a2  | RAID-1  |   3637G |   64 KB |    ADRA,WB |  Default |  Optimal |      sdd | None         
c1a3  | RAID-0  |   3637G |   64 KB |    ADRA,WB |  Default |  Optimal |      sde | None         

Quit) Quit

[172.21.13.89]> c1a0

Select disk to off line

Disk ID  | -- ID    | Type | Size Gb  | Status          | Speed    | Slot ID  
55       | c1a0s0a0 | HDD  | 3637     | Online, Spun Up | 6.0Gb/s  | [50:0]   
57       | c1a0s0a1 | HDD  | 3637     | Online, Spun Up | 6.0Gb/s  | [50:1]   

Quit) Quit

[172.21.13.89]> 57

Disk offlined sucessfully
 Of) Offline Disk
 Mi) Mark Disk as Missing
 Rm) Replace Missing Disk

 Quit) Quit

As you can see you can't mark disks as missing unless they are off line, so it's
first when you off lined a disk this action item will appear, 


Thats it for now, I'm sure you will find bugs if so please report them :).



Note: You will need the  latest version of MegaCLI. As of writing this is MegaCLI 5.5 P2 or "Ver
8.07.14 Dec 16, 2013"  when you execute MegaCli -v.  
