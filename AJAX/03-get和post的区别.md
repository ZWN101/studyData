1. get重点在于从服务器获取资源，post重点在于向服务器发送数据

2. get传输数据是通过URL请求，以key=value的形式，放在URL之后，用“？”连接，多个参数时“&&”连接，如：http://localhost:8080/test/loginaction?name=admin&&password=admin,这个过程是用户可见的；post传输数据通过http的post机制，将携带的参数封装在请求体中发送给服务器，这个过程是对用户不可见的

3. get传输的数据量小，因为受URL长度的限制，但是效率高；post可以传输大量的数据，所以上传文件时只能用post方式

4. get方式不安全，因为URL是可见的，可能会泄漏私密信息；post比较get安全性高

5. get方式只能支持ASCII字符，向服务器传中文字符可能会出现乱码；post支持标准字符集，可以正确的传递中文字符