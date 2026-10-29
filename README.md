# networkwalksB084E-week-01-Cyber-security-lab-set-up
CYBER SECURITY LAB SET UP
## 🖥️ 1. Prepare the Host System  
- **Host OS**: Windows 10 (your base system).  
- **RAM**: At least 8 GB (so you can allocate ~2 GB to Kali and still keep your host responsive).  
- **Processor**: Intel Core i7 with virtualization enabled (check BIOS/UEFI settings for Intel VT-x).  

👉 Why: Virtualization support is essential for running virtual machines smoothly.  

---

## 📦 2. Install VirtualBox  
- Download VirtualBox from the official site.  
- Install it with default settings.  
- Also install the **VirtualBox Extension Pack** (adds USB, networking, and other advanced features).  

👉 Why: VirtualBox is the hypervisor that lets you run multiple operating systems safely inside your host.  

---

## 🌐 3. Create a Virtual Network  
- Open VirtualBox → Preferences → Network → Add a **NAT Network**.  
- Configure:  
  - IPv4 Prefix: `10.0.0.0/24`  
  - DHCP: Enabled (optional, but static IPs are better for labs).  
  - IPv6: Disabled (simplifies setup).  

👉 Why: NAT Network allows multiple VMs to talk to each other while still having controlled internet access. Perfect for attacker-target simulations.  

---

## 🐉 4. Install Kali Linux VM  
- Download Kali Linux VM image from [kali.org](https://www.kali.org/get-kali/).  
- Import into VirtualBox (File → Import Appliance).  
- Configure VM:  
  - RAM: 2048 MB  
  - Network Adapter: Attached to **NatNetwork**  
  - Adapter Type: Intel PRO/1000 MT Desktop  
- Optional: Add a **Shared Folder** for file transfer between host and VM.  

👉 Why: Kali Linux is the attacker’s toolkit — it comes preloaded with penetration testing tools like Nmap, Metasploit, Burp Suite, etc.  

---

## ⚙️ 5. Configure Kali Networking  
Inside Kali:  
- Set static IP:  
  - IP Address: `10.0.0.2`  
  - Subnet Mask: `255.255.255.0`  
  - Gateway: `10.0.0.1`  
  - DNS: `8.8.8.8`  

👉 Why: A consistent IP makes documentation easier and ensures Kali is always reachable in your lab.  

---

## 📸 6. Create a Clean Snapshot  
- In VirtualBox → Right-click Kali → Take Snapshot.  
- Name it: *Clean Kali - Network Setup*.  

👉 Why: Snapshots let you roll back to a clean state if experiments break your VM.  

---

## ✅ 7. Verify the Lab  
Run these tests in Kali:  
- `ip a` → Confirms IP address.  
- `ping 10.0.0.1` → Tests gateway.  
- `ping 8.8.8.8` → Tests internet connectivity.  
- `nslookup networkwalks.com` → Tests DNS resolution.  
- `nmap -version` → Confirms Nmap is installed.  

👉 Why: Verification ensures your lab is functional before adding target machines.  

---

## 🛠️ 8. Expand with Target VMs (Future Step)  
- Add vulnerable machines like **Metasploitable2** or **DVWA**.  
- Connect them to the same NAT Network.  
- Assign IPs (e.g., `10.0.0.3`, `10.0.0.4`).  

👉 Why: This creates a playground where Kali can scan, exploit, and analyze targets safely.  

---

## 🛡️ Security & Ethics  
- Only test systems you own or have explicit permission to use.  
- Never connect vulnerable VMs to real networks.  
- Keep your lab isolated to avoid accidental attacks outside your environment.  

## 💡 Key Takeaways  
- VirtualBox provides safe virtualization.  
- NAT Network enables attacker-target communication.  
- Static IPs and snapshots make labs stable and repeatable.  
- Documentation is as important as the setup itself. 


Would you like me to build that roadmap for you?
