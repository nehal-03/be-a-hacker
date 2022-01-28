### Downloading Files:
wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt Using **wget** 

scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt
- IP address of the remote system: 192.168.1.30
- User on the remote system:	ubuntu
- Name of the file on the remote system:	documents.txt
- Name that we wish to store the file as on our system:	notes.txt

Ubuntu machines come pre-packaged with python3. Python helpfully provides a lightweight and easy-to-use module called "HTTPServer". This module turns your computer into a quick and easy web server that you can use to serve your own files, where they can then be downloaded by another computing using commands such as **curl** and **wget**. 

Python3's "HTTPServer" will serve the files in the directory that you run the command, but this can be changed by providing options that can be found in the manual pages. Simply, all we need to start the module is 
>run python3 -m  http.server 

 A more advanced yet lightweight webserver. [Watch Dog](https://github.com/sc0tfree/updog)
 
 >> 28-01-2022


