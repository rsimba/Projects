#!/usr/bin/python
#Import Modules
import getpass
import telnetlib

user = input("Enter your username: ")
password = getpass.getpass()

for n in range (100,110):
        HOST = "192.168.10." + str(n)
        tn = telnetlib.Telnet(HOST)

        tn.read_until(b"username: ")
        tn.write(user.encode('ascii') + b"\n")
        if password:
            tn.read_until(b"Password: ")
            tn.write(password.encode('ascii') + b"\n")


        tn.write(b"conf t\n")

        for n in range (2,10):
                tn.write("vlan " + str(n) + "\n")
                tn.write("name Dot1x_VLAN_" + str(n) + "\n")

        tn.write("end")
        tn.write("exit\n")

print(tn.read_all().decode('ascii'))
