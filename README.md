This code is released under the GNU General Public License. See LICENSE.txt.

Here is a set of bash scripts made under **Ubuntu** to use multiple **OpenSimulator** instances by multiple system users using **Tmux**.

Note that these scripts are for testing only and not pretending to be fully functionnal.
These scripts can Damage your system. Use them at your own risk.

Installation
------------

  - Check the path to ostmu for the variable OSTMU_FOLDER at the top of the files if the files are not located in /opt/ostmu :
    - install
    - check_sim
    - create_sim_files
    - ostmu

  - Rename the file ostmu/etc/config.example to ostmu/etc/config

  - Rename the folder ostmu/models.example to ostmu/models

  - Check the options in the file ostmu/etc/config

  - Check the ostmu/models files (the strings surrounded by <[ ]> will be replaced by variables)
   
  - run the file named "install" (as root)

Create a new simulator
----------------------

Run the file named (as root)

    create_sim_files

followed by the system user name and the sim name.

ex :

    sudo create_sim_files foo mysim

Run a simulator
---------------

The users can run "ostmu" file and follow the questions.

Check a simulator
-----------------

Run the file named

    check_sim

followed by the system user name and the sim name.

ex :

    check_sim foo mysim

Available variables for the models files
----------------------------------------
       <\[user_name\]>
       <\[grid_ip\]>
       <\[db_password\]>
       <\[sim_name\]>
       <\[sim_port\]>

Files organization
------------------

Here is the default files organization

       /home/username/.opensimulator
       └── sim1.sim
           ├── config-include
           │   ├── GridCommon.ini
           │   └── GridHypergrid.ini
           ├── log
           │   └── sim1.log
           │   └── OpenSim.log
           ├── OpenSim.exe.config
           ├── OpenSim.ini
           └── regions
               └── Regions.ini

Ports organization
------------------

Here are the available default ports used.

 available ports from 1024 to 49151 = 48127 ports available

 48000 - 10000 = 38000 ports available / 100 = 380 users
 

     user1 = 10 100
     
     sim0 = 10 100
     region0 = 10 101
     region0 = 10 109
     
     sim1 = 10 110
     region1 = 10 111
     region9 = 10 119
     
     sim2 = 10 120
     region1 = 10 121
     region9 = 10 129
     
     sim3 = 10 130
     region1 = 10 131
     region9 = 10 139
     
     .../...
     
     sim9 = 10 190
     region1 = 10 191
     region9 = 10 199
so : 9 regions per sim and 10 sims per user = 90 regions per user...
     
     user2 = 10 200
     user9 = 10 900
     user10 = 11 000
     user11 = 11 100
     user99 = 19 900
     user100 = 20 000

