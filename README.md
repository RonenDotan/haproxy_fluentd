# haproxy_fluentd

This is an example of using haproxy's abbility and also log.



Traffic first reach external-lb - the first load balancer.
using several limit on the same ip 
then based on tag and tag mapping adding publisher and decide:
1. Redirect or not
2. new serving or not

By mapping country code to a sub-domain, redirecting to the appropriate load balancer. (old or new serving type)


see :
haproxy_fluentd/external-lb/etc/haproxy/haproxy.cfg




Then Traffic reaches the regional load balancer.
each time a user arrives here a repetition number is set (using ip and stick tables)
each repetition number has a unique demand connected to (based on country and othe properties).
also, saves repetition for network so traffic would not send again to the same offer.

create a unique-id (scidu)

detect blocking type by allowed response

sends data to log (syslog => td-agent(fluentd))





