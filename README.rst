===========================
meta-repo
===========================
master branch
---------------------------

Meta-repo is a git repository that contains all the ports trees for Funtoo
Linux. The ports trees for Funtoo Linux are stored in the ``kits`` sub-directory,
as git *submodules*. For those who are unfamiliar with submodules, they are
essentially git's flavor of 'symbolic links' to other repositories, so that
a git repository can link to other repositories.

Please note that meta-repo is currently in beta. If you use meta-repo at the
moment, it should be for the primary purpose of testing meta-repo for Funtoo
Linux. It will receive significantly fewer updates than our regular ports
tree, so this if this concerns you, you should not be using meta-repo at this
time.

---------------
Using Meta-Repo
---------------

To use meta-repo as your meta-repository for Funtoo Linux, perform the following
steps on your Funtoo Linux system, as root:

::

 # cd /var/git
 # git clone https://github.com/funtoo/meta-repo.git
 # cd meta-repo
 # git submodule init
 # git submodule update
 # rm /usr/share/portage/config/repos.conf
 # rm -rf /etc/portage/repos.conf
 # ln -s /var/git/meta-repo/repos.conf /etc/portage/repos.conf
 # chown -R portage:portage /var/git/meta-repo

At this point, you should be able to use the ``emerge`` command and use 
Portage normally.

----------------
What is Included
----------------

Meta-repo consists of a number of 'kits', which are independent overlays that
contain ebuilds related to a specific set of functionality. The following kits
currently exist as submodules in meta-repo. Note that xorg-kit is the only one
that is currently documented:

`core-kit`_
  Core-kit contains a set of what we consider 'core' ebuilds -- ebuilds needed
  to build a stage3, plus essential userland utilities, development tools and
  libraries, except for perl and python.

`python-kit`_
  As the name suggests, python-kit contains all ebuilds related to python,
  which includes ``dev-lang/python`` as well as all all ``dev-python`` ebuilds.

`perl-kit`_
  Similar to ``python-kit``, perl-kit contains all ebuilds related to perl.

`security-kit`_
  Security-kit contains all core ebuilds related to Kerberos, SELinux and other
  security-enhanced Linux technologies.

`editors-kit`_
  Editors-kit contains all ebuilds related to text editors, including vim,
  emacs and xemacs and their plugins.

`media-kit`_
  Media-kit contains all ebuilds related to media, which typically includes
  all ebuilds in the ``media-*`` category other than those that are included
  in ``xorg-kit``.

`xorg-kit`_
  Xorg-kit contains all ebuilds that provide core graphics functionality,
  including xorg-server, OpenGL/Mesa, Vulkan, etc.

`nokit`_
  The 'nokit' kit contains all ebuilds that have not yet been 'kitted', or
  added to their own kit. If an ebuild isn't in one of the kits above, and it's
  in Funtoo, then it's part of nokit.

---------------
Active Branches
---------------

The following branches are active by default in meta-kit:

============   ============
kit            branch
------------   ------------
core-kit       1.0-prime
python-kit     3.4-prime
perl-kit       5.24-prime
security-kit   1.0-prime
editors-kit    1.0-prime
media-kit      1.0-prime
xorg-kit       1.17-prime
nokit          master
============   ============

These are the branches that we plan to maintain going forward. 

---------------
Reporting Bugs
---------------

To report bugs or suggest improvements to meta-kit, please use the Funtoo Linux
bug tracker at https://bugs.funtoo.org. Thank you! :)

.. _core-kit: https://github.com/funtoo/core-kit
.. _python-kit: https://github.com/funtoo/python-kit
.. _perl-kit: https://github.com/funtoo/perl-kit
.. _security-kit: http://github.com/funtoo/security-kit
.. _editors-kit: http://github.com/funtoo/editors-kit
.. _media-kit: http://github.com/funtoo/media-kit
.. _xorg-kit: http://github.com/funtoo/xorg-kit
.. _nokit: http://github.com/funtoo/nokit

