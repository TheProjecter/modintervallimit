# Logging Names of Threshold Exceeded Rules #

The name of rules that threshold exceeded are added to http header table with the key name of **threshold\_exceeded\_rules**.<br>
Therefore, you can add the counter info to the <a href='http://httpd.apache.org/docs/2.0/en/mod/mod_log_config.html'>CustomLog</a> by adding the <b>%{threshold_exceeded_rules}i</b> string to log format string of CustomLog directive.<br>
<br>
CustomLog Format Example:<br>
<pre><code>CustomLog logs/clicklog "%h %l %u %t \"%r\" %&gt;s %b \"%{Referer}i\" \"%{User-Agent}i\" \"%{threshold_exceeded_rules}i\"<br>
</code></pre>