# Methods #

All calls must have be authenticated and have a valid APIKEY.

## check_in ##

```check_in``` optionally calls ```update_ipv4``` or ```update_ipv6``` when necessary (if the IP has changed). 

 * generic client checkin method
  * client initiated "head mans break" style keepalive
  * DynDNS can be turned on and automatically maintain A or AAAA record(s)
  * visit specific v4 or v6 only version of page for autodetection to work
 * can include JSON encoded data as POST data
  * system inventory (system info, software, hardware, network, etc)

Parameters:

 * HOSTNAME = [system FQDN]: mandatory
 * DDNS = [y]: default n

## update_ipv4 ##

When called, updates a zone entries A record value based on the calling IP, or the specified IP, and increments the zones serial. Optional parameters: A, TTL. 

 * When IP is specified, use this instead of the calling IP. Gets around transparent proxies in between messing up the detection.
 * When TTL is specified, change the TTL for this A record to be the specified TTL value.

Parameters:

 * HOSTNAME= [system FQDN]: mandatory

OR

 * HOST= [system hostname]: mandatory
 * ZONE= [domain or domains, comma separated]: mandatory

 * A= [IP]: optional, the IP to change A to
 * TTL= [TTL in seconds]: optional

## update_ipv6 ##

When called, updates a zone entries AAAA record value based on the calling IP, or the specified IP, and increments the zones serial. Optional parameters: AAAA, TTL. 

 * When IP is specified, use this instead of the calling IP. Gets around transparent proxies in between messing up the detection.
 * When TTL is specified, change the TTL for this AAAA record to be the specified TTL value.

Parameters:

 * HOSTNAME= [system FQDN]: mandatory

OR

 * HOST= [system hostname]: mandatory
 * ZONE= [domain or domains, comma separated]: mandatory

 * AAAA= [IP]: optional, the IP to change AAAA to
 * TTL= [TTL in seconds]: optional

## get_ipv4 ##

When called, returns the current A record for HOSTNAME or HOST + ZONE. Allows for comparison with current IP for manual updates via ```update_ipv4```

Parameters:

 * HOSTNAME= [system FQDN]: mandatory

OR

 * HOST= [system hostname]: mandatory
 * ZONE= [domain or domains, comma separated]: mandatory

## get_ipv6 ##

When called, returns the current AAAA record for HOSTNAME or HOST + ZONE. Allows for comparison with current IP for manual updates via ```update_ipv6```

Parameters:

 * HOSTNAME= [system FQDN]: mandatory

OR

 * HOST= [system hostname]: mandatory
 * ZONE= [domain or domains, comma separated]: mandatory

