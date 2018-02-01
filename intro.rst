.. role:: bash(code)
   :language: bash

Introduction
============


Arjuna is a multi-departmental GPU cluster managed by Gregory Houchins. If you have questions or would like to be added
to the mailing list, please email <arjunahelp@cmu.edu>.

Accessing Arjuna
----------------

Setting up an account
~~~~~~~~~~~~~~~~~~~~~

If you would like to request access to Arjuna, please email arjunahelp@cmu.edu with your andrew ID, name, and research advisor.

Accessing with ssh
~~~~~~~~~~~~~~~~~~

Arjuna is located at :bash:`arjuna.psc.edu`, or equivalently, :bash:`coe.psc.edu`. To access Arjuna, in a terminal type:

.. code-block:: bash

    > ssh andrewID@arjuna.psc.edu

or

.. code-block:: bash

    > ssh andrewID@coe.psc.edu

You will be prompted to enter your password to gain access.

Changing your password
~~~~~~~~~~~~~~~~~~~~~~

To change your password, use the command :bash:`passwd`. You will be prompted to enter your current password and a new password.

Off-campus access
~~~~~~~~~~~~~~~~~

Arjuna can only be accessed by ssh from IP addresses in the cmu domain. To log in, you must therefore do one of the following:

1. use a computer on campus
2. use a VPN
3. first ssh into an on-campus machine, then ssh onto Arjuna (users with an andrew ID can access a machine on the campus network at andrewID@unix.andrew.cmu.edu and using their andrew password as credentials)

.. _nodeinfo:

About the nodes
---------------

The available nodes have the following specs:

- 68 CPU nodes, each with 128 GB memory and 56 cores
- 2 high-memory nodes, each with 512 GB and 32 cores
- 27 GPU nodes, each with 128 GB, 64 cores, and 4 K80 NVIDIA GPUs

Arjuna has 8 TB of RAID storage for the entire cluster. There are currently no limits on the amount of storage that each
user may use, but please be aware of the amount of space you are using. See :ref:`storage` for more details about
best practices.

Computing limits
~~~~~~~~~~~~~~~~

There is a 30 percent limit on CPU node usage for any user at any one time. There are no limits on usage for GPU or
high-memory nodes, with one exception: if you are in Chemical Engineering and have access to the GPU nodes, you may only
use 4 nodes at once.

Useful Commands
---------------

Arjuna uses Slurm to schedule its jobs. Below are some useful commands for submitting, checking, or canceling jobs.

sbatch (submit a job)
~~~~~~~~~~~~~~~~~~~~~

This command will submit a script to slurm to be run. This job will sit on the queue until an available node executes it.

.. code-block:: bash

	> sbatch my_job

squeue -u user_ID (check job status)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This command will check the status of your jobs. If you run :bash:`squeue` without any arguments, it will show all jobs on
the queue.

.. code-block:: bash

	> squeue -u user_ID

scancel job_ID (cancel a job)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This command will cancel a job. You will need the job ID number as an identifier.

.. code-block:: bash

	> scancel job_ID

sinfo (check nodes status)
~~~~~~~~~~~~~~~~~~~~~~~~~~

This command shows the status of the different computing nodes. "idle" nodes have no jobs running, "alloc" nodes have jobs running 
on all their cores, and "mix" nodes have some cores taken and some idle.

.. code-block:: bash

	> sinfo

	PARTITION AVAIL  TIMELIMIT  NODES  STATE NODELIST
	gpu*         up   infinite     27  alloc c[002-028]
	cpu          up 7-00:00:00     28    mix d[001-002,007-008,010-012,015,017,020,032-034,036-038,041-042],f[001,003,005,007,010,014,017,019-020,023]
	cpu          up 7-00:00:00     42  alloc d[003-006,009,013-014,016,018-019,021-031,035,039-040,043-044],e[001-002],f[002,004,006,008-009,011-013,015-016,018,021-022,024]
	highmem      up 7-00:00:00      2  alloc e[003-004]

scontrol show job job_ID (display job information)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This command will display various useful metadata about a job identified by :bash:`job_ID`.

.. code-block:: bash

	> scontrol show job job_ID

sacctmgr list associations (show accounts, users, and restrictions)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This command displays a list of all users and associated accounts, along with any restrictions on each user's access to
computating resources.