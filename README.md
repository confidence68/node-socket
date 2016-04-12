## nodejs+socket创建简单的聊天室

注：部分引用es6的写法，聊天室很简单，就是创建room,更改名称，简单聊天等功能！

命令：

	 /nick 用户名    //修改用户名
   
	 /join 房间名   //修改房间名称
	
入口文件server.js




app.js演示本地创建本地https服务器。

创建本地https服务器私钥key.pem命令

	openssl genrsa 1024 > key.pem命令

	
除了私钥还要用证书，创建本地证书命令：

	openssl req -x509 -new -key key.pem > key-cert.pem
	

基本的代码如下

		var https = require('https')
		const fs = require("fs")
		const hostname = '127.0.0.1'
		const port = 3000

		const options ={
			key:fs.readFileSync("./key.pem"),
			cert:fs.readFileSync("./key-cert.pem")
		}

		const server = https.createServer(options,(req, res) => {
		  res.statusCode = 200
		  res.setHeader('Content-Type', 'text/plain')
		  res.end('Hello World\n')
		})

		server.listen(port, hostname, () => {
		  console.log(`Server running at https://${hostname}:${port}/`)
		})
		
因为我们的证书不是有证书颁发机构颁发的，所有会有安全提示。假如要在服务器上面用https的，那么要去找个证书的颁发机构（CA）进行注册，并为你的服务器取得一份真实的、受信任的证书！


   

   


