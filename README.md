This the official blazing fast UAC-bypassing Rubber Ducky payload generator.
For anything related , hit me up: https://twitter.com/SkiddieTech

          _   _  _   ___   ___  _   _  ___ _  __
         | | | |/_\ / __| |   \| | | |/ __| |/ /
         | |_| / _ \ (__  | |) | |_| | (__| ' <
          \___/_/ \_\___| |___/ \___/ \___|_|\_\

        [+++++++++++++++++++++++++++++++++++++++]
        
Our Goal.
Our main goal is to silently and FAST download an drop any binary executable to an Windows box,granting it administrate privileges to freely roam the system.

It uses a simple 2 stage process

Stage 1:
Stage one is the script that is triggered when the ducky is connected to any targeted windows machine.
It will execute an powerful one-liner inside the "run" dialog of the system.
The one liner is a simple powershell script, that when executes instantly hides then powershell windows and runs it the background.
The powershell script downloads and execute our stage 2 .vbs payload in the %temp% directory

Stage 2:
Once your .vbs payload is on the system, we proceed to download our main binary payload. The .vbs script exploits a flaw in the windows registry system, this allows us to execute and binary file on the system with admin privilege without prompting the user for access (UAC).

NT Authority/System on ANY windows system u say?

As far as i can tell, still after the latest Windows 10 update, using this setup togheter with the "Getsystem" script in the meterpreter module, we will always be able to get NT Authority/System permisson using Tech 1 (Named Pipe Impersonation (In Memory/Admin))

Tested on Win7,Win8 and Win10 running latest update.
That is pretty sick...

Video demo of the VBS payload, i will be showing full execution using the rubber ducky very soon.
http://sendvid.com/g4nj0crt

As you can see, we get an meterpreter shell that says it's running under user, however, if we drop into a CMD shell inside the meterpreter module, we can see we are running inside the system32 dir, indicating that we are running as admin, we can even use the getsystem script in the meterpreter module to gain NT System privliges, that's pretty sick.(Tested working on Win7,Win8 and Win10! 


Here is a video doing a normal run, as you see we get a shell in "userland" and we cannot gain any further privliges using the "getsystem" script.
http://sendvid.com/j6tdud7x


