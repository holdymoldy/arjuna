.. role:: bash(code)
   :language: bash

.. _bestpractices:


Best practices
==============

.. _storage:

Disk space usage
----------------

There are currently no limits on the amount of disk space that a user can use. Please be cognizant of this - if Arjuna's
storage becomes completely full, most queued jobs will be canceled. For your reference you can check the state of the
storage with the command

.. code-block:: bash

    > df -h

:bash:`/dev/mapper/raid_vg-home_lv` is the relevant memory location that :bash:`/home/` is mounted to.

You can also check your usage by running

.. code-block:: bash

    > du -sh /home/username

This will give you a summary (-s) in human readable units (-h) of how much disk space you are taking up. **Users using around 500GB or more are using a disproportionally high amount of storage and should strongly consider removing unimportant data.**

.. _computeresources:

Asking for computing resources
------------------------------

Please follow these guidelines when asking for computing resources in your job file.

**Ask for a number of cores that can evenly divide the total number of cores on that node.** For example, a CPU
node has 56 cores, so you can ask for 14 or 28 cores, but not 31. The reason is that nodes can be split amongst separate
jobs. Asking for awkward numbers of cores like this makes it difficult for the job manager to split these leftover resources.

**Ask for memory that is proportional to the number of requested cores.** For example, if you need 64 GB (out of 128) of memory on a
CPU node, ask for 28 cores (out of 56). Don't ask for, say, 64 GB on 10 cores. Again, this makes it difficult for the
job manager to split remaining resources amongst other jobs.