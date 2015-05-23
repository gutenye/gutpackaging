Guten Packaging, Packaging Automation
=====================================

First, let's find out what people say about packaging:

* [Revisiting How We Put Together Linux Systems](http://0pointer.net/blog/revisiting-how-we-put-together-linux-systems.html) by Pid Eins

Second, look at the existing packaging systems:

* [Arch Linux Packaging](https://wiki.archlinux.org/index.php/Creating_packages)
* [Debian Packaging](https://wiki.debian.org/Packaging)
* [Ubuntu Snappy Packaging](https://developer.ubuntu.com/en/snappy/tutorials/build-snaps)
* [GNOME Sandboxed Applications](https://blogs.gnome.org/mclasen/2015/01/21/sandboxed-applications-for-gnome)

Future is bright, as for now, here are my solutions:

### As an author of a project, I want

```
$ git tag v1.0.0
$ git push --tags
```

It'll publish a new package.

### As a maintainer of a package, I want

```
$ do nothing
```

It'll check upstream version changes every day and publish a new package.

* For Arch Linux, read [Arch Linux Guide](https://github.com/gutenye/gutpackaging/blob/master/Arch Linux Guide.md)
* For Debian/Ubuntu, read [Debian Guide](https://github.com/gutenye/gutpackaging/blob/master/Debian Guide.md)
