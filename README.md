# Scrapy_spider

### 安装环境:
 
##### 1. server config：
* Distributor:    CentOS release 6.8
*  cpu: Intel(R) Xeon(R) CPU E5606 @ 2.13GHz x 2       
*  Memory：32GB (4GB x 8)          
*  Drive：2TB x 4          
*  network: Broadcom Corporation NetXtreme II BCM5716 Gigabit Ethernet x 2
##### 2.  Install`python`： Since Scrapy requires python 2.7 or higher, you need to upgrade python2.7 first
* download: `wget http://python.org/ftp/python/2.7.3/Python-2.7.3.tar.bz2`
* Decompression: `tar -jxvf Python-2.7.3.tar.bz2`
* install: `[root@hostname Python-2.7.3]# ./configure`
* make :`[root@hostname Python-2.7.3]# make && make install`
* verification
```
[root@hostname Python-2.7.3]# python2.7     
Python 2.7.3 (default, Apr 28 2017, 17:08:56)      
[GCC 4.4.7 20120313 (Red Hat 4.4.7-17)] on linux2      
Type "help", "copyright", "credits" or "license" for more information.      
>>>
```  

#####   3. Install setuptools
   
* download:`wget http://pypi.python.org/packages/source/s/setuptools/setuptools-0.6c11.tar.gz`    
* Decompression:`tar zxvf setuptools-0.6c11.tar.gz`
* install : `[root@hostname setuptools-0.6c11]# python2.7 setup.py install`

#####   4. install Twisted   
* Installed `/usr/local/lib/python2.7/site-packages/six-1.10.0-py2.7.egg `
`[root@hostname setuptools-0.6c11]# easy_install Twisted`
* Of course `zope.interface` will automatically download and install
```
Reading http://pypi.python.org/simple/zope.interface/
Best match: zope.interface 4.4.0
```  
#####   5.  install `w3lib`
```       
 [root@hostname setuptools-0.6c11]# easy_install -U w3lib 
 Installed /usr/local/lib/python2.7/site-packages/w3lib-1.17.0-py2.7.egg
 Processing dependencies for w3lib
 Finished processing dependencies for w3lib
```    
#####  6. install `libxml2` or use `easy_install` install `lxml`
``` 
[root@hostname setuptools-0.6c11]# easy_install lxml
Building lxml version 3.7.3
```
* next we can verification lxml ？
```
[root@d1-datanode24 setuptools-0.6c11]# python2.7
Python 2.7.3 (default, Apr 28 2017, 17:08:56)
[GCC 4.4.7 20120313 (Red Hat 4.4.7-17)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import lxml
>>> exit()
```
##### 7. Install `pyOpenSSL`(This is optional to install, mainly to enable `scrapy` to support `https`)

* Easy_install pyOpenSSL is installed pyOpenSSL-0.13 version, did not install successfully, then manually download .011 version to install.
* install
```
[root@hostname pyOpenSSL]# wget http://launchpadlibrarian.net/58498441/pyOpenSSL-0.11.tar.gz
100%[=======================================================================================================================================>] 242,152     68.1K/s   in 3.5s
2017-04-28 19:52:24 (68.1 KB/s) - “pyOpenSSL-0.11.tar.gz” saved [242152/242152]

```
* Decompression: `[root@hostname pyOpenSSL]#  tar zxvf pyOpenSSL-0.11.tar.gz`
* Install:`[root@hostname pyOpenSSL-0.11]# python2.7 setup.py install`
##### 8.Install `scrapy`
`[root@hostname pyOpenSSL-0.11]# easy_install -U Scrapy`

__ERROR__:
`error: Installed distribution pyOpenSSL 0.11 conflicts with requirement pyopenssl>=0.12`

```
[root@d1-datanode24 site-packages]# scrapy
Traceback (most recent call last):
File "/usr/local/bin/scrapy", line 5, in <module>
from pkg_resources import load_entry_point
File "build/bdist.linux-x86_64/egg/pkg_resources.py", line 2607, in <module>
File "build/bdist.linux-x86_64/egg/pkg_resources.py", line 569, in resolve
pkg_resources.VersionConflict: (pyOpenSSL 0.11 (/usr/local/lib/python2.7/site-packages), Requirement.parse('pyopenssl>=0.12'))
```

###### Solution
* Do not force it to be removed and then reinstall it. This is __*wrong*__
* TRUE solution:

``` 
[root@hostname site-packages]# yum info pyOpenSSL
Available Packages
Name        : pyOpenSSL
Arch        : x86_64
Version     : 0.10
Release     : 2.el6
Size        : 212 k
Repo        : base_source
Summary     : Python wrapper module around the OpenSSL library
URL         : http://pyopenssl.sourceforge.net/
License     : LGPLv2+
Description : High-level wrapper around a subset of the OpenSSL library, includes
            :  * SSL.Connection objects, wrapping the methods of Python's portable
            :    sockets
            :  * Callbacks written in Python
            :  * Extensive error-handling mechanism, mirroring OpenSSL's error codes
            : ...  and much more ;)
```

*  Download 0.12 and install
`wget http://pypi.python.org/packages/source/p/pyOpenSSL/pyOpenSSL-0.12.tar.gz`
`Writing /usr/local/lib/python2.7/site-packages/pyOpenSSL-0.12-py2.7.egg-info`

