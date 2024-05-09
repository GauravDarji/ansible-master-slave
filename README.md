# Ansible Playbook to setup Master Slave for MySQL

This guide provides step-by-step instructions for running an Ansible playbook to create master slave.

## Prerequisites

- **Ansible Installed**: Ensure that Ansible is installed on your system.
- **Python Version**: Ansible relies on Python. Make sure you have Python installed.

## Tested With

- **Ansible Version**: 2.14.9
- **Python Version**: 3.11

## Repository Setup

- Clone the repository containing the Ansible playbook you want to run.
- Navigate to the `group_vars` directory within the cloned repository and fill in the required variables for your environment.

## Steps to Run Ansible Playbook

1. **Create Hosts File**: Define the target hosts (master and slave) in the hosts file.
2. **Check Connectivity**: Verify connectivity to the target hosts using the Ansible ping module.
3. **Run Playbook**: Execute the Ansible playbook against the specified hosts.

## Execution Steps

1. Clone Repository:
    ```bash
    git clone <repository_url>
    ```

2. Create Hosts File:
    ```plaintext
        [mysql]
        master ansible_host= ansible_user= ansible_ssh_common_args='-o StrictHostKeyChecking=no' ansible_python_interpreter=/usr/bin/python3
        slave ansible_host=  ansible_user= ansible_ssh_common_args='-o StrictHostKeyChecking=no' ansible_python_interpreter=/usr/bin/python3

        [mysql:vars]
        ansible_ssh_pass=''
        ansible_sudo_pass=''
    ```

3. Check Connectivity:
    ```bash
    ansible -i hosts -m ping all
    ```

4. Run Playbook:
    ```bash
    ansible-playbook -i hosts replication.yml
    ```

## Additional Notes

- Ensure that your `hosts` file is properly configured with the necessary hostnames or IP addresses.
- Customize the execution further by exploring additional options available for the `ansible` and `ansible-playbook` commands.
- Report buds into comment sections.
