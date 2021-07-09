README
######

:Homepage: https://github.com/romain-dartigues/ansible-netdata
:License: BSD 3-Clause

Deploy `netdata <https://my-netdata.io/>`_
(`:octocat: <https://github.com/firehol/netdata>`_) through ansible with
ability to configure and switch master.

Contributions and suggestions welcome.

Requirements
============

* ``inventory_hostname`` should be a FQDN and *must* be consistent with
  ``netdata_stream_master``, ``netdata_stream_host``
* tested with ``ansible`` 2.5 and CentOS 7

Configuration
=============

+-------------------------+-------------------------------------------------+
| ``netdata_dmz``         | if set, will download netdata package through   |
|                         | the ansible host                                |
+-------------------------+-------------------------------------------------+
| ``netdata_package_uri`` | URI of the latest package; when unset           |
|                         | (default) will guess it from GitHub. This is    |
|                         | only useful if you have a local mirror.         |
+-------------------------+-------------------------------------------------+

Streaming
---------

+-------------------------+--------------------------------------------+
| ``netdata_master``      | hostname to contact the master;            |
|                         | or ``netdata_master_host`` if unset        |
+-------------------------+--------------------------------------------+
| ``netdata_master_host`` | name of the master                         |
+-------------------------+--------------------------------------------+
| ``netdata_stream_uuid`` | UUID used by clients to connect the master |
+-------------------------+--------------------------------------------+

Example Playbook
================

.. code-block:: yaml

    - hosts:
         - foo.example.net
         - bar.example.net
         - xyz.example.net
      vars:
        ansible_master: "netdata.example.net"
        ansible_master_host: "foo.example.net"
        netdata_stream_uuid: "e512bb7d-2514-4ff3-9022-e25645e96503"
      roles:
        - netdata


Credits
=======

I'm not affiliated in any ways with `FireHOL <https://firehol.org/>`_
(but admirative about their work ♥).
