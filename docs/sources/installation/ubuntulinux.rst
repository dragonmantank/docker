:title: Requirements and Installation on Ubuntu Linux
:description: Please note this project is currently under heavy development. It should not be used in production.
:keywords: Docker, Docker documentation, requirements, virtualbox, vagrant, git, ssh, putty, cygwin, linux

.. _ubuntu_linux:

Ubuntu Linux
============

  **Please note this project is currently under heavy development. It should not be used in production.**

Right now, the officially supported distribution are:

- :ref:`ubuntu_precise`
- :ref:`ubuntu_raring`

Docker has the following dependencies

* Linux kernel 3.8 (read more about :ref:`kernel`)
* AUFS file system support (we are working on BTRFS support as an alternative)

.. _ubuntu_precise:

Ubuntu Precise 12.04 (LTS) (64-bit)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This installation path should work at all times.


Dependencies
------------

**Linux kernel 3.8**

Due to a bug in LXC docker works best on the 3.8 kernel. Precise comes with a 3.2 kernel, so we need to upgrade it. The kernel we install comes with AUFS built in.


.. code-block:: bash

   # install the backported kernel
   sudo apt-get update && sudo apt-get install linux-image-generic-lts-raring

   # reboot
   sudo reboot


Installation
------------

Docker is available as a Ubuntu PPA (Personal Package Archive),
`hosted on launchpad  <https://launchpad.net/~dotcloud/+archive/lxc-docker>`_
which makes installing Docker on Ubuntu very easy.

.. code-block:: bash

   # Add the PPA sources to your apt sources list.
   sudo apt-get install python-software-properties && sudo add-apt-repository ppa:dotcloud/lxc-docker

   # Update your sources
   sudo apt-get update

   # Install, you will see another warning that the package cannot be authenticated. Confirm install.
   sudo apt-get install lxc-docker

Verify it worked

.. code-block:: bash

   # download the base 'ubuntu' container and run bash inside it while setting up an interactive shell
   docker run -i -t ubuntu /bin/bash

   # type 'exit' to exit


**Done!**, now continue with the :ref:`hello_world` example.

.. _ubuntu_raring:

Ubuntu Raring 13.04 (64 bit)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Dependencies
------------

**AUFS filesystem support**

Ubuntu Raring already comes with the 3.8 kernel, so we don't need to install it. However, not all systems
have AUFS filesystem support enabled, so we need to install it.

.. code-block:: bash

   sudo apt-get update
   sudo apt-get install linux-image-extra-`uname -r`

Installation
------------

Docker is available as a Ubuntu PPA (Personal Package Archive),
`hosted on launchpad  <https://launchpad.net/~dotcloud/+archive/lxc-docker>`_
which makes installing Docker on Ubuntu very easy.


Add the custom package sources to your apt sources list.

.. code-block:: bash

   # add the sources to your apt
   sudo add-apt-repository ppa:dotcloud/lxc-docker

   # update
   sudo apt-get update

   # install
   sudo apt-get install lxc-docker


Verify it worked

.. code-block:: bash

   # download the base 'ubuntu' container and run bash inside it while setting up an interactive shell
   docker run -i -t ubuntu /bin/bash

   # type exit to exit


**Done!**, now continue with the :ref:`hello_world` example.
