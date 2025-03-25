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
* [Blog Post: Volume Snapshots](https://www.cloudscale.ch/en/news/2025/02/11/volume-snapshots-pave-the-way-back)

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

---

### `02.03` - Snapshot A Volume

> Please be aware: Snapshots do not serve as a substitute for backups.

Using the Cloud Control Panel, or your favorite tool, create a new server.

Create a snapshot of your root volume, using our [API](https://www.cloudscale.ch/en/api/v1#volume-snapshots).

> A snapshot captures the state of the disk at the moment it is taken. However, only changes that are fully written and flushed to disk before the snapshot will be included in it. In contrast, any writes that were in progress at the time of the snapshot may not be fully captured.

Once the operation completes successfully, start your maintenance tasks. For this exercise, you can delete an important file, such as `/etc/passwd`, to simulate a failed maintenance. [Revert the previously created snapshot](https://www.cloudscale.ch/en/api/v1#revert-volume-to-snapshot) to restore the system to the last working state.

Once the VM has booted, does `/etc/passwd` reappear?

---

### `02.04` - Snapshot Additional Volumes

> Please be aware: Snapshots do not serve as a substitute for backups.

Using the Cloud Control Panel, or your favorite tool, create a new server and add an additional non-root volume to it.
Format the volume to ext4 with `sudo mkfs.ext4 /dev/sdb` and mount it to `/mnt`.

Create a new file on that volume and ensure it is synced to disk with fsync: `sudo dd if=/dev/zero of=/mnt/included count=1 bs=1M conv=fsync`.

> A snapshot captures the state of the disk at the moment it is taken. However, only changes that are fully written and flushed to disk before the snapshot will be included in it. In contrast, any writes that were in progress at the time of the snapshot may not be fully captured.

Create a snapshot of the additional volume, using our [API](https://www.cloudscale.ch/en/api/v1#volume-snapshots).

Now, create a second file that is not included in the snapshot: `sudo dd if=/dev/zero of=/mnt/not-included count=1 bs=1M`.

[Revert the previously created snapshot](https://www.cloudscale.ch/en/api/v1#revert-volume-to-snapshot) to restore the volume to its previous state.
You will encounter the following error message unless you first shut down your server and detach the volume before executing the restore command:
```
{
  "detail": "Cannot revert non-root volumes while they are attached to a server."
}
```
To successfully perform the revert operation, ensure that the server is powered down and the volume is detached before retrying.

Verify whether the file `/mnt/included` is present while `/mnt/not-included` is not.
Do you see the expected results?
