How to get TTD log 
 
1.	Get TTD tool from OneDrive link. 
  
2.	Download it and Exact the content to a folder, x86\TTD is for 32bit OS, and amd64\TTD is for 64bit OS. 
3.	Copy the “amd64\TTD” to “C:\TTD” if you are using 64bit OS.  
  
4.	Create a new folder C:\TTD\Dumps for log files. 
  
5.	Open a command prompts using Administrator permission and navigate to TTD folder. 
  

6.	Move Outlook to work offline, compose the information (DL included) in MS Publisher until you are ready to click the “Send” button. 

7.	Initialize the tool firstly using following command. 
TTTracer.exe -initialize 
  
8.	Attach the TTD tool to application, you need to check the PID from task manager and attach it with the ttt tracing. 
 

TTTracer.exe -onlaunch excel.exe -dumpfull -out C:\TTD\Dumps
TTTracer.exe -dumpfull -attach 12320 -out C:\TTD\Dumps
 
9.	Then when Publisher is attached, you will see a new CMD window opened, when it’s OK, we will see a small window like below. (I used PPT in my case)
 
 
10.	It means the TTD tool is running, you may need wait several minutes to see this window. 
11.	Then we can try to reproduce this issue, because TTD is attaching application to get logs, so the application might be a bit slow. 
12.	When we click the “send” button and issue is reproduced, uncheck the “Tracing On”, then the TTD log files will be saved. 
  
13.	Go to the C:\TTD\Dumps folder, you will see TTD files. 
  
14.	Zip all files in the Dumps folder to reduce file size and share the zip file to engineer for next step analysis. 

15.	Because TTD is attached to application, so we need un-attach it. Execute following command in CMD window. 
TTTracer.exe -stop ALL 
TTTracer.exe -delete excel.exe 

 
