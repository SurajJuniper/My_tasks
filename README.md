#Task1- automation to check the connected interfaces

import paramiko

session = paramiko.SSHClient() #created obj for SSH client
session.set_missing_host_key_policy(paramiko.AutoAddPolicy) #auto adding policy when client is not validating ssh connection
session.connect(hostname="10.204.216.94", username="root", password='c0ntrail123') #giving necessary information to log in

#CONNECTION is established till here

print("\n")
print("Identifying the interfaces connected to Rack1-DataSw ")
stdin, stdout, stderr = session.exec_command("lldpcli show neighbors | grep -i nodem5") #running commands
    
print(stdout.read().decode()) # printing  the results
    
    

