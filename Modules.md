# Modules

## HandsFreeLink Unit
Honda Part Number: 39770-TL2-A110-M1  
Mfg: Johnson Controls Interiors  
Model # / FCC ID: [CB2BLUEC08](https://fcc.report/FCC-ID/CB2BLUEC08)  
Relevant FCC filing for older model: [CB2BLUEC05](https://fcc.report/FCC-ID/CB2BLUEC05)  

A single PCBA comprises the unit, with one external connector.
The PCBA houses the main MCU, the bluetooth transceiver, a DSP(?), an IEBus transceiver, and power regulation.  
### Photos
<details>
<summary>Block Diagram</summary>  
<image src="images/handsfreelink/HFL_Block_Diagram.png" alt="HFL Block Diagram">
</details>

<details>
<summary>PCBA - Top Overview</summary>  
<image src="images/handsfreelink/HFL_PCBA_Top1.bmp" alt="PCBA Top Overview">
</details>

<details>
<summary>IC - IEBus</summary>  
<image src="images/handsfreelink/HFL_IC_IEBus.bmp" alt="IEBus IC">
</details>

<details>
<summary>IC - DSP(?)</summary>  
<image src="images/handsfreelink/HFL_IC_DSP.bmp" alt="DSP IC">
</details>

<details>
<summary>IC - BlueTooth</summary>  
<image src="images/handsfreelink/HFL_IC_BT.bmp" alt="BlueTooth IC">
</details>

<details>
<summary>IC - CAN</summary>  
<image src="images/handsfreelink/HFL_IC_CAN.bmp" alt="CAN IC">
</details>

<details>
<summary>IC - DRAM</summary>  
<image src="images/handsfreelink/HFL_IC_DRAM.bmp" alt="DRAM IC">
</details>

<details>
<summary>ICs - Misc</summary>  
<image src="images/handsfreelink/HFL_ICs_Misc1.bmp" alt="Misc ICs - 1">
<image src="images/handsfreelink/HFL_ICs_Misc2.bmp" alt="Misc ICs - 2">
<image src="images/handsfreelink/HFL_ICs_Misc3.bmp" alt="Misc ICs - 3">
</details>

### Connector
Color: Grey  
Pin Count: 28  

<details>
<summary>FSM Pinout Image</summary>  
<image src="images/handsfreelink/HFL_Connector.png" alt="FSM Pinout">
</details><br>

| Pin# | Color | Description      | Pin# | Color | Description       |
|------|-------|------------------|------|-------|-------------------|
| 1    | BLK   | Ground           | 15   | WHT   | Battery Power     |
| 2    | PUR   | HFL Steering Sw  | 16   | PUR   | Accessory Power   |
| 3    | PUR   | HFL Mute         | 17   | BLU   | B-CAN Low         |
| 4    | RED   | GA-NET Bus +     | 18   | BLK   | B-CAN High        |
| 5    | GRN   | GA-NET Bus -     | 19   | GRY*  | GA-NET Bus Shield |
| 6    | WHT   | Navi Comm 4      | 20   | BLK   | Navi Comm 1       |
| 7    | RED   | Navi Comm 3      | 21   | GRN   | Navi Comm 2       |
| 8    | GRY*  | Navi Comm Shield | 22   | GRY*  | Audio Shield      |
| 9    | GRN   | Audio Right +    | 23   | WHT   | Audio Right -     |
| 10   | GRN   | Audio Left +     | 24   | RED   | Audio Left -      |
| 11   | GRN   | Telm Sig +       | 25   | RED   | Telm Sig -        |
| 12   | N/A   | Mic Sig Shield   | 26   | GRY*  | Telm Sig Shield   |
| 13   | GRN   | Mic +            | 27   | GRN   | HFL Navi Mic +    |
| 14   | WHT   | Mic -            | 28   | RED   | HFL Navi Mic -    |

### ICs
[comment]: <> (todo: move common IC to separate page?)
 - Main MCU: Renesas "SH7760 Group" HD6417760BL200ADV
	- 200MHz 32-bit RISC
	- 1x 256MBit DRAM (Offboard)
		- ISSI IS45S32800D-7TLA1 ([Datasheet](datasheets/ISSI_IS45S32800D_DRAM.pdf))
	- 1x 256MBit Flash (Offboard)
		- Spansion (Now Infineon) S99GL256NTB1 ([Closest Datasheet](datasheets/Infineon_S29GL_Flash.pdf))
	- Notable Interfaces:
		- 2x I2C 400Kbps
		- SSI (Serial Sound Interface)
		- 2x CAN 2.0B
		- USB Host (1.1)
	- [Datasheet](datasheets/Renesas_SH7760Series_MCU.pdf.pdf)
	- Notes
		- Marked as 64117760
		- Seems to be used in LOTS of Honda/Acura smart modules
 - BlueTooth Transceiver: Broadcom BCM2035MIFBG
	- Bluetooth 1.1/1.2 😔
	- PCM audio output
	- USB/UART interfaces
	- Very Old Chipset
 - IEBus Transceiver: Renesas UPD72042B
	- IEBus is used to carry GA-NET (audio control network) in this vehicle 
	- Not much "aftermarket" info is out there on IEBus or GA-NET
 - CAN Transceiver: NXP TJA1041T
	- CAN 2.0B 1MBit/sec
	- Local wake-up input

## AcuraLink Control Unit
Honda Part Number: 39820-TL2-A610-M1  
Also Marked: GEX-7807 (Pioneer internal PN?)  
Mfg: Pioneer Corporation, Made In Thailand  
Serial No Example: KHT009419US  

Two boards comprise the unit, linked by 2 FFCs.  
The "upper" board houses both external connectors, the main MCU, the XM module, and all power regulation.  
The "lower" board houses a more powerful processor with off-board RAM and flash memory.
### Photos

<details>
<summary>Upper Board - Top Overview</summary>  
<image src="images/acuralink/ALM_UpperBoard_Top1.bmp" alt="Upper Board Top Overview">
</details>

<details>
<summary>Upper Board - Bottom Overview</summary>  
<image src="images/acuralink/ALM_UpperBoard_Bot1.bmp" alt="Upper Board Bottom Overview">
</details>

<details>
<summary>Lower Board - Top Overview</summary>  
<image src="images/acuralink/ALM_LowerBoard_Top1.bmp" alt="Lower Board Top Overview">
</details>

<details>
<summary>XM Sub-Module</summary>  
<image src="images/acuralink/ALM_XMModule_Chips.bmp" alt="XM Module Chips">
</details>

### External Connectors
#### Connector A
Color: Grey  
Pin Count: 32  

<details>
<summary>FSM Pinout Image</summary>  
<image src="images/acuralink/ALM_Connector_A.png" alt="FSM Pinout">
</details><br>

| Pin# | Color | Description     | Pin# | Color | Description       |
|------|-------|-----------------|------|-------|-------------------|
| 1    | WHT   | Battery Power   | 17   | WHT   | Navi Comm 1       |
| 2    | PUR   | Accessory Power | 18   | RED   | Navi Comm 2       |
| 3    | BRN   | Ignition Power  | 19   | GRN   | Navi Comm 3       |
| 4    | N/A   | NC              | 20   | BLK   | Navi Comm 4       |
| 5    | N/A   | NC              | 21   | GRY*  | Navi Comm Shield  |
| 6    | RED   | F-CAN Low       | 22   | WHT   | HFT Comm 1        |
| 7    | WHT   | F-CAN High      | 23   | RED   | HFT Comm 2        |
| 8    | BLU   | B-CAN Low       | 24   | GRN   | HFT Comm 3        |
| 9    | PNK   | B-CAN High      | 25   | BLK   | HFT Comm 4        |
| 10   | N/A   | NC              | 26   | GRY*  | HFT Comm Shield   |
| 11   | N/A   | NC              | 27   | N/A   | NC                |
| 12   | N/A   | NC              | 28   | BLK   | Ground            |
| 13   | GRN   | Audio Right +   | 29   | GRY*  | GA-NET Bus Shield |
| 14   | WHT   | Audio Right -   | 30   | RED   | GA-NET Bus +      |
| 15   | BLK   | Audio Left +    | 31   | GRN   | GA-NET Bus -      |
| 16   | RED   | Audio Left -    | 32   | GRY*  | Audio Shield      |

<p>*= Shielded bundle, may be black or dark-gray<br>
Note: Pin2 is BRN on Sedan, PUR on Sport Wagon</p>

####  Connector B
Color: Black  
Pin Count: 2 (Coaxial)  

<details>
<summary>FSM Pinout Image</summary>  
<image src="images/acuralink/ALM_Connector_B.png" alt="FSM Pinout">
</details><br>

Pinout:
| Pin #     | Description |
|-----------|-------------|
| 1 (Inner) | Signal      |
| 2 (Outer) | Shield      |
### ICs
#### Upper Board
- Main MCU: Renesas "MC32C" M30878FJAGP
	- 32MHz 16/32-bit ARM
	- 248k RAM
	- 512k FLASH
	- Notable Interfaces:
		- 2x CAN 2.0B
	- 144-pin LQFP
	- [Datasheet](datasheets/Renesas_M32Series_MCU.pdf) (Originally named `REN_rej03b0127_32c87ds_DST_20080731.pdf`, [source](https://www.renesas.com/us/en/document/dst/m32c87-group-m32c87-m32c87a-m32c87b-datasheet?language=en))
	- Notes
		- Marked as PEG701A8 (Pioneer Electronics Group?)
		- Not seen elsewhere in Honda/Acura devices
 - GA-NET Transceiver: Renesas HA12240FP
	- IEBus actually but yeah
	- [Datasheet](datasheets/Renesas_HA12240FP.pdf)
 - XM Receiver: MAX 2141 SDARS Receiver
	- Seems identical to prior MAX2140 ([Datasheet](datasheets/Maxim_MAX2140.PDF))
#### Lower Board
 - Main MCU: Renesas "SH7760 Group" HD6417760BL200ADV
	- 200MHz 32-bit RISC
	- 2x 256MBit DRAM (Offboard)
		- Samsung K4S561632J-UC75 ([Datasheet](datasheets/Samsung_K4S56_DRAM.pdf))
	- 2x 256MBit Flash (Offboard)
		- Spansion (Now Infineon) S99GL256NTB1 ([Closest Datasheet](datasheets/Infineon_S29GL_Flash.pdf))
	- Notable Interfaces:
		- 2x I2C 400Kbps
		- SSI (Serial Sound Interface)
		- 2x CAN 2.0B
		- USB Host (1.1)
	- [Datasheet](datasheets/Renesas_SH7760Series_MCU.pdf.pdf)
	- Notes
		- Marked as 64117760
		- Seems to be used in LOTS of Honda/Acura smart modules
