<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Xdebug_Logo.svg/351px-Xdebug_Logo.svg.png" width="100" height="50">

- Add Xdebug Helper on your browser (Firefox or Chrome)
- Install PHP
- Install PHP Xdebug : If  Windows OS download **Xdebug.dll** put it in Xampp *.dll  file path , normally in **C:\Xampp\php\ext** 

- Configure xdebug in php.ini file and  add these lines :
```ini
[xdebug]
;zend_extension = "/path/to/xdebug.so or /path/to/xdebug.dll"
zend_extension="C:\xampp\php\ext\php_xdebug.dll"
xdebug.remote_enable=true
xdebug.remote_host=localhost
xdebug.remote_port=9000
xdebug.remote_handler=dbgp
xdebug.idekey=STDIDE
; Optional Configuration
; Show stacktraces?
xdebug.default_enable=true
xdebug.remote_autostart =true
xdebug.remote_log = "C:\xampp\tmp\xdebug.txt"
```

- Configure your IDE (XDebug Client)

 PHPStorm
   <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d0/Phpstorm.png/220px-Phpstorm.png" width="25" height="25">

```yaml
Languages & Frameworks > Setting > php > Debug :
XDebug : 
  Debug port : 9000 
  Host : localhost # same as xdebug.remote_host=localhost
Languages & Frameworks > Setting > php > Debug > DBGp Proxy :
  IDE Key : STDIDE
  Host : localhost
  Port : 9000 
Languages & Frameworks > Setting > php > Servers :
  Project Files: /path/to/project 
  Host : localhost
  Port : 80
  Debugger : Xdebug
```
Optional alternative in phpstorm
```yaml
Settings > Interpreters > PHP :
Name : PHP
PHP Executable : /path/to/bin/php # maybe /usr/bin/php
Debugger Extension : /path/to/xdebug(.so|.dll)

```
VS Code 
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Visual_Studio_Code_1.35_icon.svg/langfr-800px-Visual_Studio_Code_1.35_icon.svg.png" width="25" height="25">

  - Install php-debug plugin by Felix Becker
  - Generate launch.json by adding run configuration in your project opened in vscode. For more informations, see <a href="https://code.visualstudio.com/docs/editor/debugging"> how to create a launch.json file for debugging in vscode</a>  

<img src="https://code.visualstudio.com/assets/docs/editor/debugging/launch-configuration.png" width="350" height="250">
  
  Your generated launch.json file may be like this:

```json

    "version": "0.2.0",
    "configurations": [
        {
            "name": "Listen for XDebug",
            "type": "php",
            "request": "launch",
            "port": 9000
        },
        {
            "name": "Launch currently open script",
            "type": "php",
            "request": "launch",
            "program": "${file}",
            "cwd": "${fileDirname}",
            "port": 9000
        }
    ]
}

```
  

- Run with Postman <img src="https://seeklogo.com/images/P/postman-logo-F43375A2EB-seeklogo.com.png" width="25" height="25">
```yaml
# http://domain.name/api/url?XDEBUG_SESSION_START=IDEKEY
# Example
http://localhost:8000/apiusers?XDEBUG_SESSION_START=PHPSTORM
# In our case xdebug.idekey=STDIDE
http://localhost:8000/apiusers?XDEBUG_SESSION_START=STDIDE

```




