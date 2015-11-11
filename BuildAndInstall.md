# Build and Install mod\_interval\_limit #

1) extract files from an archive
```
tar zxf modintervallimit-<VERSION>.tar.gz
cd modintervallimit-<VERSION>
```
Or you can check out current source code from master repo
```
git clone git://github.com/yokawasa/mod_interval_limit.git
cd mod_interval_limit
```

2) open Makefile and modify ap\_basedir variable
```
vi Makefile
 ap_basedir=/PATH-TO-APACHE-BASE
```
see [Makefile](http://github.com/yokawasa/mod_interval_limit/blob/master/Makefile)

3) make and install
```
make
sudo make install
```
after done configuration, don't forget to stop and start apache
```
sudo make stop 
sudo make start
```