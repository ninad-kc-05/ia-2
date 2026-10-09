# Wireless Communication & Mobile Networks — IA2 Study Notes

> **Purpose:** Readable, GitHub-friendly notes for the IA2 question bank, organized by module and question.
>
> **How to use these notes**
> - For **7-mark answers**, learn the explanation, draw the suggested diagram, and include the analysis/example.
> - For **2-mark answers**, learn the definition and the key distinction or function.
> - The question bank and syllabus are the basis for the topics and organization. Formula explanations and examples below are written as study aids.

## IA2 pattern and syllabus map

| Module | Main syllabus topics | Question-bank coverage | Expected preparation |
|---|---|---|---|
| **Module 4 — Signal Propagation and Interference** | LOS/NLOS, path loss and shadowing, multipath fading, noise, interference, mitigation | Q1–Q5, 7 marks each | Prepare all five long answers |
| **Module 5 — Mobile Network Architecture** | Cellular components, call flow, handover, roaming, SIM/IMSI/authentication, packet core | Q1–Q5, short answers | Prepare every short topic |
| **Module 6 — Future Trends in Wireless Communication** | 5G, applications, IoT, connected devices, edge computing, AI in telecom, 6G | Q1–Q5, 7 marks each | Prepare all five long answers |

---

# Module 4 — Signal Propagation and Interference

## Q1. Analyze the differences between LOS and NLOS propagation. Explain how obstacles and propagation mechanisms affect signal reception, with examples. *(7 marks)*

### 1. Introduction

Wireless communication sends information through electromagnetic waves. The signal path between a transmitter and receiver depends on the surrounding environment. Two important propagation conditions are **Line-of-Sight (LOS)** and **Non-Line-of-Sight (NLOS)**.

- **LOS propagation:** A direct, unobstructed path exists between the transmitter and receiver.
- **NLOS propagation:** The direct path is blocked or unavailable. The receiver may receive the signal through reflected, diffracted, or scattered paths.

### 2. LOS versus NLOS

| Feature | LOS | NLOS |
|---|---|---|
| Direct path | Direct path is clear | Direct path is blocked or unavailable |
| Typical environment | Open areas, rural areas, clear rooftop links | Dense cities, indoor areas, streets between buildings |
| Signal strength | Often stronger and more predictable | Often weaker and more variable |
| Path loss | Usually lower for comparable conditions | Often higher because the direct path is obstructed |
| Multipath | Usually less severe when the direct path dominates | Often more significant because several indirect paths may arrive |
| Reliability | Generally easier to plan | Depends strongly on obstacles and reflections |
| Example | A clear link between two antennas | A phone communicating around buildings in a city |

### 3. How obstacles affect reception

Buildings, hills, trees, vehicles, and walls can absorb, block, or redirect radio waves. The received signal can become weaker, fluctuate over time, or arrive through multiple paths.

Three important mechanisms are:

1. **Reflection:** A radio wave strikes a large surface, such as a building or wall, and bounces away in another direction.
2. **Diffraction:** A wave bends around an obstacle or travels into a region that is not directly visible from the transmitter.
3. **Scattering:** A wave encounters smaller or irregular objects, such as foliage, rough surfaces, or street furniture, and spreads in several directions.

These mechanisms can allow communication even without a clear direct path, but they can also create signal variations and additional path loss.

### 4. Practical examples

- **LOS:** A wireless link between two antennas on rooftops with a clear view of one another.
- **NLOS:** A mobile user standing behind a building. The signal may reach the phone after reflecting from nearby buildings or diffracting around an edge.
- **Indoor NLOS:** A router is in one room and the phone is in another, with walls weakening or redirecting the signal.

### 5. Suggested diagram

Draw two simple cases:

- **LOS:** `Transmitter  ---------------->  Receiver`
- **NLOS:** `Transmitter  ---> [Building] ---> reflected/diffracted path ---> Receiver`

Label the building as an obstacle and show the indirect path with a bent arrow.

### 6. Conclusion

LOS provides a clear direct path and is usually more predictable. NLOS communication depends on reflection, diffraction, and scattering, so received signal strength and quality are more affected by the environment.

**Keywords to remember:** direct path, obstruction, reflection, diffraction, scattering, path loss, multipath.

---

## Q2. Analyze the factors contributing to path loss and explain how increasing path loss affects received signal strength and link performance. *(7 marks)*

### 1. Definition

**Path loss** is the reduction in signal power as a radio wave travels from the transmitter to the receiver. As the signal spreads over a larger area and interacts with the environment, less power is available at the receiver.

### 2. Factors affecting path loss

1. **Distance:** As the transmitter–receiver distance increases, the signal spreads out and received power generally decreases.
2. **Frequency:** Path loss generally increases with frequency for comparable distance and antenna conditions.
3. **Obstacles and clutter:** Buildings, walls, trees, and terrain can block or weaken the signal.
4. **Environment:** Open rural areas, dense urban streets, and indoor environments produce different propagation conditions.
5. **Antenna height and placement:** Antenna position affects obstruction and the available propagation path.
6. **Atmospheric conditions:** Depending on the frequency and environment, atmospheric absorption and rain can contribute to additional attenuation.
7. **Shadowing:** Large objects may partially block the signal, producing slower variations in received power as the user moves.

### 3. Useful equations

A commonly used log-distance model is:

### Log-Distance Path Loss Model

The log-distance path loss model estimates how signal power decreases as the distance between a transmitter and receiver increases.

