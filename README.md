# Allow List IP Address Updater

## Project Overview

This project contains a Python script designed to update an allow list of IP addresses for a healthcare company's secure network. The allow list controls which employees can access restricted patient data based on their IP addresses.

The script reads the current allow list from a file, compares it with a remove list of IP addresses that should no longer have access, removes those IPs from the allow list, and updates the file accordingly. This automation ensures that only authorized users retain network access, which is crucial for maintaining patient privacy and security.

## Repository Contents

- `update_allow_list.py` — Python script implementing the algorithm to update the allow list.
- `allow_list.txt` — Example allow list file containing IP addresses (should be updated with actual data).
- `Algorithm_for_file_updates_in_Python.md` — Portfolio document explaining the project, code, and algorithm step-by-step.

## How to Use

1. Place the `allow_list.txt` file in the same directory as the script. This file should contain one IP address per line.
2. Modify the `remove_list` variable inside `update_allow_list.py` to include IP addresses you want to remove from the allow list.
3. Run the Python script:
   ```bash
   python update_allow_list.py
