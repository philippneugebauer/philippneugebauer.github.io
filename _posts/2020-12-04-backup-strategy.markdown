---
layout: post
title: Backup Strategies
date: 2020-12-20 07:00:33 +0200
categories: backups time-machine pi raspberry-pi wasabi kopia duplicati
---

2020 with its craziness gave me time think about and to revise my backup setup.
I started several years ago with SVN repositories to store and share my sensible data across several machines and added at some point after switching to macOS Time Machine with an external drive.
This setup annoyed me a lot since I always needed to grab my drive and these rare backups then took so long that it annoyed me even more.
All in all, my strategy wasn't as sophisticated as I wanted it to be.

I've now added [Duplicati](https://www.duplicati.com/) and [Kopia](https://kopia.io/) backing up my sensible data encrypted to several cloud providers like [Dropbox](https://www.dropbox.com/) and [Wasabi](https://wasabi.com/). This makes me independent from a specific cloud and also backup tool provider and allowed me to avoid a single point of failure.

In addition to the cloud backups, I also bought a Raspberry Pi, connected my old SSDs via USB to it and set up a Time Machine endpoint with netatalk as well as a simple SFTP server for local backups of Duplicati and Kopia.

In detail, the setup of tools on the Pi is described in the following blog posts:
<https://jeremycollins.net/using-a-raspberry-pi-as-a-nas-mac-os-time-machine-2020-edition>
<https://gist.github.com/jhanzo/f1df54b303307c5a6350de0ca3abd5af>
<https://linuxconfig.org/how-to-setup-sftp-server-on-ubuntu-20-04-focal-fossa-linux>
<https://www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-a-user-s-directory-on-ubuntu-18-04>

Furthermore, I deactivated the automated backups from Time Machine and use the [Time Machine Editor](https://tclementdev.com/timemachineeditor/) to ensure weekly backups.

To properly use the Raspberry Pi with the connected drives, I needed to buy a [USB hub](https://www.amazon.de/gp/product/B07P6MPXJ7/ref=ppx_yo_dt_b_asin_title_o04_s00?ie=UTF8&psc=1) since the Pi itself couldn't power all of them.
