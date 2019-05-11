Linux Security Modules
----------------------

A collection of three simple linux security modules, more for learning and experimentation than for serious use.

* [whitelist](security/whitelist/)
   * Only allow execution of commands with xattr present.
* [hashcheck](security/hashcheck/)
   * Only allow execution of commands with xattr containing valid SHA1sum of binaries.
* [can-exec](security/can-exec)
   * The only __serious__ module in this repository.
   * Invokes the user-space helper `/sbin/can-exec` to determine whether a user can execute a specific command.
   * Allows policies to be written and changed on-demand.


## Documentation

I wrote a couple of blog posts which might provide more background,
and they are listed below (in order oldest to most recent):

* https://blog.steve.fi/so_i_accidentally_wrote_a_linux_security_module.html
* https://blog.steve.fi/linux_security_modules__round_two_.html
* https://blog.steve.fi/yet_more_linux_security_module_craziness___.html

## Installation

The code has been tested upon kernels as recent as 5.1

Copy the contents of `security/` into your local Kernel-tree, and run `make menuconfig` to enable the appropriate options.

**NOTE**: Over time the two files `security/Kconfig` & `security/Makefile` might need resyncing with the base versions installed with the Linux source-tree, you can look for mentions of `CAN_EXEC`, `HASH_CHECK`, & `WHITELIST` to see what I've done to add the modules.

For a Debian GNU/Linux host, building a recent kernel, these are the dependencies you'll need to install:

      # apt-get install flex bison bc libelf-dev libssl-dev \
                        build-essential make libncurses5-dev \
                        git-core
