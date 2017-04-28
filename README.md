# Scrapy_spider

### 安装环境:
 
##### 1. server config：centos6.5

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
   
*download:`wget http://pypi.python.org/packages/source/s/setuptools/setuptools-0.6c11.tar.gz`    
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
#####   6 install `libxml2` or use `easy_install` install `lxml`
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




    




     

                                        
  
  
