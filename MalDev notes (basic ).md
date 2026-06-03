Windows Architecture 

There are two main things the User Mode and the Kernel Mode 

* User process --> System DLLs --> NTDLL.DLL --> Executive kernel *


1. User process - A Program / application executed by the users as notepad , Google Chrome or Microsoft word.
2. Systems Dlls - DLL that contain API functions that are called by user processes. 
3. Kernel32.dll - exporting the create file windows Api (Win API) function, other common system DLLs are htdll.dll, advapi32.dll and user32.dll. 
4. Ntdll.dll - A system wide DLL which is the lowest layer available in user mode . This is special DLL that creates the transition form user mode to kernel mode. This is often referred to as the native API or NTAPI. 
5. Executive kernel - This is what is known as the windows kernel and it calls other drivers and modules the available within kernel mode to complete tasks. The windows kernel is partially stored in a file called **ntoskrnl.exe** 
--> Under - =="C:/Windows/System32"==

### Function Call flow 


![[Pasted image 20260603230111.png]]


## Directly invoking the Native API (NTAPI)

Its important to note that applications can invoke syscalls directly without having to go thorugh the wind API. The Windows API simply acts as a wrapper for the native API. With that being said the native API is more difficult to use because it is not officially documented by Microsoft. 



### Lets make a program to see how to create a file in windows using API
