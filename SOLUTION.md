# Elevation Lab

This lab tests the student's ability to identify users on a Linux system, perform dictionary-based brute force attacks, and escalate privileges using a vulnerable SUID binary.

In this lab, students will learn:

- How to read files containing internal (unencrypted) credentials
- How to use `hydra` and dictionaries like `rockyou.txt` for brute force attacks
- How to detect and exploit binaries with the SUID bit
- How to gain root access and retrieve sensitive system files

## Machine Specifications 🖥️

- **System:** Ubuntu Server (no GUI)
- **Active Service:** SSH
- **Defined Users:**  
    - `robert` – `P!Roberto1984`  
    - `carla` – `Spring!1994`  
    - `emily` – `1988MoUnt41n`  
    - `daniel` – `@Cal1f0rn!aRulezzZ`  
    - `chester` – password unknown (but weak, included in `rockyou.txt`)

- **File with visible credentials:** `/home/users.txt`
- **Directories with filler files:**  
    `/home/Accounting/`, `/home/Financial/`, `/home/Team/`, `/home/HumanResources/`, `/home/Support/`

- **Vulnerable SUID Binary:** `/home/chester/rootme`
    - Binary content:
        ```c
        #include <unistd.h>
        int main() {
            setuid(0);
            setgid(0);
            execl("/bin/bash", "bash", NULL);
            return 0;
        }
        ```
    - Compiled as root, with `4755` (SUID) permissions

- **Final Flag:** `/root/flag.txt`

> **Note:** Root access is only possible by discovering Chester's password through brute force and executing the SUID binary.

### Machine Credentials

```bash
servername: elevation-lab
username: student
password: 4geeks-lab
```

## Expected Steps for the Student

1. **Perform network reconnaissance to identify the machine.**
     - Use tools like `nmap`, `netdiscover`, or `arp-scan`.
     - Detect an IP with port **22 (SSH)** open.

2. **Access via SSH with known users.**
     - Log in as: `robert`, `carla`, `emily`, and `daniel`.
     - Verify that their home directories contain only irrelevant information.

3. **Discover the `/home/users.txt` file.**
     - It contains the passwords for all users except `chester`.
     - Includes a warning that Chester's password is weak.

4. **Perform a brute force attack with Hydra.**
     - Use the `rockyou.txt` dictionary to find Chester's password (e.g., `123456` or similar).

5. **Log in as Chester.**
     - Check the contents of Chester's home directory.
     - Find the `rootme` binary, which has **SUID** permissions.

6. **Execute the vulnerable binary.**
     - It should open a shell with root privileges.

7. **Access the flag located at `/root/flag.txt`.**
     - The goal is to understand how a misconfigured SUID binary can allow full privilege escalation.
