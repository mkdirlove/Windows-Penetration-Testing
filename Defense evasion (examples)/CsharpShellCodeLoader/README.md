### C# ShellCode Loader
--------------------------------------
A quick and dirty C# shellcode loader that implements several antivirus bypass and defense evasion techniques. <br> 

<i/>Note: I simply reused and modified codes from various Github projects.</i>

#### FEATURES
  - Classic shellcode injection technique using the function 'NtCreateThreadEx'  (=>To do next: upgrade with a better injection technique)
  - Shellcode encryption (XOR)
  - NTDLL unhooking (it loads a fresh new copy of ntdll.dll via file mapping and imports functions from this ntdll.dll)
  - AMSI bypass
  - Basic sandbox detection/evasion techniques
    - Exit if the program is running on a computer that is not joined to a domain
    - Exit if after sleeping for 15s, time did not really passed
    - Exit if a debugger is attached
    - Exit if making an uncommon API call fails (i.e. we are running in an AV sandbox that can't emulating it)

#### TESTS
- Succesfully tested on a Windows 10 x64 laptop (target) with Windows Defender enabled (without 'Automatic sample submission') and a shellcode generated with the Havoc C2 (in C# format & encrypted with XOR cipher algorithm)  
- Code compiled with "Developer PowerShell for VS 2022"
  - Microsoft (R) Visual C# Compiler version 4.5.0-6.23123.11
  - Command: csc /t:exe /out:C:\path\Loader.exe C:\path\Program.cs
