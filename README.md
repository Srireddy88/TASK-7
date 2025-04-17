## TASK-7 DAY-7

# Monitor System Resources Using Netdata

## Objective
Install Netdata using Docker and visualize system and application performance metrics.

---

## Tools Used
- **Netdata** (open-source monitoring tool)
- **Docker**

---

Steps Followed from link : (https://learn.netdata.cloud/docs/netdata-agent/installation/docker#:~:text=Using%20the%20docker%2Dcompose%20command&text=From%20your%20project%20directory%2C%20start,docker%2Dcompose%20up%20%2Dd%20.&text=If%20you%20plan%20to%20connect,your%20Space's%20%22Nodes%22%20view.)

1. Pulled and ran the Netdata container:
   ```bash
   docker run -d --name=netdata \
     -p 19999:19999 \
     --cap-add SYS_PTRACE \
     --security-opt apparmor=unconfined \
     -v netdataconfig:/etc/netdata \
     -v netdatalib:/var/lib/netdata \
     -v netdatacache:/var/cache/netdata \
     -v /etc/passwd:/host/etc/passwd:ro \
     -v /etc/group:/host/etc/group:ro \
     -v /proc:/host/proc:ro \
     -v /sys:/host/sys:ro \
     -v /etc/os-release:/host/etc/os-release:ro \
     netdata/netdata
   ```
# Accessed the dashboard at:
```bash
http://localhost:19999
```
   
# Checked logs by entering the container:
```bash
docker exec -it netdata bash
cd /var/log/netdata
```
![Screenshot 2025-04-17 203120](https://github.com/user-attachments/assets/21bb3523-2f4a-4c11-b3c5-491bc1bc2d2b)
![Screenshot 2025-04-17 204655](https://github.com/user-attachments/assets/b2e1ffc7-337f-4c66-9df3-3fc04d7478ea)

## Explored real-time system metrics:
- CPU usage (per core and total)
- Memory usage
- Disk I/O
- Network traffic
- Docker container metrics
