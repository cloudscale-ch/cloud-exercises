# `01` Compute Exercises

Virtual servers (sometimes also referred to as "cloud servers") are our bread and butter. Since they run on different physical hosts than the storage they use, we often refer to their function as "compute".

## 💡 Background Information

### Compute Flavors

Currently, our servers come in two different types of compute flavors:

* **Flex** - CPU cores are shared between virtual servers; these flavors provide room for short-term load peaks and are ideal for most applications.
* **Plus** - The physically available computing power is not overcommitted; these flavors provide consistent CPU performance and are ideal for demanding workloads.

See https://www.cloudscale.ch/en/pricing for more details.

### Cloud Control Panel & API

Servers can be launched in two different ways:

* Through the Cloud Control Panel (https://control.cloudscale.ch).
* Through the REST API (https://api.cloudscale.ch).

The API can be used in various ways:

* Using an HTTP client (Curl, Python Requests library etc.).
* Using our [official CLI](https://cloudscale-ch.github.io/cloudscale-cli/).
* Using our [Ansible cloud collection](https://docs.ansible.com/ansible/latest/collections/cloudscale_ch/cloud/).
* Using our [Terraform provider](https://registry.terraform.io/providers/cloudscale-ch/cloudscale/latest/docs).

### References

* [API Documentation](https://api.cloudscale.ch/)
* [Blog Post: Plus Flavors](https://www.cloudscale.ch/en/news/2019/11/19/even-more-power-thanks-to-plus-flavor)
* [Blog Post: Our API](https://www.cloudscale.ch/en/news/2016/11/03/workflow-automation-with-our-new-api)
* [Blog Post: Our CLI](https://www.cloudscale.ch/en/news/2020/09/15/cloudscale-cli-now-available)
* [Blog Post: Ansible (1/2)](https://www.cloudscale.ch/en/news/2017/05/17/ansible-cloud-module-and-libcloud-integration)
* [Blog Post: Ansible (2/2)](https://www.cloudscale.ch/en/news/2020/12/21/cloud-orchestration-with-ansible-collections)
* [Blog Post: Terraform (1/2)](https://www.cloudscale.ch/en/news/2017/11/01/infrastructure-as-code-with-terraform)
* [Blog Post: Terraform (2/2)](https://www.cloudscale.ch/en/news/2019/12/23/latest-features-with-terraform)
* [Blog Post: Cloud-Init (1/2)](https://www.cloudscale.ch/en/news/2016/07/21/improved-efficiency-comfort-and-control)
* [Blog Post: Cloud-Init (2/2)](https://www.cloudscale.ch/en/news/2020/06/23/initialize-servers-with-cloud-init)


## 🎓 Exercises

### `01.01` - Launch and Delete a Server

Using the following tools, launch and delete a server (once per each tool):

* Your library of choice (Curl, Python Requests library etc.).
* An Ansible playbook.
* A Terraform config.
* The [official CLI](https://github.com/cloudscale-ch/cloudscale-cli).

Make sure to connect to each server before deleting it to ensure that it actually booted correctly.

---

### `01.02` - Scale a Server

Using your favorite tool, create a `flex-2` instance, then turn it into a `plus-8` instance.

---

### `01.03` - Use Cloud-Init to Provision a Server

Virtual servers launched on IaaS platforms usually need some kind of initial provisioning (interface configuration, hostname, SSH authorized keys). The de-facto industry standard is using cloud-config for cloud-init. Learn more about it and try launching a server using cloud-init to install nginx right after boot, without any additional intervention.
