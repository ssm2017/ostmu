This code is released under the GNU General Public License. See LICENSE.txt.

Here is a set of bash scripts made under **Debian** to use multiple **OpenSimulator** instances by multiple system users using **Tmux**.

Note that these scripts are for testing only and not pretending to be fully functionnal.
Use them at your own risk.

Installation
------------

  - run the file named "install" (as root)

Then answer the questions.

The installation process will create a /etc/ostmu folder. This folder contains the ostmu.conf file and some "models" folders. These models will be used when creating new simulators. You can customize the models using bash variables.

The installation process will also create 2 symlinks in /usr/local/bin named :

  - opensimulator

  - check_sim

Databases
---------

Actually, the script is set to use sqlite or mysql.

To allow the script to write in the database, the root user needs to have credentials set in the /root/.my.cnf file.

Create a new simulator
----------------------

Run the file named (as root)

    create_sim_files

followed by the system user name and the sim name.

example :

    sudo create_sim_files JohnDoe mysim

Then answer the questions.

Run a simulator
---------------

The users can run "opensimulator" file and follow the questions.

  - If running "opensimulator" without any parameter, the script will ask you some questions.

  - If running "opensimulator" followed by a sim name (without .sim at the end), the script will run the session and display it or just display it if it is already running.

  - If running "opensimulator" followed by the keyword "autostart", the script will run all the user simulators that contain a file named "autostart" in the .sim folder of the simulator. (the file can be blank) (example : /home/JohnDoe/.opensimulator/mysim.sim/autostart)

Check a simulator
-----------------

Run the file named

    check_sim

followed by the system user name and the sim name.

ex :

    check_sim JohnDoe mysim

If everything is fine, the script will return 0 and 1 if there was an issue.

Update database password
------------------------

If you are running mysql and that you deleted the simulator folders, you can update the user password in the database using the file named :

    update_password

followed by the user name.

The user database password is stored in a file in the user opensimulator folder and can be read only by the user or root.

Example :

    /home/JohnDoe/.opensimulator/db_pass


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

