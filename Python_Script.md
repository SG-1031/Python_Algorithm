"""
update_allow_list.py

Project:
Automate updating an IP allow list by removing IP addresses that should no longer have access.

Scenario:
This script reads an allow list of IP addresses from 'allow_list.txt', compares it against a 
remove list of IPs, removes any matching IPs from the allow list, and writes the updated list 
back to the file. This process helps maintain secure access control in a healthcare network 
environment.

Key Python concepts demonstrated:
- File handling using with statement and open()
- Reading and writing files with .read() and .write()
- String to list conversion with .split()
- Looping through lists with a for loop
- Conditional removal of list elements with .remove()
"""

# Define the file containing the allowed IP addresses
import_file = "allow_list.txt"

# Define IP addresses that should be removed from the allow list
remove_list = [
    "192.168.1.10",
    "10.0.0.5",
    "172.16.0.3"
]

def update_allow_list():
    # Step 1: Open the file and read the contents into a string
    with open(import_file, 'r') as file:
        ip_addresses = file.read()

    # Step 2: Convert the string of IPs into a list for easier manipulation
    ip_addresses = ip_addresses.split("\n")

    # Step 3: Iterate through each IP in the remove list
    for element in remove_list:
        # Step 4: Check if the IP is in the allow list, then remove it
        if element in ip_addresses:
            ip_addresses.remove(element)  # safe since no duplicates in the list

    # Step 5: Convert the list back to a newline-separated string
    updated_ip_addresses = "\n".join(ip_addresses)

    # Step 6: Overwrite the original file with the updated list
    with open(import_file, 'w') as file:
        file.write(updated_ip_addresses)

if __name__ == "__main__":
    update_allow_list()
    print("Allow list updated successfully.")
