
Security solution use several techniques to detect malicious software. It's important for one to understand what techniques security solutions use to detect or classify software as being malicious. 

## Static / Signature Detection 

 A signature is a number of bytes or strings within a malware that uniquely identifies it. Other conditions can also be specificized such as variable names and important functions.

Once  the security solution scans a program, it attempts to match it to list of known rules. These rules have to be prebuilt and pushed to security solution. YARA tool that is used by security vendors to build detection  rules. 

It a shellcode contains a bytes sequence that begins with FC 48 83 E4 F0 E8 C0 00 00 00 then this can be used to detect that the payload is a msfvenom's X64 payload. The same detection mechanism can be used against strings with the file. 

Signature detection is easy to bypass but can be time consuming its important to avoid hardcoding values in the malware that can be used to uniquely identified the implementation. 


## Hashing Dtection 
* Hashing detection is a subset of static /signature detection 
* This is the method is done by simply saving hashes 
## Heuristic Detection 
* To spot suspicious characteristics that can be found in unknown, new and modified various of existing malware. 
### Static heuristic 
Involves decompiling the suspicious program and comparing code snippets to known malware that are already known and are in heuristic database if a particulate percentage of the source code matches anything in heuristic database , the program is flagged. 

### Dynamic heuristic 
The program is placed inside a virtual environment or a sandbox which is then analyzed by the security solution for any suspicious behavior. 

## Behavior Based Detection 

The security solution will look for suspicious indicators such as loading a DLL , calling a certain windows API and connecting to internet. 

once the suspicious behavior is detected the security solution will conduct an in-memory scan of the running process . if the process is determined to be malicious, it is terminated. 


## API HOOKING 

Mainly EDR's , to monitor the process or code execution in real time for malicious behaviors. API hooking works by inter coping commonly obused API's  and then analyzing the parameter of these API's in real time . This is a powerful way of detection because it allows the security solution to see the  content passed to the API after its been de-obfuscated or decrypted This stiction in considered a combination of real time and behavior- based detection. 



## IAT Checking 

One of the components that were discussed is the import address table. 

it contains functoin names that are used in the PE at runtime. It also contains the library DLL that export these functions. This infroamtion is valuable to a seucrity solution since it known what WinAPi the executalbe is using. 