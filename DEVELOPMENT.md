# Development

This guide contains information for setting up this repository for development. It also includes a guide on how to develop these images.

## Requirements

You'll need the following to develop and test our images:

- [Vagrant][vagrant]
- Virtualization software, either: [VMware Workstation][vmwareworkstation], [VMware Fusion][vmwarefusion] or [Virtual Box][virtualbox]
- [Git][git]

Once you've created the virtual machine you'll have an environment complete with:

- Docker
- Docker compose
- Git
- Node.js

There are files for editors that should keep the file formatting consistent with what already exists in the repository.

## Setup

- [host] Fork the repository.
- [host] Clone your fork locally.
- [host] Start the vagrant machine by running `vagrant up`.
- [host] Once everything has been setup, gain access to the VM with `vagrant ssh`.
- [guest] Issue `sudo apt-get update` to update the Aptitide repositories.
- [guest] Update the OS with `sudo apt-get dist-upgrade` (you may be asked some questions).

Everything should be setup and ready to develop with. You should execute into the `/vagrant` directory for most day to day usage with `cd /vagrant`.

To test the images, run [guest] `c up` - this is a custom script that has been built to ease the process of interacting with Docker and Docker Compose.

## Git, building and testing

The core images in this repository are:

- `flashmedia/consul`
- `flashmedia/consului`

There is also one used only for testing:

- `flashmedia/orchestrator-app`

### Building

You can build these images locally using `c up`, `c build` and `c rebuild`. These images are built for production using Docker Cloud. Autobuild repositories have been setup and will automatically build for you on certain events:

- Pushing to `dev` branch will build the `:dev` version of these images.
- Pushing a tag in the format `{image-name}-v{semver}` will build the images, with the corresponding version tag.
- Pushing to master won't kick-off any build process.

### Git

`master` should contain only tested working code. A `dev` branch should be created and used for development purposes. If you need to, you can branch from `dev` as required for testing locally and trying out ideas. However, should you want to build those remotely, you'll need to use the `dev` branch.

[vagrant]: https://www.vagrantup.com/
[vmwareworkstation]: https://www.vmware.com/au/products/workstation/
[vmwarefusion]: https://www.vmware.com/au/products/fusion/
[virtualbox]: https://www.virtualbox.org/
[git]: https://git-scm.com/
