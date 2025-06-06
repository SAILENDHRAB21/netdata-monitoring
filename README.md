# 🖥️ Netdata System Monitoring with Docker

## 📌 Objective
Monitor system and application performance metrics such as CPU, memory, disk I/O, and Docker container stats using **Netdata**, a lightweight open-source monitoring tool, running inside a Docker container.

---

## 🧰 Tools Used
- [Netdata](https://www.netdata.cloud/)
- Docker
- GitHub (for version control and documentation)

---

## 🐳 How to Run Netdata via Docker

Make sure Docker is installed on your machine. Then, run the following command in your terminal:

```bash
docker run -d \
  --name=netdata \
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
