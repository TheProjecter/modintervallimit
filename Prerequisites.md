# Prerequisites of mod\_interval\_limit #

| software | description |
|:---------|:------------|
| **[libevent](http://www.monkey.org/~provos/libevent/)** |  used by memcached |
| **[memcached](http://www.danga.com/memcached/)** | used as block floag and count storage. |
| **[libmemcached](http://libmemcached.org/libMemcached.html)** | used as memcached c client library |

**`[`note`]`**<br>
<b>- memcached-1.4.0 or up, which implements binary protocol, is highly recommended for performance reanson.</b> <br>
<b>- Use libmemcached-0.38 or up for mod_interval_limit-1.0.1 or up</b>