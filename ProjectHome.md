## Apache Module mod\_interval\_limit Overview ##

Apache2 module that provide rule-based interval counter limits of connections per client

※ Use libmemcached-0.38 or up for mod\_interval\_limit-0.0.2 or up for the reason that the name of memcached\_st struct member (memcached\_server\_st pointer) has been changed from hosts to servers since libmemcached-0.38 (2010-02-11).


**If you have any issues or requests on this module, please post them to the following github project site:**
https://github.com/yokawasa/mod_interval_limit/issues


## News ##
  * 2013/02/17 [version 1.0.1](http://modintervallimit.googlecode.com/files/modintervallimit-1.0.1.tar.gz) released
  * 2009/11/30 [version 1.0.0](http://modintervallimit.googlecode.com/files/modintervallimit-1.0.0.tar.gz) released
  * 2009/11/08 Initial Commit

## Documentation ##
  * [Prerequisites](Prerequisites.md)
  * [Build and Install](BuildAndInstall.md)
  * [Configuration Directives](ConfigurationDirectives.md)
  * [Sample Configuration](http://github.com/yokawasa/mod_interval_limit/blob/master/sample.conf)
  * [Logging Threshold Exceeded Rules](LoggingThresholdExceededRules.md)
  * [Application Sample](ApplicationSample.md)

## Downloads ##
  * Released packages: [downloads page](http://code.google.com/p/modintervallimit/downloads/list)
  * Current source code: **http://github.com/yokawasa/mod_interval_limit/tree/master**

## Questions, Problems ##
Feel free to email me (yokawasa at gmail dot com) if you have any questions. Or always welcome if you have ideas for improvements or even patches! In addition, if you find any problems,  please report them as a new issue. see [current issues](http://code.google.com/p/modintervallimit/issues/list).

## Authors ##
Yoichi Kawasaki <yokawasa at gmail.com>