# `02` Storage Exercises

Compute is nothing without state. In our case, state is a Ceph cluster with either more affordable but slower (Bulk), or more expensive but faster (NVMe SSD based) distributed storage.

## 💡 Background Information

Volumes of virtual servers are stored on separate physical hosts. As a result, our offering comes with certain storage characteristics:

1. Every byte written to a volume of a server is automatically replicated to three different disks in three different storage hosts located in three different racks, insulating it against hardware failures.

2. Every byte that is read or written crosses the network, thereby adding some latency.

This is something to be aware of with most cloud offerings: If the disks accessed by the server are local to the host they run on, a hardware failure is more likely to cause data loss. If the disks are connected over a network, a latency penalty has to be paid.

### References

* [API Documentation](https://api.cloudscale.ch)
* [Blog Post: Bulk Storage](https://www.cloudscale.ch/en/news/2016/08/17/introducing-bulk-storage)
* [Blog Post: Volume Management](https://www.cloudscale.ch/en/news/2019/01/22/flexible-management-of-ssd-and-bulk-volumes)

## 🎓 Exercises

### `02.01` - Add Additional Volumes

Using the Cloud Control Panel, create a server and add an additional Bulk and an additional SSD volume.

Be sure to format each volume with a filesystem and use a tool like `ioping` to measure the latency of the attached volumes.

Can you see a difference?

---

### `02.02` - Scale A Volume

Create a server using the API and add a volume to it. Using the Cloud Control Panel scale the volume after it has been formatted.

Can you grow the size of the volume without restarting the system?

Hint: Click on the question mark in the Cloud Control Panel near each volume for further instructions.
