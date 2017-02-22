---
layout: post
title:  "How to setup vagrant virtual box on Mac"
date:   2017-02-22 13:00:00 +0530
categories: github
---

Whenever we are working on a project that needs testing on old IE browsers,
we neeed to look for ways to test website on internet explorer.
Browserstack helps meets these expectations. Still, it comes at a cost.
In this post, we will discuss how to setup vagrant with desired virtual box
of internet explorer to test things out on local environment without any hassle.

**Note**: I have tested this on Mac and it works.
Let me know if anyonce faces any problems through this.

Here are the steps to setup vagrant with internet explorer 11 virtual box.

### Steps

#### 1. Install vagrant

Install vagrant from https://www.vagrantup.com/downloads.html

#### 2. Download virtual box

Download desired virtual box from [Windows Dev](https://dev.windows.com/en-us/microsoft-edge/tools/vms/mac/). I used [IE11.Win7.For.Vagrant.box](https://modernievirt.blob.core.windows.net/vhd/VMBuild_20140627/Vagrant/IE11.Win7.For.Vagrant.box)

#### 3. Create vagrant directory

Let's say we create directory `vagrant-windows-ie11`

```bash
$ mkdir -p vagrant-windows-ie11
```

Change directory to newly created directory.

```bash
$ cd vagrant-windows-ie11
```

#### 4. Configure

Use below given commands to configure virtual box with vagrant -

Initialize vagrant by command,
```bash
$ vagrant init windows
```

```bash
$ vagrant box add ~/Downloads/IE11.Win7.For.Vagrant.box --name=windows
```
Replace path with your downloaded virtual box path.

Start the vagrant by command,
```bash
$ vagrant up
```

This will start VM with the box configured with vagrant.
