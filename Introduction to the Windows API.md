
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
	* *