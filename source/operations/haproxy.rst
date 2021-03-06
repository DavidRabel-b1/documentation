=======
HAProxy
=======

Manual failover
===============

* Although HAProxy runs on multiple nodes, the virtual IP addresses can only be assigned to one node.
  That means that only one HAProxy instance is used at the same time.

* Keepalived manages the virtual IP addresses and initiates an automatic failover if one node fails.
  There is no official way to manually tell keepalived to failover the VIP. But if you restart the
  keepalived container on the active node, the VIP will be moved to another node.

.. code-block:: console

   $ docker restart keepalived

* Another possibility is the use of a additional dummy interface. However, it is necessary to maintain
  keepalived configuration as an overlay file.

  https://www.virtualtothecore.com/en/manual-failover-of-keepalived/
