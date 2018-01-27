Introduction
============


Arjuna is a multi-departmental GPU cluster managed by Gregory Houchins <ghouchin@andrew.cmu.edu>. 

Useful Commands
---------------

sinfo (check nodes status)
~~~~~~~~~~~~~~~~~~~~~~~~~~

This command shows the status of the different computing nodes. "idle" nodes have no jobs running, "alloc" nodes have jobs running 
on all their cores, and "mix" nodes have some cores taken and some idle.

.. code-block:: bat

	> sinfo

	PARTITION AVAIL  TIMELIMIT  NODES  STATE NODELIST
	gpu*         up   infinite     27  alloc c[002-028]
	cpu          up 7-00:00:00     28    mix d[001-002,007-008,010-012,015,017,020,032-034,036-038,041-042],f[001,003,005,007,010,014,017,019-020,023]
	cpu          up 7-00:00:00     42  alloc d[003-006,009,013-014,016,018-019,021-031,035,039-040,043-044],e[001-002],f[002,004,006,008-009,011-013,015-016,018,021-022,024]
	highmem      up 7-00:00:00      2  alloc e[003-004]
