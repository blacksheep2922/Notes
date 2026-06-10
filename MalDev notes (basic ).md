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

![]( <Notes_images/flow.png> )

## Directly invoking the Native API (NTAPI)

Its important to note that applications can invoke syscalls directly without having to go through the wind API. The Windows API simply acts as a wrapper for the native API. With that being said the native API is more difficult to use because it is not officially documented by Microsoft. 



### Lets make a program to see how to create a file in windows using API

#include <windows.h>
#include <stdio.h>

int main() {
    HANDLE hFile;

    hFile = CreateFileW(
        L"C:\\Users\\abhik\\Desktop\\file.txt",
        GENERIC_READ | GENERIC_WRITE,
        FILE_SHARE_READ,
        NULL,
        CREATE_ALWAYS,
        FILE_ATTRIBUTE_NORMAL,
        NULL
    );

    if (hFile == INVALID_HANDLE_VALUE) {
        // %lu is the format specifier for DWORD (unsigned long)
        printf("CreateFile failed. Error code: %lu\n", GetLastError());
        return 1;
    }

    printf("CreateFile success!\n");

    CloseHandle(hFile);

    // Using system("pause") just like your original code
    system("pause");

    return 0;
}


## Windows Memory Management 


Memory in  modern OS  is not mapped directly to physical memory (RAM) 
 - Virtual Memory address are used by process that are mapped to physical memory address. why ? to save physical memory 

- Virtual memory may be mapped  to physical memory but can also be stored on disk. 

- with this, addressing it become possible for multiple process to share the same physical address *
- while having a unique virtual memory address.


## Page state 

The page reside within a process's virtual address space can be in one of 3 stare. 

### 1. Free 
- The page is neither committed nor reserved. The page is not accessible to the process .It is available to be reserved, Committed or simultaneously reserved and committed. Attempting to read from or write to a free page can result in an access violation exception. 
### 2. Reserved
* The page has been reserved for future use. The range of address cannot be used by other allocation function. The page is not accessible and has no physical storage associated with it, it is available to be committed. 
### 3. Committed 
- Memory charges have been allocated from the overall size of RAM and paging files on disk. The page is accessible and access is controlled by one of the memory protection constants. The initialize and loads each committed page into physical memory only during the first attempt to read or write to that page. When terminated, the system releases the storage for committed pages. 

## Memory protection 
 Modern os have built in memory protection to the exploits and attacks. There are also important to keep in mind as they well likely be encountered when building or debugging the malware. 
## Data Execution Prevention (DEP)

In a system memory protection features that in bult into the operating system. 
* Starting with windows XP and windows server 2003. if the page protection option is set to PAGE_READONLY, then DEP will prevent ode from exacting in that memory region. 

### Address space layout randomization (ASLR)
ASLR is a memory protection techniques used to prevent the exploitation of memory corruption vulnerability. ASLR randomly arranges the address space position of key data areas of a process including the base of the executable and the positions of the stack, heap and libraries. 

### X86 VS X64 memory space 

when working with windows process, it's important to not whether the process is x86 or x64. x86 process have a smaller memory space of 4GB(0xfffff) where as x64 has a vastly larger memory space of 128TB. 

lets see some examples of it we can use in our program to see what different functions we can use some of them are : 
* **Method 1 - Using malloc()**
	* ==PVOID pAddress = malloc(100);==
* **Method 2 - Using HeapAlloc()***
	* ==PVOID pAddress = HeapAlloc(GetProcessHeap(),0100);==
* **Method 3 - Using Local Alloc()***
	* ==PVOID pAddress = LocalAlloc (LPTR,100);==

These function return base address which is simply a pointer to the beginning of the memory block that was allocated. 

* pAddress will be the base address of the memory block that was allocated. 
* Using the pointer several actions can be taken such as reading, writing and executing.


![](<Notes_images/Pasted%20image%2020260610201400.png>)