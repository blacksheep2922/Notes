
The windows API gives developer with the ways for their applications to interact with windows OS. 
## Windows Data type
* The windows api has many data types outside of the well-known ones. 
* DWORD - A 32-bit unsigned integer, on both 32- bit and 64-bit Systems, used to represent values from 0 to (2^32 -1).*
	* Example - DWORD dwVariable =42;
**SIZE_t** = used to represent the size of an object, its a 32-bit unsigned integer on 32-bit systems representing values from 0 to (2^32 -1). on the other hand, it's a 64-bit unsigned integers on 64-bit systems. representing values from 0 to (2^64 -1) .
* example Size_T sVariable = SizeOF(int);

**VOID** 
* Indicate the absence of a specific data tpye. 
* Void * pVariable =NULL; 

PVOID
*  A 32-bit or 4 bytes pointer of any data type on 32-bit systems. Alternatively a 64bit or 8 bytes pointer of any data type on a 64-bit system. 
	* PVOID pVariable = $SomeData;

HANDLE 
* A value that specific a perticular object that the operating system in managing
	* file, process, thread 
		* HANDLE hFile = CreateFile(..);

HMODULE 
* A handle to module. This is the base address of the module in memory. An example of a Module can be a DLL or EXE file. 
	* HMODULE hModule =GetModuleHandle(...); *
	*
## **LPCSTR /PCSTR**

A pointer to a constant null-ternimated string of 8bit windwos charatcter (ANSI)

* The L string for long which is derived from the 16bit windows programming period, nowdays it doesn't affect the data type, but the naming convention still exists
* The C stands for constanct or read only variable both these data types are equivalent to const char* 
	* LPCSTR lpcString ="Hello World";
	* PCSTR pcString = "Hello, World";
LPSTR/ PSTR 

The same as LPCSTR and PCSTR 
the only differecne is that LPSTR and PSTR do not point to a constant variable, and instead point to a readable and write able string both these data types are equivalent to char* 


### Data Types Pointer 

The windows api allows a developer to declare a data type directly or a pointer to the data type names where the data types that start with "p" represents to the actuale data type while the other that don't start with "p" represent the actual data type itself.
This will become useful later when working with windows api that have parameter that are pointer to a data type. The example below shoe how the "p" data tyoe relates to its non-poinyer equivalent. 
	* PHANDLE  is the same as HANDLE*
	* PSIZE_T is the same as SIZE_T
	* PDWORD is the same as DWORD 
	
### ANSI  and Unicode Functions
The majority of windows api functions have two versions ending with either "A" or with "W". 
for example , there is CreateFileA and CreatefileW The functions ending with "A" are meant to indicate "ANSI" whereas the functions ending with "W represent unicode or "Winde".

The main differnece to keep 