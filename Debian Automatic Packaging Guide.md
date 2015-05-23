Common Setup
--------

1. [Create a GPG key](http://www.dewinter.com/gnupg_howto/english/GPGMiniHowto-3.html#ss3.1)

2. Create an APT Repository

```
$ aptly repo create -distribution=debian default
$ aptly publish repo default
```

3. Upload to Github

```
$ gutdeb upload
```

As Author of a Project
----------------------

You can find a example at [here](https://github.com/gutenye/gutdeb)

1. Install [drone](https://github.com/drone/drone)

2. Create .drone.yml

```
image: gutenye/debian-devel
cache:
  - /root/.aptly
  - /root/.gnupg
  - /root/.gitconfig

deploy:
  bash:
    script:
      - cd misc/deb && gutdeb publish $(cat ../../VERSION)
```

3. Settings

```
Create a new SSH deploy key with empty passphrase

  $ ssh-keygen -N '' -f ~/.ssh/id_rsa
  $ Add this key to a Github repository as a deploy key

Upload ssh key to drone

  $ drone set-key <repo> ~/.ssh/deploy

Create a new GPG key with empty passphrase

  $ gpg --full-key-gen

Set git configuration

  $ git config --global user.email "you@example.com"
  $ git config --global user.name "Your Name"

Setup Environment Variable

  DEBFULLNAME="x"
  DEBEMAIL="x"
```

As Maintainer of a Package
--------------------------

You can find a example at [here](https://github.com/gutenye/debs)

1. Install gutdeb(https://github.com/gutenye/gutdeb)

```
# apt install gutdeb
```

2. Put packages in /app/debs

3. Settings

```
Create a new SSH deploy key with empty passphrase

  $ ssh-keygen -N '' -f ~/.ssh/id_rsa
  $ Add this key to a Github repository as a deploy key

Create a new GPG key with empty passphrase

  $ gpg --full-key-gen

Set git configuration

  $ git config --global user.email "you@example.com"
  $ git config --global user.name "Your Name"
```

4. Start timer

```
# systemctl start gutdeb-autopublish.timer
# systemctl enable gutdeb-autopublish.timer
```
