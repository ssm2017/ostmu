Here is a set of bash scripts made under **Ubuntu** to use multiple **OpenSimulator** instances by multiple system users using **Tmux**.

Note that these scripts are for testing only and not pretending to be fully functionnal.
These scripts can Damage your system. Use them at your own risk.

Installation
------------
run the file named "install"

Create a new simulator
----------------------

Run the file named

    create_sim_files

followed by the system user name and the sim name.

ex :

    create_sim_files foo mysim

Run a simulator
---------------

The users can run "opensim" file and follow the questions.

Check a simulator
-----------------

Run the file named

    check_sim

followed by the system user name and the sim name.

ex :

    check_sim foo mysim