**Formula:**

$$
PL(d)=PL(d_0)+10n\log_{10}\left(\frac{d}{d_0}\right)
$$

**Where:**
- $PL(d)$ = Path loss at distance $d$ (dB).
- $PL(d_0)$ = Path loss at the reference distance $d_0$ (dB).
- $d$ = Distance between the transmitter and receiver.
- $d_0$ = Reference distance.
- $n$ = Path-loss exponent, determined by the propagation environment.
- $\log_{10}$ = Base-10 logarithm.

**Example:**

Given:
- $PL(d_0)=40$ dB
- $d_0=10$ m
- $d=100$ m
- $n=3$

Substituting into the formula:

$$
PL(d)=40+10(3)\log_{10}\left(\frac{100}{10}\right)
$$

$$
PL(d)=40+30\log_{10}(10)
$$

Since $\log_{10}(10)=1$:

$$
PL(d)=40+30=\boxed{70\text{ dB}}
$$

**Result:** The path loss at 100 metres is **70 dB**.

**Key takeaway:**

As the distance between the transmitter and receiver increases, path loss generally increases, causing the received signal power to decrease.

> **Remember:** Higher path loss generally means weaker received signal power and potentially poorer communication quality.

**Where:**
- $PL(d)$ is the path loss at distance $d$.
- $PL(d_0)$ is the known path loss at the reference distance $d_0$.
- $n$ is the path-loss exponent, which depends on the propagation environment.

### Received Signal Power

The received signal power can be estimated using the simplified link-budget equation:

$$
P_r \approx P_t - PL
$$

**Where:**
- $P_r$ = Received signal power (dBm).
- $P_t$ = Transmitted signal power (dBm).
- $PL$ = Path loss (dB).

**Note:** A complete link budget may also include antenna gains, cable losses, and other system losses.

**Key takeaway:**

$$
\text{Higher Path Loss} \Rightarrow \text{Lower Received Signal Power}
$$
### 4. Effect of increasing path loss

The sequence is:

**Path loss increases → received power decreases → signal-to-interference-plus-noise ratio (SINR) may decrease → link performance can deteriorate.**

Possible effects include:

- Lower received signal strength.
- Lower achievable data rate or more conservative modulation and coding.
- Increased packet errors and retransmissions.
- Reduced coverage at the cell edge.
- More dropped connections or call failures when the signal becomes too weak.

The actual effect also depends on interference, receiver sensitivity, antenna gains, transmit power, and the system's link adaptation.

### 5. Example

A phone close to a base station usually receives a stronger signal than a phone far away behind several buildings. The distant phone may experience greater path loss and lower SINR, so data speeds may fall or the connection may become unreliable.

### 6. Suggested diagram

Draw a transmitter and receiver separated by distance \(d\). Show the signal spreading outward and label:

`Greater distance / more obstacles → higher path loss → lower received power`

### 7. Conclusion

Path loss is influenced by distance, frequency, obstacles, antenna placement, and the propagation environment. Higher path loss reduces received power and can lower data rates, reduce coverage, and increase the risk of connection failure.

**Keywords to remember:** distance, frequency, environment, shadowing, path-loss exponent, received power, SINR.

---

## Q3. Explain how reflection, diffraction, and scattering produce multipath fading. How can fading cause poor signal quality or call drops? *(7 marks)*

### 1. Definition of multipath

**Multipath propagation** occurs when copies of the transmitted radio signal reach the receiver along different paths. The copies may have different delays, phases, and amplitudes because they have travelled different distances or interacted with different objects.

When these copies combine, the total received signal can become stronger or weaker. The rapid variation in received signal strength caused by the combination of paths is called **multipath fading**.

### 2. Mechanisms that create multiple paths

- **Reflection:** Waves bounce from surfaces such as buildings, walls, and the ground.
- **Diffraction:** Waves bend around corners, roof edges, or other obstacles.
- **Scattering:** Waves spread in many directions after interacting with irregular surfaces or small objects.

The receiver may therefore get one direct component and several indirect components—or only indirect components in an NLOS environment.

### 3. Constructive and destructive interference

When the signal copies arrive:

- **Constructive interference:** Their phases align sufficiently for them to reinforce one another, making the received signal stronger.
- **Destructive interference:** Their phases oppose one another, causing partial or severe cancellation and a weaker received signal.

As the user or surrounding objects move, path lengths and phases change. A signal that was strong at one location may become weak only a short distance away.

### 4. Common fading descriptions

- **Rayleigh fading:** A common model when there is no dominant direct LOS component and many indirect components combine.
- **Rician fading:** A common model when a dominant component, often a LOS path, exists along with weaker multipath components.

These are statistical models used to describe different propagation conditions.

### 5. Effects on communication

Multipath fading can cause:

1. Rapid changes in received signal strength.
2. Increased bit errors and packet loss.
3. Distortion or inter-symbol interference when delayed copies overlap symbols.
4. Retransmissions and reduced effective throughput.
5. Loss of synchronization or failure to decode control information.
6. A radio-link failure or dropped call if the connection cannot be maintained.

Modern systems use techniques such as diversity, channel estimation, equalization, coding, and adaptive modulation to reduce the impact of fading.

### 6. Example

A person walking through a city may receive signals reflected from several buildings. At one point the copies reinforce one another; after moving a short distance, their phases may change and the copies can partially cancel. The phone may then show fluctuating signal quality or experience interrupted data.

### 7. Suggested diagram

