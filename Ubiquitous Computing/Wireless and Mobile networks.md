---
id: UbiComp_Wireless_Mobile_Network
aliases:
  - Wireless & Mobile Network
tags:
  - University
  - UbiComp
---

# Wireless Network

## Elements of Wireless Network
- Host (Computer, Mobile)
- Base Station (Have wired connection to wired network): Relay data to wire network infrastructure.
- Infrastructure Mode (Handoff between area)
- [~] *Wireless Link*

## Characteristic of Wireless Link

### Fading / Attenuation 
- The radio signal loses power the further it goes
- Path Loss is proportional to ```(frequency * distance)**2```

### Multipath
- The signal could reflect off object, arriving at the destination at different time.
- **Coherence Time**
    - Period of time that signal is coherent
    - Limit maximum transmission rate since coherence time can't overlap.
    - Inversely proportional to frequency and receiver's velocity

![CoherenceTime.png](CoherenceTime.png)

### Noise
- Interefence from other source
- SNR: Signal-to-noise ratio (Higher is good)
- **SNR vs BER tradeoff**
    - In physical layer: +Power -> +SNR -> -BER
    - SNR may change with mobility: adapt with physical layer (modulation, rate) (??)

### Hidden Terminals
- A problem where some terminals can't communicate with each other while intermediate terminal can.
![hidden_terminal_1.png](hidden_terminal_1.png)

- Path Loss / Attenuation also cause this problem

![hidden_terminal_2.png](hidden_terminal_2.png)

## Code division multiple access (CDMA)
- A way / protocol to communicate where multiple users which could be prone to interference(?)
- Work by assigning unique code to each user

![CDMA.png](CDMA.png)

![CDMA2.png](CDMA2.png)

## IEEE 802.11 Wireless LAN
- Use CSMA/CA (Carrier-sense multiple access /w Collsion Avoidance) to handle multiple hosts.

### CSMA/CA
- Sender:
    - transmit frames if channel has been idle for certain time (DIFS: Distributed Interframe Space) 
    - back off and wait from random amount of time try again after waiting util ACK (Acknowledge) is receivecd

- Receiver
    - if the receivecd frame is good then return ACK after waiting SIFS (Short interframe space)
    - *Need ACK due to hidden terminal problem*

- Basically, sender reserves channel for transmission.

![RTS-CTS.png](RTS-CTS.png)

### 802.11 frame addressing

| Size (byte) | Name | Remark |
|-|-|-|
|2|Frame control|-|
|2|Duration|-|
|6|Address 1|Address of receiver|
|6|Address 2|Address of sender|
|6|Address 3|Address of router|
|2|Sequence Control|-|
|6|Address 4|For adhoc mode|
|0-2312|payload|-|
|4|CRC|-|

Frame control

| Size (bits)| Name |
|-|-|
|2|Protocl version|
|2|Type (RTS, CTS, ACK, data)|
|4|Subtype|
|1|to AP|
|1|from AP|
|1|more frag|
|1|retry|
|1|power management|
|1|more data|
|1|WEP|
|1|rsvd (?)|

### Mobility within same subnet
![mobile_subnet.png](mobile_subnet.png)

### Advance capability: Rate adaptation
- Adapt transmission rate of mobile based on SNR and BER.

### Advance capability: Power management
- Node can sleep util next beacon frame and letting it know
- Beacon frame will not send anything when sleep
- Beacon frame: contain list of mobiles with AP-to-mobile frames waiting to be sent

## Bluetooth (Personal Area Network)

- Less than 10m diameter
- Is **AD HOC** (No infrastructure)
- 2.4 - 2.5 GHz radio band, up to 3 Mbps
- Consists of:
    - Master controller
    - Client devices

# Mobile / Cellular Network

- Wide-area mobile network

## Difference from wired network
- Difference wireless link
- Have user identity (SIM cards)
- User need to subscribe (business)

## 4G LTE
- LTE: Long Term Evolution

### 4G Architecture (SKIPPED)

> Not in exam baby

### 4G Planes
- Seperated into 2 planes: Control Plane, Data Plane for different tasks
    - Control Plane: Do mobility management, security & authentication.
    - Data Plane: Tunnel (basically) to outside internet.

![data_control_planes.png](data_control_planes.png)



