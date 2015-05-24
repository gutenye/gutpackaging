As Author of a Project
----------------------

You can find an example at [here](https://github.com/gutenye/gutbackup)

1\. Install [drone](https://github.com/drone/drone)

2\. Create .drone.yml

```
image: gutenye/archlinux-devel
deploy:
  bash:
    script:
      - chown docker:docker -R misc/aur
      - su docker -c 'cd misc/aur && gutaur publish $(cat ../../VERSION)'
```

3\. Setup Environment Variable

```
AUR_USERNAME=x
AUR_PASSWORD=y
```

As Maintainer of a Package
--------------------------

You can find an example at [here](https://github.com/gutenye/aurs)

Define a `_watch` in PKGBUILD

```
_watch=("https://github.com/gutenye/gutbackup/tags" "v([-.\d]+).tar.gz")
```

**If you're using Arch Linux**

1\. Install gutaur

```
$ pacaur -S gutaur
```

2\. Put PKGBUILDs into /app/aurs

3\. Setup Environment Variable

```
AUR_USERNAME=x
AUR_PASSWORD=y
```

4\. Start timer

```
# systemctl start gutaur-autopublish.timer
# systemctl enable gutaur-autopublish.timer
```

**If you're using Ubuntu Server**

1\. Install docker

2\. Prepare

```
docker pull gutenye/archlinux-autopublish
```

3\. Download and edit [gutaur-autopublish.{service,timer}](https://github.com/gutenye/gutaur/blob/master/misc/docker) to /etc/systemd/system

4\. Start timer

```
# systemctl start gutaur-autopublish.timer
# systemctl enable gutaut-autopublish.timer
```
