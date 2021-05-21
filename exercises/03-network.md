# `03` Network Exercises

Handing a virtual server a single public IP and calling it a day is not good enough in today's environments. Customers require additional features:

* Private networks between virtual servers.
* Virtual servers that do not use a public IP address at all.
* IP addresses that can be reassigned to other servers.

## 💡 Background Information

### References

* [API Documentation](https://api.cloudscale.ch)
* [Blog Post: Floating IPs](https://www.cloudscale.ch/en/news/2017/04/20/high-availability-using-floating-ips)
* [Blog Post: Floating Networks](https://www.cloudscale.ch/en/news/2017/07/06/more-flexibility-with-floating-networks)
* [Blog Post: Private Networking](https://www.cloudscale.ch/en/news/2016/07/04/private-networking-available)
* [Blog Post: Multiple Private Networks](https://www.cloudscale.ch/en/news/2019/10/25/segmentation-with-multiple-private-networks)
* [Blog Post: Managed DHCP for Private Networks](https://www.cloudscale.ch/en/news/2020/04/03/mastering-the-private-network-with-managed-dhcp)
* [Blog Post: Increasing Availability Using Anti-Affinity](https://www.cloudscale.ch/en/news/2016/10/21/increasing-availability-using-anti-affinity)

## 🎓 Exercises

### `03.01` - Isolated Server

Using the API, create a server that has no public IP address and can only be reached through another server that acts as its firewall and gateway.

This requires some work on both servers after they are created. You can either use `iptables` to forward packets to the private server, or you can use `nginx` to proxy requests to the private server.

---

### `03.02` - Private Network

Using the API, create a private network without DHCP and statically configure two servers inside that network to communicate with each other over the private network.

It is fine if both of those servers are also connected to the Internet. The only requirement is that they can talk to each other over a private link.

---

### `03.03` - Floating IP

Create two servers and run an HTTP server on each of them. When queried over HTTP, they should return their respective hostnames.

Assign a Floating IP to one server, then switch the Floating IP to the second server. Observe how the HTTP response changes when you repeatedly run `curl` against the Floating IP.

Since this is a simple way of implementing a high-availability setup, those two servers should not be running on the same physical host. Make sure to create a server group and launch the two servers in anti-affinity to further increase the resiliency of your setup.