Draw a transmitter, three paths (direct, reflected from a building, and diffracted around a corner), and one receiver. Label the paths “different length / delay / phase.” Then draw the copies combining at the receiver.

### 8. Conclusion

Reflection, diffraction, and scattering create multiple signal paths. Their copies can reinforce or cancel each other, producing fading. Severe fading can increase errors, reduce throughput, and—in difficult conditions—cause a dropped connection.

**Keywords to remember:** multipath, reflection, diffraction, scattering, phase, constructive, destructive, Rayleigh, Rician, call drop.

---

## Q4. Analyze different sources of noise and differentiate thermal noise from interference. *(7 marks)*

### 1. Introduction

A wireless receiver does not receive only the desired signal. Unwanted electrical disturbances and transmissions from other sources can affect reception. Two important impairments are **noise** and **interference**.

- **Noise** is unwanted random energy that affects the received signal.
- **Interference** is unwanted energy from other transmissions or systems that overlaps with the desired communication.

### 2. Common sources of noise

1. **Thermal noise:** Produced by the random thermal motion of charge carriers in electronic components. It is present even when no other transmitter is active.
2. **Shot noise:** Associated with the discrete nature of electric charge in electronic devices.
3. **Flicker noise:** Low-frequency noise found in electronic components.
4. **Atmospheric noise:** Caused by natural electrical activity, including lightning.
5. **Cosmic noise:** Radio energy originating from celestial sources.
6. **Man-made noise:** Unwanted electrical emissions from equipment and electronic devices.

For many receiver calculations, thermal noise is especially important.

### 3. Thermal noise equation

The available thermal noise power can be expressed as:

\[
N=kTB
\]

where:

- \(N\) = noise power in watts,
- \(k\) = Boltzmann's constant, approximately \(1.38\times10^{-23}\,\text{J/K}\),
- \(T\) = absolute temperature in kelvin,
- \(B\) = receiver bandwidth in hertz.

Increasing the bandwidth or temperature increases the total thermal noise power.

A commonly used approximate thermal noise density at room temperature is about \(-174\ \text{dBm/Hz}\). The receiver's noise figure adds to the effective noise level.

### 4. Thermal noise versus interference

| Feature | Thermal noise | Interference |
|---|---|---|
| Origin | Random thermal motion in electronic components | Unwanted signals from other transmitters or systems |
| Presence | Always present in practical receivers | Depends on nearby transmissions and frequency use |
| Typical examples | Noise generated by receiver circuitry | Other cells, nearby radios, overlapping channels |
| Main dependence | Temperature and bandwidth | Transmitters, channel allocation, power, distance, and propagation |
| Common mitigation | Low-noise receiver design and suitable bandwidth | Frequency planning, power control, coordination, filtering |

### 5. Important types of radio interference

- **Co-channel interference (CCI):** Interference from another transmitter using the same frequency channel.
- **Adjacent-channel interference (ACI):** Interference from a nearby frequency channel, often because of imperfect filtering or insufficient channel separation.

### 6. Signal-to-interference-plus-noise ratio

A useful measure is:

\[
SINR=\frac{S}{I+N}
\]

where \(S\) is desired signal power, \(I\) is interference power, and \(N\) is noise power, measured in compatible linear units.

Higher SINR generally allows more reliable reception and/or a higher data rate. If interference or noise increases while the desired signal remains unchanged, SINR decreases.

### 7. Example

If two nearby cells transmit on the same frequency and their coverage areas overlap, a user near the cell boundary may receive unwanted energy from the other cell. This is co-channel interference. Even if the desired signal is reasonably strong, interference can lower SINR and increase errors.

### 8. Conclusion

Noise is unwanted energy arising from physical and electronic sources, while interference is unwanted energy from other transmissions. Thermal noise depends on temperature and bandwidth; interference can often be reduced through better frequency planning, power control, and coordination.

**Keywords to remember:** thermal noise, shot noise, flicker noise, CCI, ACI, bandwidth, SINR.

---

## Q5. Explain how power control and frequency planning reduce interference and improve signal quality. *(7 marks)*

### 1. Introduction

In a cellular network, many users and base stations operate in nearby areas. If transmissions use excessive power or reuse the same frequencies without proper planning, unwanted signals can interfere with desired communication.

Two useful interference-management methods are **power control** and **frequency planning**.

### 2. Power control

Power control adjusts a transmitter's output power to meet communication requirements without using more power than necessary.

**How it helps:**

1. A nearby user can transmit at lower power instead of overpowering other users.
2. Lower unnecessary transmit power reduces interference to neighbouring cells.
3. It can help balance received signal levels among users.
4. It can reduce mobile-device battery consumption.
5. The network can increase power when needed, subject to system limits, to maintain a usable link.

**Key idea:** Use enough power to maintain the required link quality, but avoid unnecessarily high power.

### 3. Frequency planning

Frequency planning assigns channels to cells or sectors to reduce harmful overlap.

- **Frequency reuse:** The same frequency channels can be reused in cells separated far enough to limit interference.
- **Cluster size \(N\):** The number of cells in a frequency-reuse cluster in a traditional hexagonal cellular model.
- **Reuse distance:** The distance between co-channel cell centres is commonly approximated by

\[
D=R\sqrt{3N}
\]

where \(R\) is the cell radius and \(N\) is the cluster size.

In this simplified model, increasing \(N\) increases co-channel reuse distance, which can reduce co-channel interference. However, it also reduces how frequently a channel set is reused and may reduce capacity per area. Real networks use more advanced reuse and scheduling techniques, but the relationship is useful for understanding the concept.

