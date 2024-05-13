# Modules

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