[root@hostname pyOpenSSL-0.12]# easy_install -U Scrapy
```
Searching for Scrapy
Reading http://pypi.python.org/simple/Scrapy/
Best match: Scrapy 1.3.3
Processing Scrapy-1.3.3-py2.7.egg
Scrapy 1.3.3 is already the active version in easy-install.pth
Installing scrapy script to /usr/local/bin

Using /usr/local/lib/python2.7/site-packages/Scrapy-1.3.3-py2.7.egg
Processing dependencies for Scrapy
Searching for pyasn1-modules
Reading http://pypi.python.org/simple/pyasn1-modules/
Best match: pyasn1-modules 0.0.8
Downloading https://pypi.python.org/packages/66/54/3c0f81c62dcb9bc055b8740d81e6b2a8e4708e347a52af4114501bfd4e54/pyasn1_modules-0.0.8-py2.7.egg#md5=f03fff5bc43106475a64a1c34d4052d7
Processing pyasn1_modules-0.0.8-py2.7.egg
Moving pyasn1_modules-0.0.8-py2.7.egg to /usr/local/lib/python2.7/site-packages
Adding pyasn1-modules 0.0.8 to easy-install.pth file

Installed /usr/local/lib/python2.7/site-packages/pyasn1_modules-0.0.8-py2.7.egg
Searching for pyasn1
Reading http://pypi.python.org/simple/pyasn1/
Best match: pyasn1 0.2.3
Downloading https://pypi.python.org/packages/af/d7/1f4825499dd387108048f994ac54145915810548010bc497f6d4d1dd1c87/pyasn1-0.2.3-py2.7.egg#md5=318dcf752351360f7893f10b29001449
Processing pyasn1-0.2.3-py2.7.egg
Moving pyasn1-0.2.3-py2.7.egg to /usr/local/lib/python2.7/site-packages
Adding pyasn1 0.2.3 to easy-install.pth file

Installed /usr/local/lib/python2.7/site-packages/pyasn1-0.2.3-py2.7.egg
Finished processing dependencies for Scrapy

```

__VERION ERROR__
```
Traceback (most recent call last):
  File "/usr/local/bin/scrapy", line 8, in <module>
    load_entry_point('Scrapy==1.3.3', 'console_scripts', 'scrapy')()
  File "build/bdist.linux-x86_64/egg/pkg_resources.py", line 318, in load_entry_point
  File "build/bdist.linux-x86_64/egg/pkg_resources.py", line 2221, in load_entry_point
  File "build/bdist.linux-x86_64/egg/pkg_resources.py", line 1954, in load
  File "/usr/local/lib/python2.7/site-packages/Scrapy-1.3.3-py2.7.egg/scrapy/cmdline.py", line 9, in <module>
    from scrapy.crawler import CrawlerProcess
  File "/usr/local/lib/python2.7/site-packages/Scrapy-1.3.3-py2.7.egg/scrapy/crawler.py", line 7, in <module>
    from twisted.internet import reactor, defer
  File "/usr/local/lib/python2.7/site-packages/Twisted-17.1.0-py2.7-linux-x86_64.egg/twisted/internet/reactor.py", line 38, in <module>
    from twisted.internet import default
  File "/usr/local/lib/python2.7/site-packages/Twisted-17.1.0-py2.7-linux-x86_64.egg/twisted/internet/default.py", line 56, in <module>
    install = _getInstallFunction(platform)
  File "/usr/local/lib/python2.7/site-packages/Twisted-17.1.0-py2.7-linux-x86_64.egg/twisted/internet/default.py", line 44, in _getInstallFunction
    from twisted.internet.epollreactor import install
  File "/usr/local/lib/python2.7/site-packages/Twisted-17.1.0-py2.7-linux-x86_64.egg/twisted/internet/epollreactor.py", line 24, in <module>
    from twisted.internet import posixbase
  File "/usr/local/lib/python2.7/site-packages/Twisted-17.1.0-py2.7-linux-x86_64.egg/twisted/internet/posixbase.py", line 18, in <module>
    from twisted.internet import error, udp, tcp
  File "/usr/local/lib/python2.7/site-packages/Twisted-17.1.0-py2.7-linux-x86_64.egg/twisted/internet/tcp.py", line 28, in <module>
    from twisted.internet._newtls import (
  File "/usr/local/lib/python2.7/site-packages/Twisted-17.1.0-py2.7-linux-x86_64.egg/twisted/internet/_newtls.py", line 21, in <module>
    from twisted.protocols.tls import TLSMemoryBIOFactory, TLSMemoryBIOProtocol
  File "/usr/local/lib/python2.7/site-packages/Twisted-17.1.0-py2.7-linux-x86_64.egg/twisted/protocols/tls.py", line 63, in <module>
    from twisted.internet._sslverify import _setAcceptableProtocols
  File "/usr/local/lib/python2.7/site-packages/Twisted-17.1.0-py2.7-linux-x86_64.egg/twisted/internet/_sslverify.py", line 38, in <module>
    TLSVersion.TLSv1_1: SSL.OP_NO_TLSv1_1,
AttributeError: 'module' object has no attribute 'OP_NO_TLSv1_1'
```





    




     

                                        
  
  
