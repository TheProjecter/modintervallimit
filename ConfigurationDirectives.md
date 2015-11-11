# Configuration Directives #

All the directives below may be specified in anywhere like Server, VirtualHost, Location, and so on.

## IntervalLimitEngine ##

| **Description** | Set "On" to enable interval\_limit, "Off" to disable. Default "Off" |
|:----------------|:--------------------------------------------------------------------|
| **Syntax**      | IntervalLimitEngine On/Off                                          |
| **Context**     |  server config, virtual host, directory, .htaccess                  |
| **Status**      | Extension                                                           |
| **Module**      | mod\_interval\_limit                                                |

## IntervalLimitCookieName ##

| **Description** | Set key name of cookie so as for the cookie value to be used for user's identification. <br> It is required when "cookie" is choosed as a user identifier in IntervalLimitRule directive. <br>
<tr><td> <b>Syntax</b>   </td><td> IntervalLimitCookieName cookieName                                                                                                                                                        </td></tr>
<tr><td> <b>Context</b>  </td><td>  server config, virtual host, directory, .htaccess                                                                                                                                        </td></tr>
<tr><td> <b>Status</b>   </td><td> Extension                                                                                                                                                                                 </td></tr>
<tr><td> <b>Module</b>   </td><td> mod_interval_limit                                                                                                                                                                        </td></tr></tbody></table>

<h2>IntervalLimitMemcachedAddrPort ##

| **Description** | Liste of the memcached address. each address is ip or host <br> adresse(s) and port ':' separated. The addresses are ',' coma separated. <br> For example: <br> 192.168.1.1:11211,192.168.1.2:11211 <br>
<tr><td> <b>Syntax</b>   </td><td> IntervalLimitMemcachedAddrPort host1:port1,host2:port2,..                                                                                                                                           </td></tr>
<tr><td> <b>Context</b>  </td><td>  server config, virtual host, directory, .htaccess                                                                                                                                                  </td></tr>
<tr><td> <b>Status</b>   </td><td> Extension                                                                                                                                                                                           </td></tr>
<tr><td> <b>Module</b>   </td><td> mod_interval_limit                                                                                                                                                                                  </td></tr></tbody></table>

<h2>IntervalLimitRule</h2>

<table><thead><th> <b>Description</b> </th><th> Set an interval limit rule line. Multiple rules can be defined at once. <br>Maximum number of rules is 5, and if you define more than 5 rules, <br>you will get error message in configuration process.<br> @see <b>IntervalLimitRule Format</b> below for the detail of rule line format. </th></thead><tbody>
<tr><td> <b>Syntax</b>      </td><td> IntervalLimitRule rule                                                                                                                                                                                                                                                                     </td></tr>
<tr><td> <b>Context</b>     </td><td>  server config, virtual host, directory, .htaccess                                                                                                                                                                                                                                         </td></tr>
<tr><td> <b>Status</b>      </td><td> Extension                                                                                                                                                                                                                                                                                  </td></tr>
<tr><td> <b>Module</b>      </td><td> mod_interval_limit                                                                                                                                                                                                                                                                         </td></tr></tbody></table>

<br>
<br>

<h1>IntervalLimitRule Format</h1>

<h2>IntervalLimitRule <code>&lt;</code>rule_name<code>&gt;</code> <code>&lt;</code>type:ip|cookie<code>&gt;</code> <code>&lt;</code>max event<code>&gt;</code> <code>&lt;</code>interval(sec)<code>&gt;</code> <code>&lt;</code>block period(sec)<code>&gt;</code> <code>&lt;</code>block:1|0<code>&gt;</code></h2>

<table><thead><th> <b>NAME</b>        </th><th> <b>VALUE</b> </th><th>  <b>DESCRIPTION</b> </th></thead><tbody>
<tr><td> <b>rule name</b>   </td><td>              </td><td> The name of rule. each name must be unique. </td></tr>
<tr><td> <b>type</b>        </td><td> <b>ip</b> or <b>cookie</b> </td><td> The type of user identifier. the value must be either ip or cookie. <br> - <b>ip</b> : ip address of incomming request. <br> - <b>cookie</b> : cookie value of incomming request.<br> <code>[</code>note<code>]</code> If cookie is choosed, the key name of cookie must be specified with <b>IntervalLimitCookieName</b> directive.</td></tr>
<tr><td> <b>max event</b>   </td><td> <b>1</b> -   </td><td> The maximum number of events allowed to access in the certain period of time, <b><code>&lt;</code>interval<code>&gt;</code></b> </td></tr>
<tr><td> <b>interval</b>    </td><td> seconds      </td><td>The time interval, in seconds, at which the number of event counter will be checked. </td></tr>
<tr><td> <b>block period</b> </td><td> seconds      </td><td> The time period, in seconds, during which a requesting user is considered as <br>"exceeded threshold" if the user's interval event counter exceeds <b><code>&lt;</code>max event<code>&gt;</code></b>.<br> If <b><code>&lt;</code>block<code>&gt;</code></b> is equal to <b>1</b>, the requesting user's access is blocked as <b>HTTP_SERVICE_UNAVAILABLE</b> <br> during the block period. After the block period, the counter is reset to 0.</td></tr>
<tr><td> <b>block</b>       </td><td> <b>1</b> or <b>0</b> </td><td> must be either <b>1</b> or <b>0</b>. <br> - <b>1</b>  : block the user access as <b>HTTP_SERVICE_UNAVAILABLE</b> during the block period. <br>- <b>0</b>  : NOT block the user access during the block period. <br>this means nothing change even if the user's interval event counter exceeds the threshold.</td></tr></tbody></table>

<h2>EXAMPLES of IntervalLimitRule</h2>
<pre><code>    ex1.<br>
    IntervalLimitRule rule_ip1 ip 10 60 60 1<br>
    #------------------------------------------------------------<br>
    # rule name        : "rule_ip1"<br>
    # user identifier  : "ip"<br>
    # max event        : 10<br>
    # interval         : 60 sec<br>
    # block period     : 60 sec<br>
    # block            : 1 - block the user access<br>
    #------------------------------------------------------------<br>
<br>
    ex2.<br>
    IntervalLimitRule rule_ip2 ip 100 3600 3600 0<br>
    #------------------------------------------------------------<br>
    # rule name        : "rule_ip2"<br>
    # user identifier  : "ip"<br>
    # max event        : 100<br>
    # interval         : 3600 sec (1hr)<br>
    # block period     : 3600 sec (1hr)<br>
    # block            : 0 - NOT block<br>
    #------------------------------------------------------------<br>
<br>
    ex3.<br>
    IntervalLimitRule rule_cookie1 cookie 10 60 60 1<br>
    #------------------------------------------------------------<br>
    # rule name        : "rule_cookie1"<br>
    # user identifier  : "cookie"<br>
    # max event        : 10<br>
    # interval         : 60 sec<br>
    # block period     : 60 sec<br>
    # block            : 1 - block the user access<br>
    #------------------------------------------------------------<br>
</code></pre>