### 4. How the methods work together

| Method | Main action | Expected benefit |
|---|---|---|
| Power control | Adjusts transmit power | Reduces unnecessary interference and power use |
| Frequency planning | Separates or coordinates channel use | Reduces co-channel and adjacent-channel interference |
| Combined use | Controls both power and frequency allocation | Can improve SINR, link reliability, and network efficiency |

### 5. Effect on signal quality

Reducing interference can increase SINR. Higher SINR generally supports fewer errors, more reliable communication, and potentially higher data rates. The network may also be able to serve users more efficiently.

The result depends on the network design: overly low power can weaken the desired signal, and overly conservative frequency reuse can reduce capacity. The goal is to balance coverage, interference, and capacity.

### 6. Example

Suppose two nearby cells reuse the same channel and users at their edges interfere with each other. A network can coordinate channel use through frequency planning and reduce unnecessary power from nearby users. The desired signal then becomes stronger relative to interference, improving SINR.

### 7. Suggested diagram

Draw several hexagonal cells. Use one colour or label for cells in the same frequency-reuse group and show co-channel cells separated by reuse distance \(D\). Add a note: “Power control limits unnecessary transmit power.”

### 8. Conclusion

Power control manages transmission strength, while frequency planning manages where and how frequencies are reused. Used appropriately, both techniques reduce interference, improve SINR, and help maintain reliable wireless links.

**Keywords to remember:** power control, frequency reuse, cluster size, reuse distance, co-channel interference, SINR, capacity.

---

# Module 5 — Mobile Network Architecture

> These are short-answer topics. For a 2-mark response, aim for a clear definition plus one purpose, distinction, or example. The exact number of short questions selected in the assessment may vary, so prepare every topic below.

## Q1. Explain the types of handover. *(2 marks)*

**Handover** is the process of transferring an ongoing call or data session from one cell, base station, or access point to another as the user moves or network conditions change.

- **Hard handover:** The old connection is released before the new connection is established. It is often described as **break-before-make**.
- **Soft handover:** The new connection is established before the old one is released. It is often described as **make-before-break** and can allow a mobile device to communicate with more than one cell during the transition.
- **Horizontal handover:** Transfer between access points or cells using the same general access technology, such as between two cellular cells.
- **Vertical handover:** Transfer between different access technologies, such as moving from Wi-Fi to a cellular network.

**Why it is needed:** Handover helps maintain service as the user moves through different coverage areas or as radio conditions change.

## Q2. Differentiate between national and international roaming. *(2 marks)*

**Roaming** allows a subscriber to use a mobile service through a visited network when the subscriber is outside the normal coverage or service area of the home network.

| National roaming | International roaming |
|---|---|
| The subscriber uses a visited network in the same country. | The subscriber uses a visited network in another country. |
| May help provide coverage where the home operator has limited service. | Allows service while travelling abroad, subject to operator agreements. |
| Charges and service conditions depend on the operators and plan. | Charges, agreements, and service conditions may differ substantially by country and plan. |

- **Home network / HPLMN:** The subscriber's home Public Land Mobile Network.
- **Visited network / VPLMN:** The network currently providing service while the subscriber is roaming.

## Q3. Explain the role of SIM, IMSI, and authentication. *(2 marks)*

- **SIM (Subscriber Identity Module):** A subscriber module that stores information used to identify the subscriber and supports security procedures.
- **IMSI (International Mobile Subscriber Identity):** A subscriber identity used by the mobile network to identify a subscription. It is distinct from the phone number.
- **Authentication:** A security procedure that checks whether the subscriber or device is authorised to access the network.

**Basic idea:** The network initiates an authentication procedure; the SIM and network use security credentials and challenge-response calculations to verify the subscription. The network then permits access according to the result and applicable service rules.

**Remember:** SIM = subscriber module; IMSI = subscriber identity; authentication = identity/security verification.

## Q4. Differentiate between circuit-switched and packet-switched communication. *(2 marks)*

| Circuit-switched communication | Packet-switched communication |
|---|---|
| A dedicated communication path or circuit is established for the session. | Data is divided into packets and sent over shared network resources. |
| Resources may remain reserved for the duration of the connection. | Resources can be shared dynamically among many users. |
| Traditional telephony is a common example. | Internet data and IP-based services are common examples. |
| Can be inefficient when reserved resources carry no useful data. | Efficient for bursty data, though delay and delivery can vary with congestion and scheduling. |

Modern mobile networks use packet-based infrastructure for data services; voice service implementation depends on the generation and network architecture.

## Q5. Write short notes on BTS, UE, IMSI, SIM, authentication, handover, and roaming. *(2 marks / short-note preparation)*

- **BTS (Base Transceiver Station):** Radio access equipment that communicates over the air with mobile devices in a cellular network. In modern systems, terminology and equipment architecture vary by generation.
- **UE (User Equipment):** The user's device, such as a mobile phone, tablet, or cellular modem, that connects to the network.
- **IMSI:** A subscriber identity used by the mobile network; it is not the same as the phone number.
- **SIM:** A subscriber module that stores identity/security-related information and supports authentication.
- **Authentication:** The process by which the network verifies that a subscriber is authorised to access services.
- **Handover:** Transfer of an ongoing connection from one cell or access point to another to preserve service.
- **Roaming:** Use of a visited network when the subscriber is outside the home network's normal service area.

