# chaining ping command
in the ctf ultratech, there is an RCE at http://<target_ip>:8081/ping?ip=<user_input>. here the ping command was getting executed once the user-input value was given a valid ip adress

i want to bypass this ping command and execute other commands to get an access on the system. lets go google dorking to find out ways to bypass this mechanism

`intel of the tech:`

Node.js is the software being used at the port 8081

REST api is being used

the shell which is executing the commands is /bin/sh

