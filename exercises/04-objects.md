# `04` Objects Exercises

A feature that all cloud providers *have* to offer is an S3-compatible object storage. At cloudscale.ch, we call our object storage "Objects". Our object storage is powered by RADOS Gateway, a Ceph service that offers an S3-compatible API to store and retrieve objects. Customers use the object storage for serving big files, website artifacts, Docker images, etc.

There are a lot of things that can be done with S3, for example offering an upload form for anonymous users. As an engineer at cloudscale.ch you should at least be familiar with `s3cmd` and `aws s3api`, both CLIs designed to deal with S3 services.

## 💡 Background Information

### References

* [API Documentation](https://api.cloudscale.ch)
* [s3cmd](https://s3tools.org/s3cmd)
* [AWS CLI](https://docs.aws.amazon.com/cli/latest/reference/s3/)
* [Blog Post: Object Storage (1/3)](https://www.cloudscale.ch/en/news/2017/06/30/launch-of-our-s3-compatible-object-storage)
* [Blog Post: Object Storage (2/3)](https://www.cloudscale.ch/en/news/2017/08/28/ready-to-go-with-our-object-storage)
* [Blog Post: Object Storage (3/3)](https://www.cloudscale.ch/en/news/2020/01/17/object-storage-new-urls)

## 🎓 Exercises

### `04.01` - s3cmd

Using `s3cmd`, create a bucket, upload a file, and make it publicly accessible.

---

### `04.02` - AWS CLI

Create a bucket using `aws s3api`, enable objects versioning and upload a file several times, slightly changing its content each time. Can you recover a previous version of the file? What do you need to do in order to delete the bucket again?