### Extra syllabus topic: simplified call setup flow

The question bank does not list a dedicated long question on call flow, but it is included in the syllabus, so learn this basic sequence:

1. The user initiates a call or service request.
2. The device sends the request through the radio access network.
3. The network checks access and security requirements.
4. The core network routes or establishes the requested service.
5. The destination is alerted or the data session is established.
6. The network maintains the session and later releases resources when it ends.

This is a high-level learning flow; exact signalling differs between network generations and between voice and data services.

### Extra syllabus topic: packet core networks

A **packet core** provides functions that support packet-data connectivity, mobility, authentication/policy interaction, and routing toward external data networks. At a high level, the device connects through the radio access network to core-network functions, which help establish and manage data connectivity.

---

# Module 6 — Future Trends in Wireless Communication

## Q1. Analyze how 5G supports smart-city applications and autonomous systems, considering connectivity, latency, reliability, and data requirements. *(7 marks)*

### 1. Introduction

**5G** is a generation of mobile communication designed to support high data rates, responsive communication, and large numbers of connected devices. These capabilities can support smart-city infrastructure and connected or autonomous systems.

The actual performance depends on deployment, spectrum, coverage, device capability, network load, and application design. Not every 5G connection automatically provides ultra-low latency or guaranteed reliability.

### 2. Important 5G service categories

A common high-level view describes three service categories:

- **eMBB (enhanced Mobile Broadband):** Supports high data rates and bandwidth-intensive applications.
- **URLLC (Ultra-Reliable Low-Latency Communications):** Targets applications that need very low delay and high reliability.
- **mMTC (massive Machine-Type Communications):** Supports large populations of connected devices, often sending small amounts of data.

These categories describe different design goals rather than meaning that every application receives all three benefits at once.

### 3. Smart-city applications

1. **Intelligent traffic management:** Connected sensors and cameras collect traffic information. The network carries data to systems that can adjust signal timing or identify congestion.
2. **Smart surveillance and public safety:** Video and sensor data can help authorised systems detect incidents and coordinate responses.
3. **Smart utilities and grids:** Connected meters and infrastructure sensors report usage or equipment status.
4. **Environmental monitoring:** Sensors measure air quality, noise, temperature, or other local conditions.
5. **Emergency coordination:** Connected systems can help responders share relevant information when suitable coverage and service arrangements are available.

These applications need a combination of connectivity, suitable data rates, coverage, and timely data delivery.

### 4. Autonomous and connected systems

Autonomous vehicles and machines may use communication to supplement their own sensors and onboard processing.

- **Vehicle-to-vehicle (V2V):** Vehicles exchange relevant information with one another.
- **Vehicle-to-infrastructure (V2I):** Vehicles communicate with roadside or other infrastructure.
- **Collision warnings:** Timely information may help warn about hazards outside a vehicle's direct sensor view.
- **Platooning and coordination:** Connected vehicles may coordinate motion in supported systems.
- **Sensor/data sharing:** High data-rate links can support the exchange of selected information.

**Important:** Safety-critical autonomous driving must not rely blindly on a network connection; vehicles need appropriate onboard sensing, decision-making, and fail-safe behaviour because wireless coverage and delay can vary.

### 5. How 5G capabilities help

| Requirement | Relevant 5G goal | Example |
|---|---|---|
| High data volume | eMBB | Video and rich sensor data |
| Low delay | URLLC-oriented design | Responsive industrial or vehicle communication |
| Many devices | mMTC-oriented design | Smart meters and city sensors |
| Service separation | Network slicing, where deployed | Different logical network configurations for different needs |
| Wide-area connectivity | Cellular coverage and mobility support | Connected devices moving through the city |

**Network slicing** can provide logically separated network configurations for different service requirements, subject to the operator's implementation and resource availability.

### 6. Example: smart intersection

A smart intersection may use cameras and road sensors to estimate traffic conditions. A 5G connection carries selected information to an edge or central processing system, which analyses the data and updates traffic signals. Low delay can be useful for responsive control, while reliable coverage and secure system design remain important.

### 7. Suggested diagram

Draw:

`Sensors / Vehicles → 5G Radio Network → Edge or Core Processing → Traffic / Safety Application`

Add labels such as **high data rate**, **low latency**, **reliability**, and **many devices**.

### 8. Conclusion

5G can support smart cities and autonomous systems through high data rates, low-latency service designs, reliable communication targets, and connectivity for many devices. These capabilities enable applications such as traffic management, connected vehicles, smart utilities, and public-safety systems when supported by suitable network deployment and application design.

**Keywords to remember:** eMBB, URLLC, mMTC, smart city, V2V, V2I, latency, reliability, network slicing.

---

## Q2. Analyze the components of an IoT ecosystem and explain how sensing, connectivity, data processing, and applications interact. *(7 marks)*

### 1. Definition

The **Internet of Things (IoT)** is an ecosystem of physical objects equipped with sensors, software, and network connectivity that allows them to collect and exchange data. The data can be processed to monitor conditions, provide insights, or trigger actions.

### 2. Main components

A useful sequence is:

**Sense → Connect → Process → Act**

#### 1. Sensing and devices

Sensors measure physical conditions, such as:

- Temperature and humidity.
- Movement or presence.
- Light and pressure.
- Location or equipment status.

A device may also contain an actuator that performs an action, such as opening a valve or switching a motor.

#### 2. Connectivity

Connectivity transports sensor readings and control messages between devices, gateways, processing systems, and applications. Examples include:

