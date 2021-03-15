# Cloud Exercises for the cloudscale.ch IaaS Platform
As part of our onboarding process, newly hired engineers at [cloudscale.ch](https://www.cloudscale.ch) are required to complete a set of exercises in order to get familiar with the various features of our public cloud offering. Since this can also be of educational value to our customers, partners, and other interested third-parties, we have decided to publish these exercises here on GitHub.

## Prerequisites

To follow these exercises, you need a [cloudscale.ch account](https://control.cloudscale.ch/signup), some credits, and an API token with read/write access.

> ⚠️ We strongly encourage you to activate two-factor authentication for your [cloudscale.ch account](https://control.cloudscale.ch/security/two-factor-auth) before proceeding.

## Exercises

The exercises are grouped into five distinct categories. Although they can be completed independently, they are generally meant to be completed in order:

### `01` [Compute](./exercises/01-compute.md)

Virtual servers (sometimes also referred to as "cloud servers") are our bread and butter. Since they run on different physical hosts than the storage they use, we often refer to their function as "compute". Compute exercises are all about starting and configuring virtual servers:

* `01.01` - [Launch and Delete a Server](./exercises/01-compute.md#0101---launch-and-delete-a-server)
* `01.02` - [Scale a Server](./exercises/01-compute.md#0102---scale-a-server)
* `01.03` - [Use Cloud-Init to Provision a Server](./exercises/01-compute.md#0103---use-cloud-init-to-provision-a-server)

### `02` [Storage](./exercises/02-storage.md)

Compute is nothing without state. In our case, state is a Ceph cluster with either more affordable but slower (Bulk), or more expensive but faster (NVMe SSD based) distributed storage. Storage exercises explore the relationship between virtual servers and volumes:

* `02.01` - [Add Additional Volumes](./exercises/02-storage.md#0201---add-additional-volumes)
* `02.02` - [Scale A Volume](./exercises/02-storage.md#0202---scale-a-volume)

### `03` [Network](./exercises/03-network.md)

Handing a virtual server a single public IP and calling it a day is not good enough in today's environments. Network exercises let you dive into the use of public and private networks as well as Floating IPs:

* `03.01` - [Isolated Server](./exercises/03-network.md#0301---isolated-server)
* `03.02` - [Private Network](./exercises/03-network.md#0302---private-network)
* `03.03` - [Floating IP](./exercises/03-network.md#0303---floating-ip)

### `04` [Objects](./exercises/04-objects.md)

A feature that all cloud providers *have* to offer is an S3-compatible object storage. At cloudscale.ch, we call our object storage "Objects". The Objects exercises use common S3 API tools to work with this widely used storage access layer:

* `04.01` - [s3cmd](./exercises/04-objects.md#0401---s3cmd)
* `04.02` - [AWS CLI](./exercises/04-objects.md#0402---aws-cli)

### `05` [Custom Images](./exercises/05-custom-images.md)

Even though we offer a number of "off the shelf" images (like Ubuntu, Debian, or CentOS), it is often useful or even necessary to use one's own custom image. The custom images exercises focus on building and uploading custom images:

* `05.01` - [Ubuntu Cloud Image](./exercises/05-custom-images.md#0501---ubuntu-cloud-image)
* `05.02` - [Rescue Image](./exercises/05-custom-images.md#0502---rescue-image)
* `05.03` - [Manually Create a Custom Image (Advanced)](./exercises/05-custom-images.md#0503---manually-create-a-custom-image-advanced)
* `05.04` - [Automatically Build a Custom Image (Advanced)](./exercises/05-custom-images.md#0504---automatically-build-a-custom-image-advanced)

## Contributing

If you have any questions, feedback, ideas, or if you want to contribute, feel free to [open an issue](../../issues).

## License

This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
