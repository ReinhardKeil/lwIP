# Network: Network Stack using Internet Protocols

## lwIP: [lwIP (Lightweight IP stack)](lwip/doc/doxygen/output/index.html)

```yml
- pack: lwIP::lwIP@2.2.0
- license: <unknown>
- keywords: TCP/IP, network, IP connectivity, ethernet   # note: these are missing in PDSC
```

**Software Components**

```yml
- component: Network:API                    # Network high-level wrapper API

- component: Network:CORE&IPv4              # Network Core (IPv4)
- component: Network:CORE&IPv4/IPv6         # Network Core (IPv4)
- component: Network:CORE&IPv4              # Network Core (IPv4)

- component: Network:RTOS&CMSIS-RTOS2       # OS abstraction layer (CMSIS-RTOS2)
- component: Network:RTOS&FreeRTOS          # OS abstraction layer (FreeRTOS)

- component: Driver:Ethernet&CMSIS Driver   # Ethernet Interface using CMSIS Ethernet Driver
- component: Driver:SIO&CMSIS Driver        # Serial I/O Interface using CMSIS USART Driver

- component: Network:Interface:Ethernet     # Network Ethernet Interface
- component: Network:Interface:PPP          # Network PPP over Serial Interface
- component: Network:Interface:SLIP         # Network SLIP Interface
```

**External Software Component Dependency:**

List of software components that are not defined in this pack

```yml
- component: CMSIS:RTOS2                    # 
  required-by:
  - component: Network:RTOS&CMSIS-RTOS2 

- component: RTOS&FreeRTOS:Core
  required-by:
  - component: Network:RTOS&FreeRTOS 

- component: CMSIS Driver:Ethernet
  required-by:
  - component: Driver:Ethernet&CMSIS Driver

- component: CMSIS Driver:Ethernet MAC
  required-by:
  - component: Driver:Ethernet&CMSIS Driver

- component: CMSIS Driver:Ethernet PHY
  required-by:
  - component: Driver:Ethernet&CMSIS Driver

- component: CMSIS Driver:USART
  required-by:
  - component: Driver:Ethernet&CMSIS Driver
```

**API Interface Header Files**

```
<none>
```
**API Interface Header Files**

```
<none>
```

**Configuration Files**

```
- file: rte/config/lwipopts.h
  for: 
  - component: Network:CORE&IPv4              # Network Core (IPv4)
  - component: Network:CORE&IPv4/IPv6         # Network Core (IPv4)
  - component: Network:CORE&IPv4              # Network Core (IPv4)

- file: ports/cmsis-driver/config/ethif_config.h
  for: 
  - component: Driver:Ethernet&CMSIS Driver

- file: ports/cmsis-driver/config/sio_config.h
  for: 
  - component: Driver:SIO&CMSIS Driver
```

**Release Notes**

```
- version: 2.2.0    # 2022-08-17
  Release of lwIP in a PACK containing lwIP Version 2.1.3.
  Updated Ethernet Driver (support hardware checksum offload)

- version: 2.1.2    # 2020-07-13
  Removed robust mutex attribute from CMSIS-RTOS2 abstraction

- version: 2.1.1    # 2020-04-22
  Updated Ethernet Driver (semaphore protection for multi-threading)

- version: 2.1.0    # 2019-12-03
  Release of lwIP in a PACK containing lwIP Version 2.1.2.
  Added support for FreeRTOS
  Enhanced lwIP components:
   - added Core variants (IPv4, IPv6, IPv4/IPv6)
   - added RTOS abstraction layer (CMSIS-RTOS2 and FreeRTOS)
   - added Ethernet Driver using CMSIS Ethernet Driver
   - added Serial I/O Driver using CMSIS USART Driver
   - updated lwIP option template file (lwipopts.h)
  Updated examples
 
- version: 2.0.0    # 2018-02-21
  Release of lwIP in a PACK containing lwIP Version 2.0.3.

- version: 1.4.1
  Initial release of lwIP in a PACK containing lwIP Version 1.4.1.
```
