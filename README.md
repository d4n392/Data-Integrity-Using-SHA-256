# Data-Integrity-Using-SHA-256

Using various Linux commands such as ls -a, cat, sha256sum and cmp I used file hashing to verify the data integrity of two files. 

## Creating and Comparing Hash Values Using SHA-256

First I used the **ls -a** command to list the contents of my home directory. This showed two files: _file1.txt_ and _file2.txt_.
I then used **cat** to view the contents of _file1.txt_ and _file2.txt_.
At first glance they appear to be identical...

![image](https://github.com/user-attachments/assets/9dd36349-511b-4cb5-b69b-a7147b583693)

Next I used the **sha256sum** command to generate a SHA-256 hash for _file1.txt_ as well as a hash for _file2.txt_.
Comparing the generated hash values I realized even though the files appeared identical, their hash values will differ because the contents are different.

![image](https://github.com/user-attachments/assets/a5a75988-5a24-4025-8676-3af882838864)

Inputting the command **sha256sum file1.txt >> file1hash** I redirected the hash of _file1.txt_ to a new file called _file1hash_. I did the same for _file2.txt_ with the command **sha256sum file2.txt >> file2hash**

![image](https://github.com/user-attachments/assets/54e412dd-45fe-4f62-8b64-1744cd72a9b7)

With the **cat file1hash** and **cat file2hash** commands it’s easy to see below that the hash values of _file1hash_ and _file2hash_ do not match. _Let’s take a deeper look at the Byte-by-Byte level…_

![image](https://github.com/user-attachments/assets/e9f69526-85d4-4dde-aff9-677a7bebaa1c)

Finally I used the **cmp** command to compare _file1hash_ and _file2hash_ Byte-by-Byte. This shows where the first difference occurs. The first difference is in the very first character on the very first line!

![image](https://github.com/user-attachments/assets/ee3a2729-b06a-4b00-adfe-4448ba24efa4)

## Conclusion

This lab demonstrates that even when files look identical, their underlying data can differ, as shown by the different hash values.



