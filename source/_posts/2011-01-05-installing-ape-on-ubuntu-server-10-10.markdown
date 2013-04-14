---
comments: true
date: 2011-01-05 10:29:48
layout: post
slug: installing-ape-on-ubuntu-server-10-10
title: Installing APE on Ubuntu Server 10.10
wordpress_id: 261
categories:
- HowTo
tags:
- ape
- comet
---

> [![](http://static.weelya.com/weelya_ape/imgs/ape_opensource_home.png)](http://ape-project.org/)
This small tutorial was made based on the ape-project [install documentation](http://www.ape-project.org/wiki/index.php/Setup).

It summarizes things to help people get APE running on Ubunto ASAP.

Hope it helps someone who needs a good comet server up and running for yesterday :)


The environment I have choosed to install APE was a virtual machine with this configuration:



	
  * Ubuntu Server 10.10 x64

	
  * 1GB of memory

	
  * 5GB of hard disk

	
  * ssh<!-- more -->


1. Download the APE complete package (server and jsf)

	
  * You can find it here: [http://www.ape-project.org/files.php?f=APE-Project_1.0.tar.gz&v=1.0](http://www.ape-project.org/files.php?f=APE-Project_1.0.tar.gz&v=1.0)


2. You must download the libmysqlclient15off

	
  * 32-bits: [http://packages.ubuntu.com/karmic/i386/libmysqlclient15off/download](http://packages.ubuntu.com/karmic/i386/libmysqlclient15off/download)

	
  * 64-bits: [http://packages.ubuntu.com/karmic/amd64/libmysqlclient15off/download](http://packages.ubuntu.com/karmic/amd64/libmysqlclient15off/download)


3. To install libmysqlclient at ubuntu just type

	
  * 32-bits: _dpkg -i      libmysqlclient15off_5.0.51a-3ubuntu5.8_i386.deb_

	
  * 64-bits: _dpkg -i libmysqlclient15off_5.0.51a-3ubuntu5.8_amd64.deb_


4. Now it is time to install APE server

	
  * 32-bits: _dpkg -i      APE_Server-1.0.i386.deb_

	
  * 64-bits: _dpkg -i      APE_Server-1.0.amd64.deb_




> If you got the error message bellow, it means you forgot to install libmysql. To fix that you just have to type _apt-get install -f_

[![](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2011/01/libmysql-no-install-error.png)](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2011/01/libmysql-no-install-error.png)


5. Go setup your comet server



6. Now it is time to start it


> Remember that we set APE to be on port 80. Make sure you don't have apache, nginx or other program on that port.

If you have, the server won't start.





	
  * /etc/init.d/ape-server start


That's it. You should be seeing the **[OK]** of victory.

If you can't get it running try first:



	
  * see the log (it's on /var/log/ape.log)

	
  * make sure you don't have other program on port 80 (like apache or nginx)

	
  * if all fails, go take a look [here](http://www.ape-project.org/wiki/index.php/APE_Server_does_not_start)

	
  * if still lost, go to the [user group](http://groups.google.com/group/ape-project) and ask for help (there are great guys there that will be glad to help)




> The next step is to set up the jsf and the check utility to see your new toy working.

I'll cover that on other post.
