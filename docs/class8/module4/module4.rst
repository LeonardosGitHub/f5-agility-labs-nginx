Tuning the Cache
################

|

Cache is a hardware or software component embedded in an application or device memory that automatically and temporarily stores data consumed by the user to reduce the data retrieval time and effort the next time the application or device is accessed.

|
|

1) **Turn on file caching in the Nginx proxy**

.. note:: How would caching help the performance of delivering applications?  

In NIM, edit nginx.conf, and publish changes

Uncomment the proxy_cache, line 72

.. image:: /class8/images/nim-proxy-cache.png

|
|

2) Confirm cache is opperational 
   
On NGINX Proxy cli

   `ps aux | grep nginx`

.. note:: Are there any new processes running? Look for cache manager and loader processes

|

Now review the NGINX Dashboard GUI, you should now see a Cache section 

|
|

3) **Run a test and review performance**
   
Number of Users: 500

Spawn rate: 50

Host: http://10.1.1.9/

Advanced Options, Run time: 30s

.. image:: /class8/images/locus-500-50-30.png  
   :width: 200 px

.. note::  Where you do see the preformance improvment? 
	
Review NGINX Dashboard cache section.  How much bandwidth was saved from going to upstream server?

|
|

4) **Improve reading from disk performance**

Turn on Sendfile linux system call

.. note:: What does Sendfile do?

In NIM, edit nginx.conf and publish 

Comment out "sendfile off", line 28

Uncomment "sendfile on", line 29 

|

.. image:: /class8/images/nim-sendfile.png  

	
Run the same test again.

.. note:: Were there any performace gains seen?

|
|

5) **Turn on open file cache**

.. image:: /class8/images/nim-open-file-cache.png  

In NIM, edit nginx.conf and publish

Uncomment open_file_cache, line 36

   `open_file_cache max=4096`

|

.. note:: Do you notice any improvements?  

|

.. toctree::
   :maxdepth: 2
   :hidden:
   :glob:

   
