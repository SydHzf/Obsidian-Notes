___
	In Docker Compose, each service runs in a separate container, which acts like an independent system but does NOT have a full operating system. Instead, all containers share the host OS kernel while being isolated. These containers communicate with each other using a Docker network.
### **How Docker Containers Work in Docker Compose**

- Each service runs in **its own container** but **shares the host [[Docker#OS Kernel in Simple Terms| OS Kernel]]** (usually Linux).
		1. Each service (container) runs its own process (like a program on your computer).
		2. They don’t have a full OS—they just use the existing OS kernel to run.
		3. They communicate with each other using a special Docker network (like apps talking over Wi-Fi).
- Containers are **lightweight**, unlike virtual machines (VMs), because they **don’t need a full OS**—just the necessary files, libraries, and dependencies.
- All services **communicate over a virtual Docker network** (by default, a bridge network).

### **OS Kernel in Simple Terms**

Think of your computer’s **Operating System (OS)** like a big company.

- **The Kernel is the CEO** 🏢👨‍💼
    
    - It manages everything and makes sure tasks get done efficiently.
    - It decides **which apps (programs) get CPU time, memory, and resources**.
    - It makes sure programs don’t mess up each other’s work.
- **Apps (Programs) are the Employees** 🖥️👩‍💻
    
    - They follow the CEO’s rules to get their work done.
    - They don’t talk directly to the computer hardware (CPU, RAM, disk).
- **Hardware (CPU, RAM, Disk) is the Factory** 🏭⚙️
    
    - The CEO (Kernel) controls which workers (Apps) can use the machines (Hardware).