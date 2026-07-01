
Security solution use several techniques to detect malicious software. It's important for one to understand what techniques security solutions use to detect or classify software as being malicious. 

## Static / Signature Detection 

 A signature is a number of bytes or strings within a malware that uniquely identifies it. Other conditions can also be specificized such as variable names and important functions.

Once  the security solution scans a program, it attempts to match it to list of known rules. These rules have to be prebuilt and pushed to security solution. YARA tool that is used by security vendors to build detection  rules. 

It a shellcode contains a bytes sequence that begins with FC 48 83 E4 F0 E8 C0 00 00 00 then this can be used to detect that the payload is a msfvenom's X64 payload. The same detection mechanism can be used against strings with the file. 