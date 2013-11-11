Setting up WEB development environment for Maverick

- apache listen on IPV6 by default on mavericks
- install dnsmasq for resolving .dev domains
  	brew install dnsmasq
   	cp /usr/local/opt/dnsmasq/dnsmasq.conf.example /usr/local/etc/dnsmasq.conf
   	sudo cp -fv /usr/local/opt/dnsmasq/*.plist /Library/LaunchDaemons

   	# start dnsmasq
   	sudo launchctl load /Library/LaunchDaemons/homebrew.mxcl.dnsmasq.plist	

   	edit /usr/local/etc/dnsmasq.conf

	> # IPV4 ip
	> address=/dev/127.0.0.1
	> # IPV6 ip, this is important otherwise virtual hosts won't work
	> address=/dev/::1

- add resolver for dev domains
  	touch /etc/resolver/dev
  	edit /etc/resolver/dev

  	> nameserver 127.0.0.1

  	running scutil --dns should return something like this

	< resolver #8
	< domain   : dev
	< nameserver[0] : 127.0.0.1
	< flags    : Request A records, Request AAAA records
	< reach    : Reachable,Local Address  	

- set localhost as main DNS server
	this step is optional, but if your application relys in some way from the DNS
	order (like for example the dig command does) you can't automatically prepend
	localhost to the list of DNSs your DHCP gave to you.
	You have to change it manually and put 127.0.0.1 on top of the list.

	--image of network preferences

