# One-Way Stagers for Windows
Shellcodes for Windows that allow to reuse connections. This is really useful for evading restrictive environments where it is not possible to obtain a reverse shell by creating a new connection. The idea of this repository is to collect functional POCs and/or new innovative techniques (apart from the [old-school techniques](http://phrack.org/issues/62/7.html): findtag, getpeername, etc.). Feel free to contribute.


* **One-Way shellcode based on socket's lifetime:** take advantage of the service timeout to extend the lifetime of the connection to make it distinguishable from others sockets. After that idle time we can use the getsockopt API along with SO_CONNECT_TIME (SOL_SOCKET option) to go through all the handles and identify the socket whose lifetime exceeds X seconds. NAT inmmune. More information: https://www.shelliscoming.com/2018/06/windows-reuse-shellcode-based-on.html
* **One-Way shellcode using Out Of Band data:** it sends Out-of-Band data (just one byte is needed) in some packet/packets just before the Stager starts to run. To find the handle the Stager would only need to bruteforce the list of posible sockets looking for the one with OOB pending to be read (by using recv with the MSG_OOB flag). NAT inmmune. More information: https://www.shelliscoming.com/2019/03/one-way-shellcode-for-firewall-evasion.html
