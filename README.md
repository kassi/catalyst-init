Catalyst init.d Runscript
=========================

This is a simple and greedy programmed init.d runscript for [Catalyst](http://search.cpan.org/~bobtfish/Catalyst-Runtime-5.90006/lib/Catalyst.pm)
fastcgi application servers.
This version was build for and tested on Ubuntu.

Installation
------------

Copy the files to your system root, so that they will reside in

    /etc/catalyst

and

    /etc/init.d

If you use [perlbrew](http://www.perlbrew.pl/), you may edit the envvar file.

Create configuration files for each fastcgi server. The example.conf may help you here.

Foreach appserver you want to enable, create a symlink from apps-enabled to the corresponding apps-available configuration file.

General Usage
-------------

Most of the commands can be called in two ways:

    /etc/init.d/catalyst *command* *appname*
    /etc/init.d/catalyst *command*all

where *appname* is the name of the configuration file (without .conf).

The latter will search for all configration files and run the former foreach enabled app it finds.

The following just handles the single version, but can be used for the all-version as well.

Startup
-------

Start your server(s) by calling

    /etc/init.d/catalyst start *appname*

Stopping
--------

Stop your server(s) by calling

    /etc/init.d/catalyst stop *appname*

Reloading
---------

If you've made changes to your app, just reload it by calling

    /etc/init.d/catalyst reload *appname*

This is faster than restarting.

Restarting
----------

If you have to restart your server, call

    /etc/init.d/catalyst restart *appname*

This basically does a stop, waits and starts again, which can take a few seconds.

Status
------

You can have a basic view on your running servers by calling

    /etc/init.d/catalyst status

Additional Information
----------------------

This script has been written for the exact need of maintaining catalyst fastcgi servers.
However, it should be possible to enhance it to be able to deal with other app frameworks as well.
