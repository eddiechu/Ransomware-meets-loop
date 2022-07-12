# Ransomware meets loop

Ransomware works just like it sounds – it does not interfere with basic computer functions, but instead encrypts all files and subfolder files in such as pictures, documents, and videos so they cannot be accessed, to panic users. 

What if the ransomware meets an endless sub folder ...

###### Build loop folder
1. Open command prompt, go to test folder, e.g. C:\Temp
2. Create a sub folder named !loop_for_ransomware (The first visible character is '!' according to ASCII table)
3. run ``cd !loop_for_ransomware``
4. run ``mklink /d one ..\!loop_for_ransomware``
5. run ``mklink /d two ..\!loop_for_ransomware``
6. these 2 symbolic links to the parent folder form a endless loop, you can very this by ``dir /s``

###### Test
1. Open command prompt, go to test folder, e.g. C:\Temp
2. run ``for /R %x in (*.*) do ren "%x" *.test``

###### Result
You can see only the first level of file in the parent folder is affected, the files under subfolder have no change, because the "operation" is looped in the subfolder of ``!loop_for_ransomware``

###### P.S. Please exclude this folder ``#loop_for_ransomware`` in the antivirus schedule scan and backup software

###### reference
https://ss64.com/nt/mklink.html

