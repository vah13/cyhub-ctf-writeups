Hey.
For a beginning, you can see that there is a WSDL file provided with the task http://files.2020.ctf.cyhub.am/game_materials/wsdl.wsdl. 
If you examine the WSDL file request methods, you will find that there are GET/POST requests with an XML body.
As the provided web server has an IP address, you can brute force the directories in order to find some hidden services using dirb or some other tools.
As a result, you will find the following URL address: 

http://web1.2020.ctf.cyhub.am/test 

![web](images/_dirb.png)

and by opening it, you'll get a timeout error (504) instead of Not found (404).

So, as you already know that there is some XML parser on the backend, you need to send a simple POST request to /test with <a>b</a> XML body.


You got <a>b</a> in respose.
![web](images/_xml.png)


The most popular attack to web services that parse XML is XML serialization. See details in:

https://github.com/GrrrDog/Java-Deserialization-Cheat-Sheet#xmlencoder-xml

Using the classic payload for XML decoder/encoder send the following request to the server for getting the RCE. 
![web](images/_PoC.png)
![web](images/_DnS.png)

After that, you just need to read a flag from the server.

Tnx.
