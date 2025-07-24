

---

# **SDN-Based Intelligent Network Traffic Management Using LSTM Predictions**

## 📌 **Project Overview**

In the era of smart mobility and connected devices, traditional networking fails to adapt to the dynamic traffic patterns of modern vehicular and mobile networks. This project presents a Software-Defined Networking (SDN) solution that leverages Deep Learning (LSTM) to predict network congestion and dynamically reroute traffic for improved Quality of Service (QoS) and resource optimization.

## 🚀 **Key Features**

* ✅ Predictive Congestion Management using LSTM
* ✅ Real-time Traffic Rerouting via Ryu SDN Controller
* ✅ Integration of SUMO mobility simulation with Mininet
* ✅ Proactive Flow Rule Placement to Avoid Congestion
* ✅ Modular and Scalable Python-based Implementation

---

## 📂 **Project Structure**

```
📁 SDN-Traffic-Management
│
├── README.md                  ← This file
├── topology.py                ← Mininet Topology Definition (10 APs, 50 nodes each)
├── my_controller.py           ← Ryu Controller Script (LSTM-based rerouting)
├── sdn_controller.py          ← Advanced Ryu Controller with SUMO integration
├── lstm_model/                ← LSTM model training and weights (.h5)
├── sumo_simulation.py         ← SUMO TraCI Interface Script
├── dataset/                   ← CSV datasets from SUMO and Mininet
├── prediction_sender.py       ← UDP Client to send predictions to Ryu Controller
└── reports/                   ← Final report (project documentation)
```

---

## 🧠 **Abstract**

This project introduces an intelligent traffic management system in SDN-based networks. Using LSTM neural networks, future congestion at Access Points (APs) is predicted based on mobility and network parameters. Predictions are sent via UDP to a Ryu controller, which proactively adjusts OpenFlow rules to route traffic through the least congested APs, reducing latency, packet loss, and improving throughput.

---

## 🛠️ **Technologies Used**

| Technology         | Purpose                                                    |
| ------------------ | ---------------------------------------------------------- |
| **Mininet**        | Emulates SDN topology with 10 APs and 500 mobile nodes     |
| **SUMO**           | Simulates vehicle mobility (speed, acceleration, position) |
| **Ryu Controller** | SDN Controller implementing flow rule placement            |
| **LSTM**           | Predicts network metrics: packet rate, latency, bandwidth  |
| **Python**         | Programming language for all modules                       |
| **UDP/JSON**       | Protocols for lightweight real-time prediction transfer    |
| **HDF5**           | Stores trained LSTM models                                 |

---

## 🧪 **System Architecture**

### 1. **Input**

* SUMO mobility data
* Mininet network stats (packet rate, latency, bandwidth)

### 2. **LSTM Model**

* Trained using time-series data
* Predicts congestion-related metrics for each AP

### 3. **UDP Communication**

* Sends predictions to the Ryu Controller

### 4. **Ryu SDN Controller**

* Calculates congestion score
* Reroutes flows via OpenFlow rules to least congested AP

---

## 🔁 **Workflow**

1. Start **SUMO simulation** to generate mobility data.
2. Launch **Mininet topology** with 10 APs, each with 50 nodes.
3. **Train the LSTM** model on historical network and mobility data.
4. Run **prediction sender** to forward forecasts via UDP.
5. **Ryu controller** dynamically reroutes flows based on congestion scores.

---
## BLOCK DOAGRAM ##
<img width="716" height="351" alt="image" src="https://github.com/user-attachments/assets/325e02b0-c4f2-4b71-b178-e8d42eb17e58" />

---
## **FLOW CHART** 
<img width="731" height="552" alt="image" src="https://github.com/user-attachments/assets/7d886b04-1b43-4443-a8a3-0b1fc135e2ea" />

## **UNDERSTANDING FLOW CHART**

1.	*LSTM Model*- It is a type of Recurrent Neural Network (RNN) that excels at understanding temporal (time-based) dependencies, making it ideal for forecasting time-series data like network traffic. It takes in real-time and historical network data (e.g., packet load, latency, throughput at different nodes or access points) and gives out predictions of which links or APs (Access Points) are likely to be congested soon.
2.	*RYU Controller*- It acts as central brain of the SDN network which separates control plane (decisions) from the data plane (actual packet forwarding). The controller controls the flow rules while devices execute them. It receives predictions from the LSTM model and makes real-time decisions on routing and traffic flow.
3.	*Flow Rule Table* – A flow rule table is a set of instructions installed on SDN-enabled devices (e.g., switches or Access Points) to control data traffic. Each rule can specify conditions such as source/destination IP, priority, and corresponding actions (e.g., forward, drop, redirect) [1][4]. In our setup, the table is constructed based on predictions from the LSTM model and the current network state. The SDN controller then generates optimized flow rules to reroute or balance traffic loads accordingly [9].
---

## 📊 **Results**

* **Test Accuracy**: 83% in AP prediction
* **Confusion Matrix**: Shows high diagonal dominance
* **Flow Redirection**: Reduces congestion in high-load APs
* **QoS Improvement**: Lowered latency and packet loss post rerouting

 <img width="691" height="346" alt="image" src="https://github.com/user-attachments/assets/fa01b775-7e03-4595-8d4c-631dd9bf2de2" />


<img width="625" height="420" alt="image" src="https://github.com/user-attachments/assets/20c7f606-fc9e-4fe1-8a43-596ef643c753" />

<img width="470" height="422" alt="image" src="https://github.com/user-attachments/assets/a7431402-ca22-499e-985d-2e3c5bf95b22" />

<img width="732" height="467" alt="image" src="https://github.com/user-attachments/assets/2d5e81e4-1b87-4044-946a-ffab7c95e449" />


---

---

## 📈 **Simulation Parameters**

| Parameter           | Value                 |
| ------------------- | --------------------- |
| Number of APs       | 10                    |
| Number of Nodes     | 500                   |
| Node Speed          | 0–30 km/h             |
| Topology            | Linear                |
| Mobility Model      | Flow-Based            |
| SDN Controller      | Ryu with OpenFlow 1.3 |
| Prediction Protocol | UDP on Port 9999      |

---

## 💡 **Applications**

* Vehicular Networks (V2X)
* Smart City Traffic Management
* QoS-Aware 5G Networks
* IoT and Edge Computing Environments
* DDoS Detection and Mitigation

---

## ✅ **Advantages**

* Real-time congestion prediction
* Scalable to large network deployments
* Optimized AP selection and resource usage
* Lightweight LSTM reduces computational cost
* Enhances QoS for critical applications

---

## ⚠️ **Limitations**

* Performance depends on quality of training data
* May require tuning for large-scale dynamic environments
* Needs SDN infrastructure for deployment

---

## 🔮 **Future Scope**

* Real-time deployment on hardware switches
* Auto-adjust weights in congestion formula dynamically
* GUI for live monitoring of congestion and AP predictions
* Multi-controller SDN support for distributed architectures

---

## 📚 **References**

* N. Feamster et al., “A Survey of Software-Defined Networking,” IEEE.
* A. Diro and N. Chilamkurti, “Deep Learning in SDN,” IEEE TNSM.
* J.H. Saltzer et al., “End-to-End Arguments in System Design.”
* ResearchGate & IEEE: LSTM models in SDN
* [Mininet](http://mininet.org/), [SUMO](https://sumo.dlr.de/), [Ryu](https://osrg.github.io/ryu/)

---
