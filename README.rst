===========================
meta-repo
===========================

Meta-repo is a git repository that contains all the ports trees for Funtoo
Linux. Meta-repo also contains pointers to kits, which are functional units of
ebuilds used by Funtoo Linux, and which are managed by Funtoo Linux's personality
tool, `ego`.

---------------
Using Meta-Repo
---------------

To use meta-repo as your meta-repository for Funtoo Linux, first make sure that
you have not defined ``PORTDIR`` in ``/etc/make.conf`` to point to a specific
Portage repository location. If you have ``PORTDIR`` defined, comment it out or
remove this line. Then, perform the following steps as root to set up a temporary
``ego`` instance::

 # cd /var/tmp
 # git clone https://github.com/funtoo/ego.git
 # cd ego
 # ./ego sync

The ``./ego sync`` action will create a meta-repo at ``/var/git/meta-repo``, along
with kits, and also update your ``/etc/portage/repos.conf`` directory and
``/etc/portage/make.profile/parent`` file to work with ``ego`` and Funtoo Linux's
meta-repo.

You can use this temporary ``ego`` installation as needed until you are able to
emerge a recent version of ``ego`` directly. As long as you run the ``ego`` command
within the git repository, it should run self-hosted from the repository. Some
functionality such as MediaWiki document retrieval (``ego doc`` and query functionality
``ego query``) will not work without the ``mwparserfromhell`` and ``appi`` modules
being installed, but ``ego sync`` and ``ego profile`` commands should work.

--------------------------------------------
Updating to Meta-Repo with Funtoo Containers
--------------------------------------------

If you are a Funtoo Container user, you can enable meta-repo in your container
by making sure that you remove the ``PORTDIR=/var/src/portage``
line from ``/etc/make.conf``. Then follow the steps above to clone a git master
version of ego into ``/var/tmp/ego``, but do *not* run ``ego sync`` as the
last step; instead, run this variation of the command as the last step::

 # ./ego sync --config-only

This won't actually update any files in meta-repo, since it's read-only, but will
update your local ``/etc/portage/repos.conf`` directory and
``/etc/portage/make.profile/parent`` to work with meta-repo.

As above, you can now use the self-hosted git version of ``ego`` until your
system is fully upgraded and you have a local version of ego installed.

------------------
Updating Meta-Repo
------------------

From now on you will be using `ego sync` to update the Portage tree::

 # ego sync

For read-only meta-repo configurations like the default meta-repo on Funtoo
Containers, you can periodically use the read-only equivalent to ensure that
any new kits are properly enabled and accounted for::

 # ego sync --config-only

The ``emerge -auDN @world`` command may be used to update your system.

---------------
Reporting Bugs
---------------

To report bugs or suggest improvements to meta-repo, please use the Funtoo Linux
bug tracker at https://bugs.funtoo.org. Thank you! :)



