# 1. Application Sample to Lookup Env #

!mod\_interval\_limit adds the names of threshold exceeded rules to apache subprocess\_env table with the key named "**threshold\_exceeded\_rules**". Therefore, you can lookup the info like this below:

## PHP Script ##
```
<?php
 $count = getenv ( "threshold_exceeded_rules" );
?>
```
see also: [env\_check.php](http://github.com/yokawasa/mod_interval_limit/blob/master/scripts/env_check.php)

## PERL Script ##
```
#! /usr/bin/perl
my $count = $ENV{ "threshold_exceeded_rules" };
```
see also: [env\_check.pl](http://github.com/yokawasa/mod_interval_limit/blob/master/scripts/env_check.pl)