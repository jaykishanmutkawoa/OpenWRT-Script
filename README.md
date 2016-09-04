
/*
 * Copyright (c) 2016 Jaykishan MUTKAWOA <jmutkawoa@hackers.mu>
 *
 * Permission to use, copy, modify, and distribute this software for any
 * purpose with or without fee is hereby granted, provided that the above
 * copyright notice and this permission notice appear in all copies.
 *
 * THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
 * WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
 * MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
 * ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
 * WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
 * ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
 * OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
*/


Script for messing around on OpenWRT

#dnsmasq.awk
#How to run dnsmasq.awk?

1. After having created the script on the OpenWRT machine

vim /etc/dnsmasq.conf and enter the following parameters :
log-dhcp
log-queries
log-facility=/tmp/dnsmasq.log

2. Restart the service dnsmasq

/etc/init.d/dnsmasq restart

3. Now you should notice that the logs are being generated in the /tmp.dnsmasq.log
NOTE that /var is a symbolic link to /tmp

4. To strip off interesting information from the log use the following command

tail -f /tmp/dnsmasq.log | ./dnsmasq.awk

5. You might want to exclude a specific ip address for example

root@OpenWrt:/# tail -f /tmp/dnsmasq.log | ./dnsmasq.awk | grep -v 192.168.2.231

