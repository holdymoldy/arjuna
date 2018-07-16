.. role:: bash(code)
   :language: bash


Configuring your job file
=========================

Node types
----------

For a complete list of nodes and their specifications, please see :ref:`nodeinfo`.


.. _slurmflags:

Slurm flags
-----------

All slurm flags must be preceded by :bash:`#SBATCH`. See the :ref:`jobexample` for more.

- :bash:`#SBATCH -J {}` : the name of the job

- :bash:`#SBATCH --time=D-HH:MM` : runtime in days (D), hours (HH), and minutes (MM). If the job is not completed in this time, it is ended.

- :bash:`#SBATCH -A {}` : your advisor's account. If you are unsure of what to put here, use the bash command :bash:`sacctmgr list associations`.

- :bash:`#SBATCH -p {}` : the type of node you would like to use. This will be one of :bash:`cpu`, :bash:`gpu`, or :bash:`highmem`. See :ref:`nodeinfo` for more information.

- :bash:`#SBATCH -N {}` : total number of nodes requested

- :bash:`#SBATCH -n {}` : total number of cores requested

- :bash:`#SBATCH --mem-per-cpu={}` : amount of memory requested, per core, in MB.

- :bash:`#SBATCH -o {}` : the output of your job will write to this file

- :bash:`#SBATCH -e {}` : if your job throws any errors, they will be written to this file

- :bash:`#SBATCH --mail-type={}` : Asks the job manager to send you an email when your job begins (:bash:`--mail-type=BEGIN`), ends (:bash:`--mail-type=END`), fails (:bash:`--mail-type=FAIL`), or does any of these three (:bash:`--mail-type=ALL`). Must be used in conjunction with the :bash:`--mail-user={}` flag.

- :bash:`#SBATCH --mail-user={}` : See the above bullet.

Submitting your job
-------------------

If your job file is named :bash:`my_job.sh`, you may submit your job with the command

.. code-block:: bash

    > sbatch my_job.sh

.. _jobexample:

Example
-------

.. code-block:: bash

    #!/bin/bash
    #SBATCH -J test_job # Job name
    #SBATCH -n 64 # Number of total cores
    #SBATCH -N 1 # Number of nodes
    #SBATCH -A venkvis
    #SBATCH -p gpu
    #SBATCH --mem-per-cpu=2000 # Memory pool for all cores in MB
    #SBATCH -e test_job.err
    #SBATCH -o test_job.out # File to which STDOUT will be written %j is the job #
    #SBATCH --mail-type=END # Type of email notification- BEGIN,END,FAIL,ALL
    #SBATCH --mail-user=your_andrewid@cmu.edu # Email to which notifications will be sent

    echo "Job started on `hostname` at `date`"

    mpirun -np 64 python test.py

    echo " "
    echo "Job Ended at `date`"

A few comments:

- The first 11 lines are flags explained in the :ref:`slurmflags` section
- The :bash:`echo` commands will be printed in :bash:`test_job.out` file.
- The line :bash:`mpirun -np 64 python test.py` is the actual job that will be executed. **Note that the number after the "-np" in this line must match the total number of requested cores.**
