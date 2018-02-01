.. role:: bash(code)
   :language: bash

.. _donts:

Dont's!
=======

Do not:

- Run jobs on the head node (also called frontend). This slows down simple shell operations for other users and also may lead to a crash thus rending the whole cluster unavailable.

- Submit a bunch of jobs that won't completely fill a node. See :ref:`computeresources` for more details.

- Ask for the high-memory node if you don't need really need it.

- Ask for more memory than your job needs.