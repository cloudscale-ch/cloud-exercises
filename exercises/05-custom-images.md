# `05` Custom Images Exercises

Even though we offer a number of "off the shelf" images (like Ubuntu, Debian, or CentOS), it is often useful or even necessary to use one's own custom image. This is done by generating a disk image using a separate tool, uploading it to our object storage, and importing it as a custom image.

It is also possible to create a separate volume and copy an image there. This volume can then be used as a rescue image.

## 💡 Background Information

### References

* [API Documentation](https://api.cloudscale.ch)
* [Packer](https://www.packer.io/)
* [VirtualBox](https://www.virtualbox.org/)
* [Blog Post: Custom Images](https://www.cloudscale.ch/en/news/2020/12/09/flexible-and-efficient-thanks-to-custom-images)
* [Blog Post: Rescue Image](https://www.cloudscale.ch/en/news/2020/01/14/use-your-own-iso-usb-images)

## 🎓 Exercises

### `05.01` - Ubuntu Cloud Image

Upload an Ubuntu Cloud Image (e.g. `22.04`) as a custom image and use it to launch a new server:

https://cloud-images.ubuntu.com/

You can do this via API or through the control panel.

---

### `05.02` - Rescue Image

Create a rescue volume and use it to access the contents of another server's root volume.

---

### `05.03` - Manually Create a Custom Image (Advanced)

Using VirtualBox, create an image of your favorite Linux distribution (make sure to install cloud-init). Then import the image as a custom image and launch a new server using that custom image.

---

### `05.04` - Automatically Build a Custom Image (Advanced)

Using Packer, create an image of your favorite Linux distribution (make sure to install cloud-init). Then import the image as a custom image and launch a new server using that custom image.