- Wi-Fi.
- Bluetooth.
- Zigbee.
- LoRaWAN.
- Cellular IoT technologies such as NB-IoT.

The appropriate technology depends on range, power consumption, data rate, cost, coverage, and application requirements.

#### 3. Data processing and storage

Data may be processed locally on a device, at an edge gateway, or in a cloud platform. Processing can include:

- Cleaning and organising readings.
- Detecting unusual values.
- Storing historical data.
- Applying rules or analytics.
- Using AI/ML where appropriate to identify patterns or predict conditions.

Edge processing can respond quickly without sending every reading to a distant cloud, while cloud processing can support large-scale storage and broader analysis.

#### 4. Applications and user interface

Applications present information and allow users or other systems to take action. Examples include dashboards, mobile apps, alerts, reports, and automated control systems.

### 3. How the components interact

1. A sensor observes a physical condition.
2. The device converts the observation into digital data.
3. A wired or wireless connection carries the data.
4. A gateway, edge computer, or cloud platform processes the data.
5. An application displays a status, generates an alert, or chooses an action.
6. If the system has an actuator, a control command may be sent back to affect the physical environment.

Security, device management, and reliable connectivity are cross-cutting requirements across the ecosystem.

### 4. Example: smart agriculture

- **Sense:** Soil-moisture sensors measure water levels.
- **Connect:** A low-power network sends readings to a gateway or service.
- **Process:** Software compares the readings with configured thresholds and may consider other data.
- **Act:** The farmer receives an alert or an irrigation controller activates a pump.
- **Application:** A dashboard shows moisture history and irrigation status.

### 5. Suggested diagram

Draw four connected boxes:

`Sensors / Devices → Connectivity / Gateway → Edge or Cloud Processing → Application / Action`

Add a return arrow from “Application / Action” to “Devices / Actuators” to show feedback control.

### 6. Benefits and challenges

**Benefits:** remote monitoring, automation, improved visibility, timely alerts, and data-informed decisions.

**Challenges:** security and privacy, battery life, connectivity gaps, interoperability between devices, data quality, and managing many deployed devices.

### 7. Conclusion

An IoT ecosystem connects physical sensing devices to networks, processing platforms, and applications. Sensors collect data, connectivity transports it, processing turns it into useful information, and applications help people or machines take action.

**Keywords to remember:** sensors, devices, connectivity, gateway, edge, cloud, analytics, application, actuator.

---

## Q3. Analyze the role of edge computing in telecom and explain how processing closer to users affects latency, bandwidth, and network performance. *(7 marks)*

### 1. Definition

**Edge computing** places computing and data-processing resources closer to the devices or users that generate and consume data, rather than sending all data to a distant central cloud. In telecom, edge resources may be located near the radio access network or within the operator's network.

### 2. Traditional cloud path versus edge path

**Traditional remote-cloud path:**

`Device → Radio Access Network → Core / Transport Network → Remote Cloud → Response`

**Edge-assisted path:**

`Device → Radio Access Network → Nearby Edge Server → Response`

The edge path can avoid some of the transport to a remote data centre. However, the actual path depends on the operator architecture and where the application is hosted.

### 3. Main benefits

#### 1. Lower latency

Processing close to the user can reduce the distance data must travel and may reduce end-to-end response time. This is useful for applications that need quick feedback.

#### 2. Reduced backhaul bandwidth

Data can be filtered, summarised, or analysed near its source. Only relevant results may need to travel to a central cloud, reducing traffic over transport links.

#### 3. Better responsiveness

Local processing can support quick decisions for applications such as industrial monitoring, interactive services, and smart cameras.

#### 4. Potential resilience benefits

Some services can continue operating locally during certain backhaul or cloud disruptions if the edge system has the required data, logic, and local connectivity. This is not automatic; it depends on the design.

#### 5. Support for data-sensitive applications

Processing locally can help limit how much raw data leaves a site, though edge computing alone does not guarantee privacy or security.

### 4. Applications in telecom and connected systems

- **Autonomous and connected systems:** Nearby processing may help deliver timely information, while safety-critical decisions still need robust local fail-safe design.
- **Industrial automation:** Local analysis can help monitor equipment and respond to events quickly.
- **AR/VR and interactive applications:** Edge resources may reduce the time required to process certain requests.
- **Smart cameras:** Video can be analysed locally, sending only alerts or selected clips.
- **Network operations:** Operators can process local telemetry to monitor performance or detect issues.

### 5. Edge computing and 5G

5G can provide radio and core-network capabilities that work alongside edge computing. The radio link is only one part of total latency: processing time, transport delay, routing, application design, and congestion also matter. Placing an application at the edge may reduce some of these delays, but it cannot guarantee a particular latency by itself.

### 6. Limitations and trade-offs

- Edge locations have limited compute, storage, and power compared with large data centres.
- Deploying and maintaining many edge sites can be costly.
- Applications must manage updates, security, monitoring, and consistency across sites.
- Some workloads still need central cloud resources for large-scale storage or global analysis.

### 7. Suggested diagram

Draw a remote cloud far from the user and an edge server close to the base station. Show the cloud route as longer and the edge route as shorter. Label the possible effects: **lower latency** and **less backhaul traffic**.

### 8. Conclusion

Edge computing brings processing closer to users and devices. It can reduce response time, lower backhaul traffic, and improve responsiveness for selected telecom applications. The benefits depend on placement, network design, workload, and operational requirements.

