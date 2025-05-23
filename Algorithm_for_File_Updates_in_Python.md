# Algorithm for File Updates in Python

## Project Description  
This project demonstrates a Python algorithm developed to manage access control in a healthcare company’s network. The algorithm reads an allow list file containing IP addresses permitted to access restricted patient records. It then compares this list to a removal list of IP addresses that should no longer have access, removes them from the allow list, and updates the file. This automation ensures that only authorized employees retain access to sensitive data, showcasing skills in file handling, string and list manipulation, and control flow essential for cybersecurity roles.

---

## Step 1: Open the File That Contains the Allow List

```python
import_file = "allow_list.txt"
with open(import_file, 'r') as file:
    ip_addresses = file.read()
````

* The `with` statement opens the file safely and ensures it is properly closed afterward.
* The `open()` function is used with `'r'` mode to open the file for reading.
* The `.read()` method reads the entire content of the file into the string variable `ip_addresses`.

---

## Step 2: Read the File Contents

* The `.read()` method converts the file content to a string, enabling further processing.

---

## Step 3: Convert the String into a List

```python
ip_addresses = ip_addresses.split("\n")
```

* The `.split("\n")` method splits the string into a list, breaking at each newline character, so each IP address becomes a separate list item.

---

## Step 4: Iterate Through the Remove List

```python
for element in remove_list:
    # Removal logic will be applied here
```

* A `for` loop iterates over each IP address in the `remove_list`.
* The variable `element` represents the current IP address under consideration.

---

## Step 5: Remove IP Addresses That Are on the Remove List

```python
if element in ip_addresses:
    ip_addresses.remove(element)
```

* The `if` statement checks if the IP address (`element`) is present in the `ip_addresses` list.
* If it is, the `.remove()` method deletes that IP from the list.
* This works reliably because the list contains no duplicate IP addresses.

---

## Step 6: Update the File with the Revised List of IP Addresses

```python
updated_ip_addresses = "\n".join(ip_addresses)

with open(import_file, 'w') as file:
    file.write(updated_ip_addresses)
```

* The `.join("\n")` method combines the list back into a single string, with each IP separated by a newline.
* The file is reopened in write mode (`'w'`) to overwrite the old content with the updated list.

---

## Complete Python Code

```python
import_file = "allow_list.txt"

remove_list = [
    "192.168.1.10",
    "10.0.0.5",
    "172.16.0.3"
]

with open(import_file, 'r') as file:
    ip_addresses = file.read()

ip_addresses = ip_addresses.split("\n")

for element in remove_list:
    if element in ip_addresses:
        ip_addresses.remove(element)

updated_ip_addresses = "\n".join(ip_addresses)

with open(import_file, 'w') as file:
    file.write(updated_ip_addresses)
```

---
