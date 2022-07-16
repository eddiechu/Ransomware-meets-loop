# Ransomware meets loop

Ransomware encrypts all files and subfolder files in such as Pictures, Documents, and Videos so they cannot be accessed, to panic users. 

What if the ransomware meets an endless subfolder ...

###### Build loop folder
1. Open command prompt, go to test folder, e.g. C:\Temp
2. Create a sub folder named ``!loop_for_ransomware`` ('!' is the first visible character in ASCII table)
3. run ``cd !loop_for_ransomware``
4. run ``mklink /d one ..\!loop_for_ransomware``
5. run ``mklink /d two ..\!loop_for_ransomware``
6. these 2 symbolic links form an endless loop, you can verify this by ``dir /s``

###### Test
1. Open command prompt, go to test folder, e.g. C:\Temp
2. run ``for /R %x in (*.*) do ren "%x" *.test``, to simulate "ransomware operation"

###### Result
You can see only the first level of file in the parent folder is affected, the files under subfolder have no change, because the "ransomware operation" is looped in the subfolder of ``!loop_for_ransomware``

###### P.S. Exclude this folder ``!loop_for_ransomware`` in the antivirus schedule scan and backup software

###### Reference
https://ss64.com/nt/mklink.html

