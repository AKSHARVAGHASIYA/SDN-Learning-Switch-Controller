# SDN Learning Switch Controller

## 📌 Project Title

**SDN Learning Switch Controller**

---

## 📖 Problem Statement

Implement a controller that mimics a learning switch by dynamically learning MAC addresses and installing forwarding rules.

---

## 🎯 Objective

The objective of this project is to design and implement a Software Defined Networking (SDN) based learning switch using Mininet and the Ryu controller. The controller dynamically learns MAC-to-port mappings and installs flow rules to improve network efficiency and reduce unnecessary flooding.

---

## 🛠️ Technologies Used

* **Mininet** – Network Emulator
* **Ryu Controller** – SDN Controller
* **OpenFlow Protocol** – Communication between switch and controller
* **Docker** – For running Ryu controller
* **Python** – Controller implementation

---

## 🧩 System Architecture

* 1 Switch (s1)
* 2 Hosts (h1, h2)
* Remote SDN Controller

---

## ⚙️ Working Principle

1. When a packet arrives, the switch sends it to the controller (`packet_in` event).
2. The controller learns the source MAC address and stores it in a table.
3. If the destination MAC is known, the controller installs a flow rule and forwards the packet.
4. If unknown, the packet is flooded to all ports.
5. Future packets are forwarded directly without flooding.

---

## 🚀 Setup and Execution 
(You use your paths)

### Step 1: Run Ryu Controller (Docker)

```bash
sudo docker run -it --rm --privileged \
--platform linux/amd64 \
--network host \
-v /home/akshar:/app \
osrg/ryu
```

Inside Docker:

```bash
cd /app
ryu-manager learning_switch.py
```

---

### Step 2: Run Mininet (New Terminal)

```bash
sudo mn --controller=remote --switch=ovsk
```

---

### Step 3: Test Connectivity

Inside Mininet:

```bash
pingall
```

---

## 📊 Expected Output

* Initially packets are flooded.
* Controller learns MAC addresses dynamically.
* Flow rules are installed.
* Final result:

```
*** Results: 0% dropped (2/2 received)
```
<img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/aa10ae4a-a705-4478-9284-a9b301e79c38" />

---

## 🧪 Test Scenarios

### Scenario 1: First Ping

* Behavior: Flooding
* Reason: MAC address unknown

### Scenario 2: Subsequent Ping

* Behavior: Direct forwarding
* Reason: Flow rule installed

---

## 📈 Performance Observation

* Reduced packet flooding after learning
* Improved forwarding efficiency
* Zero packet loss observed
* Dynamic flow table updates

---

## 📸 Proof of Execution

* Mininet `pingall` output showing 0% packet loss
* Ryu controller logs showing `packet in` events
* Flow rule installation

---

## 📚 Key Concepts

* SDN Architecture
* Control Plane vs Data Plane
* OpenFlow Protocol
* MAC Learning
* Flow Tables

---

## ✅ Conclusion

The SDN Learning Switch Controller successfully demonstrates dynamic MAC address learning and efficient packet forwarding using OpenFlow rules. The controller reduces unnecessary flooding and improves network performance through centralized control.

---

## 🔗 References

* https://mininet.org
* https://ryu.readthedocs.io
* OpenFlow Specification

---

## 👨‍💻 Author

**Akshar Vaghasiya**
