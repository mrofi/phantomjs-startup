PhantomJS startup script ~~(NEED Selenium Grid)~~
======================================================

~~This is a simple startup script based on the selenium startup script.~~

~~This startup script assumes you have selenium server 2.x installed with startup script from feniix (https://github.com/feniix/selenium-grid-startup).~~
also assumes you have the pkg `daemon` installed and a java runtime installed (this was tested in ubuntu ~~10.04.4~~ 16.04 with `openjdk-6-jdk`)

Install PhantomJS:
```
1. Download for linux 
	# for 64 bit
	https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-x86_64.tar.bz2
	# for 32 bit
	https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-i686.tar.bz2
2. Extract
	tar xvjf phantomjs-2.1.1-linux-xxxxxxx.tar.bz2
3. Copy bin to system
	sudo cp ./phantomjs-2.1.1-linux-xxxxxx/bin/phantomjs /usr/bin/
	sudo chmod +x /usr/bin/phantomjs
4. Check instalation 
	phantomjs -v
	
```
and the following already created in your linux box:

id: phantomjs

home: /var/lib/phantomjs

shell: /bin/bash

phantomjs installation directory: /var/lib/phantomjs

    sudo groupadd -r phantomjs
    sudo useradd -r -d /var/lib/phantomjs -s /bin/bash -m -g phantomjs -G phantomjs phantomjs


log dir: /var/log/phantomjs owned by the phantomjs id

    sudo mkdir /var/log/phantomjs
    sudo chown phantomjs.phantomjs /var/log/phantomjs
    

Copy the default file and the init.d file in the right locations:

    sudo cp /local/repo/path/etc/init.d/phantomjs /etc/init.d/
    sudo cp /local/repo/path/etc/default/phantomjs /etc/default/
    
Make sure the init.d script is executable:

    sudo chmod +x /etc/init.d/phantomjs   

Install the service startup:

    sudo update-rc.d phantomjs defaults


~~Change the Selenium Grid port to 5555.~~

	~~nano -w /etc/default/selenium~~

~~Find and change the the line to:~~

	~~# SELENIUM_PORT=5555~~
	~~SELENIUM_PORT=4444~~

~~Start the selenium:~~

    ~~sudo /etc/init.d/selenium start~~

Start the phantomjs:

    sudo /etc/init.d/phantomjs start
    

Check the logs:

    sudo tail -f /var/log/phantomjs/phantomjs.log
    

The service configuration can be found in `/etc/default/phantomjs`

Copyright and license
---------------------

Copyright 2013-2014 Alexey Zhokhov under the [Apache License, Version 2.0](LICENSE). Supported by [Polusharie][polusharie].

[polusharie]: http://www.polusharie.com