**Keywords to remember:** edge server, proximity, latency, backhaul, local processing, 5G, responsiveness.

---

## Q4. Analyze how AI can be integrated into telecom and explain its role in network optimization, traffic management, and fault detection. *(7 marks)*

### 1. Introduction

Telecommunication networks generate large amounts of data about traffic, radio conditions, device behaviour, performance, and equipment health. **Artificial intelligence (AI)** and **machine learning (ML)** can analyse this data to identify patterns, make predictions, and support network-management decisions.

A simple workflow is:

**Monitor → Predict → Optimize → Detect / Recover**

AI recommendations should be checked against operational rules and safety constraints; not every network action should be automated without safeguards.

### 2. Network optimization

AI/ML can analyse network measurements to help operators choose or adjust configurations.

Possible tasks include:

- Estimating traffic demand in different cells.
- Supporting radio-resource allocation.
- Recommending power or configuration adjustments.
- Helping identify coverage or performance problems.
- Supporting beam or mobility optimisation where the system exposes relevant controls.

**Result:** Better use of network resources and potentially improved user experience, depending on the quality of the data and the control method.

### 3. Traffic management

Traffic changes by time, location, and event. AI models can use historical and live data to estimate demand.

AI can help:

1. Predict busy periods or local traffic spikes.
2. Detect congestion.
3. Recommend resource reallocation or load balancing.
4. Identify unusual traffic patterns.
5. Support capacity planning.

For example, a stadium event may cause a sudden rise in demand. Traffic predictions can help operators plan capacity and monitor congestion.

### 4. Fault detection and predictive maintenance

AI can learn patterns associated with normal equipment operation and help flag unusual measurements.

Applications include:

- Detecting abnormal performance in network equipment.
- Identifying a cell whose performance has deteriorated.
- Correlating alarms or measurements that may share a cause.
- Predicting possible equipment failure from trends in telemetry.
- Prioritising maintenance investigations.

Predictive maintenance can help operators investigate issues before they cause a major outage, but predictions need validation and should not be treated as certainty.

### 5. Self-healing concept

A simplified self-healing loop is:

1. **Collect:** Gather network measurements, logs, alarms, and performance indicators.
2. **Detect:** Identify a fault or abnormal condition.
3. **Diagnose:** Estimate the likely cause.
4. **Recommend:** Select a possible corrective action.
5. **Apply:** An authorised controller or operator applies the action.
6. **Verify:** Check whether the network recovered and whether side effects occurred.

Some systems automate parts of this loop; others keep a human operator in control.

### 6. Suggested diagram

Draw:

`Network Data → AI/ML Analysis → Prediction / Fault Detection → Recommended Action → Network Reconfiguration → Performance Feedback`

### 7. Benefits and challenges

**Benefits:** faster analysis of large data volumes, improved forecasting, quicker fault investigation, and more efficient resource use.

**Challenges:** poor or biased data, false alarms, model drift, explainability, security, privacy, and the risk of harmful automated changes. Operators need monitoring and rollback procedures.

### 8. Conclusion

AI can support telecom network optimisation, traffic forecasting, anomaly detection, and predictive maintenance. It helps convert network data into useful predictions and decisions, while reliable deployment requires good data, validation, monitoring, and safeguards.

**Keywords to remember:** AI, ML, network optimisation, traffic prediction, congestion, anomaly detection, predictive maintenance, self-healing.

---

## Q5. Analyze the conceptual vision of 6G and explain how its expected features may address future wireless limitations and requirements. *(7 marks)*

### 1. Introduction

**6G** is the conceptual next generation of wireless communication beyond 5G. Its exact specifications and deployment details are still evolving. The vision is to support future applications with greater capacity, more pervasive connectivity, improved sensing and computing integration, and better energy efficiency.

The following are research directions and expected concepts, not a guarantee that every future 6G network will implement every feature.

### 2. Why look beyond 5G?

Future systems may face increasing demands from:

- Larger volumes of data and more connected devices.
- Immersive extended-reality experiences and rich interactive media.
- Autonomous systems that need timely, dependable information.
- Connectivity in remote, aerial, maritime, or otherwise difficult-to-reach areas.
- Better integration of communication, sensing, and computation.
- Pressure to improve energy efficiency and manage network complexity.

6G research explores possible ways to address these requirements.

### 3. Potential 6G technology directions

#### 1. Terahertz (THz) communication

Very high-frequency spectrum, including candidate THz bands, may provide large bandwidths and very high peak data rates over suitable links.

**Challenge:** Such frequencies can experience high propagation loss, blockage, and limited range, so practical systems may need directional antennas and carefully designed deployments.

#### 2. Space–Air–Ground Integrated Networks (SAGIN)

SAGIN combines terrestrial networks with aerial and space-based platforms, such as drones or satellites, to extend coverage and provide additional connectivity options.

**Potential benefit:** Better service in remote areas or during some terrestrial-network disruptions.

**Challenge:** Mobility, handovers, propagation delay, cost, and coordination across different network layers.

#### 3. Joint Communication and Sensing (JCAS)

JCAS explores using radio systems for both communication and sensing. Signals and processing may help communicate data while also estimating information about the surrounding environment.

**Potential applications:** Environment awareness, localisation, and detection of objects or movement, subject to system design and regulatory constraints.

#### 4. Cell-free or distributed MIMO concepts

Instead of relying only on conventional cell boundaries, distributed access points may cooperate to serve users.

**Potential benefit:** More consistent coverage and improved interference management in suitable deployments.

