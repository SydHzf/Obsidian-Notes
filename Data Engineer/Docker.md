___
	In Docker Compose, each service runs in a separate container, which acts like an independent system but does NOT have a full operating system. Instead, all containers share the host OS kernel while being isolated. These containers communicate with each other using a Docker network.
### **How Docker Containers Work in Docker Compose**

- Each service runs in **its own container** but **shares the host OS kernel** (usually Linux).
- Containers are **lightweight**, unlike virtual machines (VMs), because they **don’t need a full OS**—just the necessary files, libraries, and dependencies.
- All services **communicate over a virtual Docker network** (by default, a bridge network).