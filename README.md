## WARNING: This role will be deprecated very soon

All of the functionality provided by this role and more is available in the [DebOps project](http://debops.org). If you are using some of my roles in conjunction with each other, you will find the move to DebOps most pleasurable.

This role will be **removed** from the **galaxy** and from **github** anywhere from 42 microseconds to 2-3 weeks after you read this message.

---


## What is ansible-xampp?

It is an [ansible](http://www.ansible.com/home) role to install xampp.

### What problem does it solve and why is it useful?

At the time of writing this there wasn't a single xampp role available. This role downloads a specific xampp version and installs it. It is not meant for production. It is just a simple way to get xampp on a box.

It is not fully automated because of how the xampp installer works. It will prompt you with a GUI once it's ready to begin installing. Basically I have a few legacy wordpress apps to maintain and I wanted a simple way to get xampp installed on my development machine.

## Role variables

```
---
# The xampp version you want to use.
xampp_version: 1.8.3

# What is the file name of the version you want to install?
# 64bit version: xampp-linux-x64-{{ xampp_version }}-4-installer.run
xampp_filename: xampp-linux-{{ xampp_version }}-4-installer.run

# Where should the installer be downloaded to?
xampp_temp_download_path: /tmp
```

## Example playbook

For the sake of this example let's assume you have a group called **dev** and you have a typical `site.yml` file.

To use this role edit your `site.yml` file to look something like this:

```
---
- name: ensure dev servers are configured
- hosts: dev

  roles:
    - { role: nickjj.xampp, tags: xampp }
```

Let's say you want to edit the filename, you can do this by opening or creating `group_vars/app.yml` which is located relative to your `inventory` directory and then making it look something like this:

```
---
xampp_filename: xampp-linux-x64-{{ xampp_version }}-4-installer.run
```

## Usage

To start the server: `sudo /opt/lampp/lampp start`

To stop the server: `sudo /opt/lampp/lampp stop`

## Installation

`$ ansible-galaxy install nickjj.xampp`

## Requirements

Tested on ubuntu 12.04 LTS but it should work on other versions that are similar.

## Ansible galaxy

You can find it on the official [ansible galaxy](https://galaxy.ansible.com/list#/roles/1032) if you want to rate it.

## License

MIT