**Challenge:** Coordination, transport capacity, synchronisation, and processing complexity.

#### 5. Energy efficiency

Future networks are expected to seek better energy efficiency through improved hardware, resource management, sleep modes, and more efficient use of computing and radio resources.

#### 6. Integrated AI and computing

AI and distributed computing may help manage complex networks, allocate resources, predict demand, and support applications that combine communication with computation.

### 4. Possible future applications

- Holographic or highly immersive communication.
- Extended reality (XR).
- Connected and autonomous systems.
- Robotics and industrial automation.
- Large-scale IoT and smart infrastructure.
- Connectivity across terrestrial, aerial, and satellite environments.
- Applications combining wireless communication with environmental sensing.

These are potential use cases whose feasibility depends on cost, deployment, standards, device capability, and real-world performance.

### 5. How 6G research could address limitations

| Future requirement or challenge | Potential 6G direction | Intended benefit | Important trade-off |
|---|---|---|---|
| Very high data demand | Wider spectrum, including candidate THz bands | More available bandwidth | Range and blockage challenges |
| Coverage in remote areas | SAGIN | Additional coverage paths | Cost, delay, and coordination |
| Better environmental awareness | JCAS | Communication plus sensing functions | Processing and privacy concerns |
| More consistent service | Distributed / cell-free MIMO concepts | Cooperative coverage | Coordination complexity |
| High network complexity | AI-assisted management | Better prediction and resource allocation | Data quality and reliability |
| Energy consumption | Energy-aware design and control | Lower energy per useful service | Must balance performance and coverage |

### 6. Suggested diagram

Draw a central “6G network” connected to:

- Terrestrial base stations.
- A drone or aerial platform.
- A satellite.
- Connected vehicles and IoT devices.
- An edge/cloud computing layer.

Label the concepts **THz**, **SAGIN**, **JCAS**, **distributed MIMO**, and **AI-assisted management**.

### 7. Conclusion

6G is a developing vision for future wireless systems that may combine very high data rates, broader connectivity, communication and sensing, distributed MIMO, AI-assisted operation, and improved energy efficiency. These directions could support future applications, but each has technical, economic, and deployment challenges.

**Keywords to remember:** 6G vision, THz, SAGIN, JCAS, cell-free/distributed MIMO, AI, energy efficiency, XR.

---

# Last-Minute Revision

## Module 4 — One-line recall

| Question | Core idea |
|---|---|
| Q1: LOS vs NLOS | LOS has a clear direct path; NLOS depends on indirect paths caused by reflection, diffraction, and scattering. |
| Q2: Path loss | Greater distance, frequency, and obstruction can increase path loss, lowering received power and potentially SINR. |
| Q3: Multipath fading | Delayed copies combine constructively or destructively, causing signal fluctuations and errors. |
| Q4: Noise vs interference | Noise comes from random physical/electronic sources; interference comes from unwanted transmissions. |
| Q5: Mitigation | Power control limits unnecessary transmit power; frequency planning coordinates channel reuse. |

## Module 5 — One-line recall

| Topic | Core idea |
|---|---|
| Handover | Transfers an active connection between cells or access points. |
| Roaming | Uses a visited network outside the home network's normal service area. |
| SIM | Subscriber module used for identity/security functions. |
| IMSI | Mobile subscriber identity; not the phone number. |
| Authentication | Verifies the subscription/device is authorised. |
| BTS | Cellular radio access equipment. |
| UE | User's mobile device or modem. |
| Circuit switching | Dedicated path/resources for a session. |
| Packet switching | Data sent as packets over shared resources. |
| Call flow | Request → access/security checks → service setup/routing → session → release. |

## Module 6 — One-line recall

| Question | Core idea |
|---|---|
| Q1: 5G | eMBB, URLLC, and mMTC support different smart-city and connected-system needs. |
| Q2: IoT | Sense → Connect → Process → Act. |
| Q3: Edge | Processing closer to users can lower latency and reduce backhaul traffic. |
| Q4: AI in telecom | AI supports optimisation, traffic prediction, fault detection, and predictive maintenance. |
| Q5: 6G | A developing vision involving THz, SAGIN, JCAS, distributed MIMO, AI, and energy efficiency. |

## A reliable 7-mark answer structure

For most long questions, write in this order:

1. **Definition / introduction** — 1 short paragraph.
2. **Main concept or components** — explain the important terms.
3. **Mechanism / working** — show how or why it happens.
4. **Analysis / effects** — explain the impact on signal, network, or application.
5. **Example** — use a practical case.
6. **Diagram** — draw and label a simple block diagram where relevant.
7. **Conclusion** — 1–2 sentences answering the question directly.

## Quick study plan

1. **First pass:** Read Module 4 Q1–Q5 and learn the definitions and cause-effect chains.
2. **Second pass:** Learn Module 5 short definitions and comparison tables.
3. **Third pass:** Read Module 6 Q1–Q5 and practise the diagrams.
4. **Active recall:** Close the notes and write the headings for each answer from memory.
5. **Timed practice:** Practise at least one Module 4 and one Module 6 answer without looking, then check for missing keywords and diagrams.

---

## Note on scope

These notes cover all questions listed in the uploaded IA2 question bank and the related Module 4–6 syllabus topics identified in the supplied materials. The question bank's five Module 5 short-answer topics are included, along with brief call-flow and packet-core notes because those topics appear in the syllabus. The exact assessment selection and marking scheme may vary.
