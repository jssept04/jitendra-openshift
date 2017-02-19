Vagrant's Linux Desktop Environment for Windows &amp; Mac
=

By: [Pablo Carranza](https://plus.google.com/107285164064863645881?rel=author) | [vDevices](http://www.vdevices.com/)

### This Project's Purpose

To provide a _simple_  (while not the only) way for Windows &amp; Mac users to launch a virtual machine ("VM") with a Linux Desktop environment &ndash; sandboxed on their local computer.

### Contributing

Contributions are more than welcome:

>If you are new to the wonderful world of [git](http://git-scm.com/) (version control) &ndash; and/or are uncomfortable with the command line &ndash; download [GitHub for Windows](http://windows.github.com/) or [GitHub for Mac](http://mac.github.com/).

1. Fork this repo. *See* [Fork A Repo | GitHub Help](https://help.github.com/articles/fork-a-repo).
1. Create a branch (`git checkout -b my_feature_branch`).
1. Commit your changes (`git commit -am "Added a sweet feature"`).
1. Push to the branch (`git push origin my_feature_branch`).
1. Create a Pull Request from your branch into the master branch of this repo (please be sure to provide enough detail, so I can decipher your proposed changes). *See* [Collaborating | GitHub Help](https://help.github.com/categories/63/articles).

## Introduction

For many years, there were barriers surrounding the many unsatisfied Microsoft Windows users yearning for more and some Mac OS X users that developed an itch for tinkering with open-source tools. Namely, they did not have:

* the cash-flow or desire to pick up a dedicated Linux box; _or_
* the technical expertise to create a dual-boot environment &ndash; that is, a partition on their local hard drive from which to boot a Linux environment, side-by-side with Windows.
	* Besides, dual-boot environments carry the inconvenience of having to reboot your computer every time you want to work with the other OS (so much for multitasking!).

Well, ladies 'n gentlemen ... drum roll, please ...

## Meet VirtualBox

VirtualBox is a cross-platform, open-source "[virtualization](https://www.virtualbox.org/wiki/Virtualization) product for enterprise as well as home use." VirtualBox is installed _on_ an existing **host** operating system ("OS") &ndash; such as Windows or Mac OS X &ndash; as an application, i.e. a VM. While running as an application/VM on your computer, VirtualBox then allows a **guest** OS to be loaded and run, within its own virtual environment. Thus, VirtualBox can be used to run a virtual Linux computer _inside_ your Mac or Windows PC, as opposed to next to it (such as in a dual-boot configuration).

To deploy a VM on one's computer, the user must first create a VM within VirtualBox and properly configure the slew of possible options. While this is *really* not as difficult as it sounds, the prospect can seem daunting to non-computer-geeks. Such unfortunates are in luck, however.

## Meet Vagrant

[Vagrant](http://www.vagrantup.com) is also a cross-platform, open-source tool. After you install VirtualBox on your computer, Vagrant itself makes it so you do not need to deal with VirtualBox directly. Vagrant was created for software developers, so they could build and share computing environments with other developers. It works with [virtualization](http://en.wikipedia.org/wiki/X86_virtualization) software such as [VirtualBox](https://www.virtualbox.org/) to provide a virtual machine (on your local Mac or Windows PC) that is sandboxed, or sectioned-off, from your local environment.

### A Match Made in Heaven

Many users run a guest OS inside of VirtualBox without Vagrant. However,

* Vagrant saves you the trouble of having to build a guest OS from scratch;
* By simply downloading a pre-packaged virtual machine running a particular guest OS, named a [vagrant box](http://docs.vagrantup.com/v2/boxes.html);
* While supporting customization via the [Vagrantfile](http://docs.vagrantup.com/v2/vagrantfile/machine_settings.html). The primary function of the Vagrantfile is to describe the type of VM required for a project and how to configure and provision the machine.

Other possible VirtualBox configurations (although, outside the scope of this project) are:

* Run a Windows 7, or Windows XP, VM on a Windows 8 machine;
* Run Max OS X on Windows;
* Run Windows programs and, consequently, the Windows OS, on a Mac;
* And more!

## How to Deploy

1. Start with any operating system ("OS").

1. Install the most recent release of [VirtualBox](https://www.virtualbox.org/wiki/Downloads), for your OS.

	>Once VirtualBox is installed, also install the corresponding [VirtualBox Extension Pack](https://www.virtualbox.org/wiki/Downloads).

1. Install the most recent release of [Vagrant](http://www.vagrantup.com/downloads.html), for your OS.

	* `vagrant` will now be available as a command in your terminal or Windows Command Prompt.
		* **Microsoft Windows users:** Can open a command prompt by pressing (on the keyboard) the `Windows` key followed by the `R` key, which will open the `Run` dialog box, and typing:

				cmd

			and pressing `Enter`. 
    
	* **Note:** If Vagrant is already installed, use `vagrant -v` to check the version. You may want to consider [upgrading](http://docs.vagrantup.com/v2/installation/upgrading.html) if a much older version is in use.

1. Clone or extract the project's repository into a local directory, e.g.

	* `git clone git://github.com/vDevices/Vagrant-LinuxDesktop.git vagrant-desktop`
	* **OR** use [GitHub for Windows](http://windows.github.com/) or [GitHub for Mac](http://mac.github.com/) by clicking on the `Clone in Desktop` button
	* **OR** download and extract the repository master [zip file](https://github.com/vDevices/Vagrant-LinuxDesktop/archive/master.zip)

1. Change into the new directory with `cd vagrant-desktop`

	#### The First `vagrant up`

1. Start the Vagrant environment by executing the command: `vagrant up`
    * Be patient as the magic happens. This could take a while on the first run as your local machine downloads the required files &amp; updates.

### What Did That Do?

The first time you run `vagrant up`, a packaged `box`  from the [Ubuntu Cloud Images](http://cloud-images.ubuntu.com/) repository, containing a basic virtual machine, is downloaded to your local computer and cached for future use. The default `Vagrantfile` used by `Vagrant's Linux Desktop Environment for Windows & Mac` contains an installation of `Ubuntu 12.04 LTS 32-bit`.

After this `box` is downloaded, it begins to boot as a sandboxed virtual machine using VirtualBox. Once booted, it runs the included provisioning script, to install the Ubuntu desktop environment.

* **Note:** Ubuntu's default desktop environment ("DE") is [Unity](http://en.wikipedia.org/wiki/Unity_(user_interface)). Feel free to modify the provisioning script (`bootstrap.sh`), if you would prefer a different DE, such as [GNOME](http://en.wikipedia.org/wiki/GNOME).

The time for all of this to happen depends a lot on the speed of your Internet connection. If you are on a fast cable connection, it will likely only take several minutes.

On future runs of `vagrant up`, the packaged `box` will be cached on your local machine and Vagrant will again apply the provisioning script, only if specifically requested.

* ***Preferred:*** If the virtual machine has been powered off with `vagrant halt`, `vagrant up` will quickly power on the machine without provisioning.
* ***Rare:*** If you would like to reapply the provisioning script with `vagrant up --provision` or `vagrant provision`, some time will be taken to check for updates and packages that have not been installed.
* ***Very Rare:*** If the virtual machine has been destroyed with `vagrant destroy`, it will need to download the full package data on the next `vagrant up`.

## How to Use

Now that you're up and running, start poking around and modifying things.

1. Your Windows or Mac desktop should now be substituted by a full-screen Linux desktop environment. Log in with the username `vagrant` and password `vagrant`.
1. You can also access the VM via the command line with the `vagrant ssh` command from your local `Vagrant-LinuxDesktop` directory. You can do almost anything you would do with a standard Ubuntu installation.
	* **MS Windows users:** An SSH client is generally not distributed with Windows PCs, by default. However, a terminal emulator such as [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) will provide access immediately. For detailed instructions on connecting with PuTTY, consult the [Vagrant-LinuxDesktop wiki](https://github.com/vDevices/Vagrant-LinuxDesktop/wiki/Connect-to-Your-Vagrant-Virtual-Machine-with-PuTTY).
1. Power off the VM with `vagrant halt` and turn it back on with `vagrant up`.
1. Suspend the VM's state in memory with `vagrant suspend` and bring it right back with `vagrant resume`.
1. Reapply provisioning to a running VM with `vagrant provision`.
1. Destroy the VM and start from scratch with `vagrant destroy`.

## Vagrant `box`

One concept to be mindful of is Vagrant's use of [boxes](http://docs.vagrantup.com/v2/boxes.html). Vagrant uses `.box` files as templates from which to spin up a new VM. Instead of building a VM from scratch &ndash; which would be a slow and tedious process because you would first have to create a VM in VirtualBox and configure the proper settings &ndash; Vagrant uses a base, combined image of both a properly-configured VirtualBox VM with a guest OS already installed, to quickly clone a VM.

Such an individual base image is referred to as a `box`. Feel free to swap-out the URL in the `config.vm.box_url` directive of this project's [Vagrantfile](http://docs.vagrantup.com/v2/vagrantfile/machine_settings.html) &ndash; that provides the default Ubuntu `box` &ndash; with the URL of either of the official Vagrant `box`es:

* **Ubuntu 12.04 32-bit:** [http://files.vagrantup.com/precise32.box](http://files.vagrantup.com/precise32.box)
* **Ubuntu 12.04 64-bit:** [http://files.vagrantup.com/precise64.box](http://files.vagrantup.com/precise64.box)

or with a `box` URL from either of the following repositories hosting VM, or guest OS, images:

* [Ubuntu Cloud Images](http://cloud-images.ubuntu.com/vagrant/) (pre-installed disk images that have been customized by Ubuntu engineering to run in the Vagrant local-virtualizaition environment).
* [Vagrantbox.es](http://www.vagrantbox.es/) (a list of Vagrant [boxes](http://docs.vagrantup.com/v2/boxes/base.html) people have been nice enough to make publicly available).

## Need Help?

* Read the Vagrant [Docs](http://docs.vagrantup.com/v2/) (while boring, that is a great place to get started).

* Vagrant has a [Mailing List](https://groups.google.com/forum/#!forum/vagrant-up) for any topic related to Vagrant.

* Open an [Issue](https://github.com/vDevices/Vagrant-LinuxDesktop/issues) on GitHub if you run into trouble or have any suggestions.

	>For more information on GitHub's issue-tracking system, consult [Issues 2.0: The Next Generation | GitHub Blog](https://github.com/blog/831-issues-2-0-the-next-generation).

## Credits

A HUGE **Thank You** is in order to:

* [Portal Stack: Vagrant + VirtualBox + Ubuntu for linux development](http://portalstack.blogspot.com/2013/11/vagrant-virtualbox-ubuntu-for-linux.html) | By [Mike Kunze](https://github.com/mikekunze?tab=repositories) (for planting the seeds for this idea); _and_
* The trailblazers at the uber-successful [Varying Vagrant Vagrants](https://github.com/10up/varying-vagrant-vagrants), which &ndash; in addition to their great work on local WordPress development &ndash; have, in the process, created a roadmap for launching _any_ local-development environment off the ground.
