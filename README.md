# ELEVATION - Escalating from Common to Root

In this lab, you will explore a corporate Linux system with multiple users, discover which of them can escalate privileges, and access a hidden flag in the root directory. In this lab, you will learn:

- Analyzing internal user files
- Enumerating accounts and passwords
- Brute-forcing with a dictionary (`rockyou.txt`) using Hydra
- Privilege escalation via SUID binaries
- Reading flags as the root user

<how-to-start>
   
## 🌱 How to Start This Lab

Follow these instructions to get started:

1. **Download the virtual machine** from this [link](https://storage.googleapis.com/cybersecurity-machines/elevation-lab.ova).
2. **Import the machine** into your preferred virtualization manager (VirtualBox, VMware, etc.).
3. Once the machine is running, you can start the lab!

</how-to-start>


## 📄 Instructions

You are facing a corporate server with multiple users. Your task is to discover how to gain privileged access from an apparently limited environment.

1. **Discover the IP address of the ELEVATION machine.**
   - The machine is connected to the same network as you, but its IP has not been provided.
   - Use tools like `nmap`, `netdiscover`, or `arp-scan` to scan the network.

2. **Access the system via SSH with known users.**

3. **Pay attention to a user without a known password.**

4. **Perform a brute-force attack using Hydra.**

5. **Gain access and look for ways to escalate privileges.**

6. **Find and read the final flag.**

**Remember:** sometimes power lies not in what is visible… but in what seems unprotected.

Happy hacking!