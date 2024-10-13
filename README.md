# Integrated Automatic antenna tuner, internal battery with a charger and speaker for QRP Labs QMX+ transceiver

QMX+ Battery Charger and ATU Companion Board             |  QMX+ ATU Mounting Board | Back of the Companion board | All-in-One QMX+ Field minimalistic config
:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:
![](https://github.com/AC8L/QMX_Plus_Autotuner_Internal_Battery_Speaker/blob/main/Photos/IMG_1165.jpeg)  |  ![](https://github.com/AC8L/QMX_Plus_Autotuner_Internal_Battery_Speaker/blob/main/Photos/IMG_1161.jpeg)  |  ![](https://github.com/AC8L/QMX_Plus_Autotuner_Internal_Battery_Speaker/blob/main/Photos/IMG_1168.jpeg)  |  <img src="https://github.com/AC8L/QMX_Plus_Autotuner_Internal_Battery_Speaker/blob/main/Photos/IMG_1172.jpeg" width=120% height=30%>

The ATU is based on N7DDC's 7x7 ATU minituarized by Barb (WB2CBA):
https://antrak.org.tr/blog/usdx-sota-modular-all-mode-sdr-hf-transceiver-for-qrp-operations/
 
<a href="https://github.com/AC8L/QMX_Plus_Autotuner_Internal_Battery_Speaker/tree/main/ATU-100_Custom_Firmware">Custom firmware</a> was written for the ATU.
 
Battery and charger is based on my <a href="https://github.com/AC8L/PSU-for-uSDX-SOTA">previous work</a>, which in turn, is also based on Barb's <a href="https://antrak.org.tr/blog/usdx-sdr-ssb-sota-transceiver-battery-pack/
">original design.</a>

**I am releasing design materials, PCB fabrication files, and code under open source license and to be free for ham radio community to embrace and enjoy DIY building. Or commercially selling.**

<span style="color:red"
Anyone who wants to commercialize and sell this solution as modules, semi kit or as a full kit are allowed to do so under these terms:

- Commercial seller can not alter design and has to keep it in it’s original published form.

- Recognition of originators and designers AC8L and WB2CBA for their work on their site.
</span>

Because of minimum batch of 5 for the PCB order plus shipment, project is very well suited for the group build. If anyone wants to make money out of it - you have my blessings and prayers for the success!

I can only do a limited support and further development on best effort basis.

Sardar - AC8L, 4K6SA, VA3DUA.

Vienna, VA 10/13/2024

AC8L@ARRL.NET

# Build steps at a glance
1. Build <a href="http://qrp-labs.com/qmxp.html">QMX+</a> with following mods:
   - Do not solther the jumper wire on JP501 as instructed on Rev2.00 build document's page 37! The ATU will play the role of that jumper wire.
   - Make sure to solder-in the 2-row 5-pin female connector into JP501.
   - Plug in a temporary jumper wire (breadboard prototyping wire is a good choice) into the female connector at JP501 at pins corresponding to a soldered jumper wire in the instruction document's page 37.
   - Thoroghly calibrate and test the QMX+ build according to the assembly manual. Making a couple of QSO's is a good idea.
   - Remove temporary jumper wire.    
2. Build ATU with <a href="https://antrak.org.tr/blog/usdx-sota-modular-all-mode-sdr-hf-transceiver-for-qrp-operations/">instructions at the WB2CBA's page</a> with following mods:
   - Do not source and solther two BNC connectors.
   - Do not source and solther male pin connectors to the ATU board. We will use different ones for our integration.
   - Use only ATU section of the page, ignore the rest for the purpose of this project.
3. Upload <a href="https://github.com/AC8L/QMX_Plus_Autotuner_Internal_Battery_Speaker/raw/refs/heads/main/ATU-100_Custom_Firmware/atu_100_fw_3.2_QMX+.hex.zip">ATU custom firmware from this repository</a> into the PIC16F1938 and plug it to the ATU board.
4. Build <a href="QMX+_ATU_Mount_Board/QMX+_ATU_Mount_Board_Front.jpg">QMX+ ATU Mount Board</a> (install the ATU itself and QMX+ connectors to the Mount board)
5. Build <a href="QMX+_ATU_Companion_Board_THT_v1.1/QMX+_ATU_Companion_Board_Front.jpg">QMX+ ATU Companion Board.</a> Keep power (battery) switch on the OFF position until the last moment before closing the enclosure top!
6. Upload <a href="QMX_plus_ATU_Companion_Board_ATMEGA328P/QMX_plus_ATU_Companion_Board_ATMEGA328P.ino">companion board firmware</a> into ATMEGA328P chip. Use Ardiuno UNO R3 board for that.
7. Install ATMEGA328P chip into the companion board
8. Install ATU mount board with ATU into the QMX+ board.
9. Insert 18650 batteries and install ATU Companion board on top of the ATU mounting board. Make sure battery power switch is still on OFF position!
10. Insert QMX+ assembly with companion boards into its enclosure, screw-in front and back panels of the enclosure.
11. Switch ATU companion board's battery switch to the ON position.
12. Carefully insert and screw-in QMX+ enclosure's top.

# Ordering PCB's
I personally have a habit ordering PCB's from <a href="https://jlcpcb.com">JLCPCB</a> (again, I am not associated with them!). For the convenience, all 3 PCB's can be ordered in one order.
1. ATU <a href="https://antrak.org.tr/wp-content/uploads/uSDX-SOTA-ATU.zip">(link to download fabrication files is here)</a>
2. ATU Mount PCB - <a href="https://github.com/AC8L/QMX_Plus_Autotuner_Internal_Battery_Speaker/raw/refs/heads/main/QMX+_ATU_Mount_Board/QMX_Plus_ATU_Mount_Board_Fabrication_Files.zip">fabrication files for latest revison</a>
3. QMX+ Companion PCB - <a href="https://github.com/AC8L/QMX_Plus_Autotuner_Internal_Battery_Speaker/raw/refs/heads/main/QMX+_ATU_Companion_Board_THT_v1.1/QMX_Plus_ATU_Companion_Board-Fabrication_Files.zip">fabrication files for latest revison</a>

# Group build manager 
Usually in group builds it supoposed to be the responsibility of a group build manager to:
1. Order PCB's.
2. Assemble kit bags.
3. Burn Arduino bootloader and load the sketch from this repo into it.
4. Upload the ATU firmware from this repo into the PIC16F1938 microcontroller.

# Build configurations
There are various build configurations possible:
1. All inclusive - ATU, battery, speaker.
2. ATU only
3. Battery only
4. Speaker only
5. ATU and battery
6. ATU and speaker
7. Battery and speaker
- For all configurations you still will have to order both PCB's from this repositiry. Even if some portions will be left unpopulated - PCB's are mechanically and electrically interdependent on each other.  
- For configurations (3),(4) and (7) - you do not need to order the ATU.
- For any non-complete configuration you can gradually add other components later on.
- Barb (WB2CBA) has detailed instructions on the ordering process from JLCPCB at the ATU link above for both "plain" PCB's an d PCB's with SMD components populated. It will be difficuilt to add anything else to his writings.

# BOM
Discalimer: I am not associated with any supplier and do not receive any monetary or other benefit from referring to their products!
I am using USA suppliers, other regions have better suppliers for BOM sourcing.
## QMX+
 - 7xM3 Nylon screw, 6mm: http://shop.qrp-labs.com/SPAREPARTS/sparepartsqmx/hscrewm3p6
   - or from kit: https://a.co/d/bzrrWku
 - 2xM3 Nylon screw, 12mm: https://a.co/d/bzrrWku
 - 5xM3 Nylon Hex nut - from kit: https://a.co/d/bzrrWku
 - 3xM3 Nylon Hex Standoff spacer female-female, 11mm: https://a.co/d/94ycTzV
 - 2xM3 Nylon Hex Standoff spacer female-female, 15mm - from kit: https://a.co/d/bzrrWku  
 - 1xM3 Nylon Hex Standoff spacer male-female, 15mm - from kit:  https://a.co/d/bzrrWku
 - JP101 one of 2x2 4-pin double row female connector: https://a.co/d/acgPCxS
 - JP501: one of 2x5 10-pin double row female connector: https://a.co/d/iHggplQ
 - JP301: one of 1x4 4-pin single row female connector: https://a.co/d/03AtQEI
 - JP106: one of 1x3 3-pin single row female connector: https://a.co/d/5E9IhZu
   - cut 3-pin module from the strip.
## ATU
 - See https://antrak.org.tr/blog/usdx-sota-modular-all-mode-sdr-hf-transceiver-for-qrp-operations/
 - Do not source and solther two BNC connectors
 - Do not source and solther male pin connectors to the ATU board. We will use different ones for our integration. 
 - two of 8-pin single row male pin header: https://a.co/d/2SuiWnt
   - just cut two 8-pin sections from the strip.
## ATU Mounting PCB
 - J1: 1x10 pin 2.54mm Female pin Header Connector Extra Tall: https://a.co/d/21eQjdI
   - the 1x6 connector from the same kit wil be used for JP102 on a companion board BOM
 - J2: JST XH2.54 PCB mount male connector: https://a.co/d/9YMnd1q
   - The pigtail from the same kit will be used for the LED connection from the front panel.
   - Although the same part is mentioned here and for the front panel - you need to source only one item.
 - J3: 2-pin single row male pin header: https://a.co/d/2SuiWnt
 - JP102: two 1x2 pin 2.54mm Male pin Header Connector Extra Tall: https://a.co/d/2l7o6wW
   - These are sold in a bulk, you will have to cut 1x2 out of it. Effectively, we will end up having one 2x2 double row Extra Tall Connector.
   - Same strip is used for the Companion board BOM.
 - JP106: 1x3 3pin 2.54mm Male pin Header Connector Extra Tall: https://a.co/d/2l7o6wW
 - JP302: 4-pin single row male pin header: https://a.co/d/2SuiWnt 
 - JP501: 2x5 10-pin double row male pin header: https://a.co/d/dF83x28
   - cut 2x5 section from the strip.
## Companion PCB
 - U1: ATMEGA328P-PU (Digikey part ATMEGA328P-PU-ND)
   - For Digikey part you will have to burn the Arduino bootloader. Instructions: https://www.youtube.com/watch?v=AwbcOT2z69k
   - If you want to source the ATMEGA with bootloader burned: https://a.co/d/9rrcNaf
 - Y1: 16Mhz Crystal (Digikey part 3155-16M20P2/49US-ND)
 - U2: CD4066BE bilateral switch (Digikey part 296-2061-5-ND)
 - U3: LM386N-4 Operational amplifier (Digikey part 296-43960-5-ND)
 - U4 - 18650 battery holder (model 1, THT): https://a.co/d/hhQG5n8 
 - U5, U7 - 18650 battery holder (model 2, SMD): https://a.co/d/4vdH2PG
 - U8: 1xBMS battery charger/protection board https://a.co/d/gX6wQ45
   - Sometimes one vendor is unavailable, other comes in. But these parts are generally are always available. Make sure to source 3S 40A 12.6V model!
 - 3x18650 Lithium Batteries. 18650BatteryStore.com part number INR18650-25R.
   - These are original Samsung 25R 18650 2500mAh 20A Batteries. Not problematic ones from Amazon and a such.
 - D1 3mm LED (Digikey part 732-5008-ND)
   - Feel free choising different colors.
 - R1,R2: 1K THT Resistor (Digikey part 13-MFR-25FRF52-1KCT-ND)
 - R3: 10K THT Resistor (Digikey part 13-MFR-25FRF52-10KCT-ND)
 - R4: 7.5K THT resistor (Digikey part MFR-25FRF52-7K5)
 - R5: 10 Ohm THT resistor (Digikey part 10.0XBK-ND)
 - C1,C2: 22pF ceramic capacitor THT (Digikey part BC1055TR-ND) 
 - C3: 1000uF electrolytic capacitor THT (Digikey part 1189-1583-1-ND)
 - C4: 47pF ceramic capacitor THT (Digikey part BC1009TR-ND) 
 - C5,C6: 100uF electrolytic capacitors THT (Digikey part 399-6601-ND)
 - 1x28Pos DIP Socket for U1 (Digikey part A120353-ND). If you bought ATMEGA from Amazon with socket included - you do not need this.
 - 1x14Pos DIP Socket for U2 (Digikey part AE9989-ND)
 - 1x8Pos DIP Socket for U3 (Digikey part A120347-ND)
 - SW1: PCB Mount Slide Switch THT: https://a.co/d/ghhbBuE
 - J1: 1x10 pin 2.54mm Male pin Header Connector Extra Tall: https://a.co/d/2l7o6wW
   - These are sold in a bulk, you will have to cut 1x10 out of it. Do not worry, we use some for the ATU Mount PCB as well.
 - JP102: 2x3 6pin 2.54mm connector, long needles: https://a.co/d/4Ca8vJi
   - For JP102 we need 2x2 female connector. But again, I could not source one with long needes. So, I just cut two side needles leaving plastic part intact.  
 - JP106: 1x6 6pin 2.54mm Female Socket Long needle stackable header: https://a.co/d/21eQjdI
   - For JP106 we need actually 3-pin connector. However I could not source one with long needles. So, I just cut 3 pins. Leaving the plastic though intact!
 - LS1: Speaker 2W 8Ohm 36mm: https://a.co/d/bCwJI5i
 ## Front Panel
 - SW1: Generic button: https://a.co/d/eFSJQzc
 - D1: 3mm LED (Digikey part 732-5008-ND)
 - J1: JST XH2.54 pigtail with PCB mount male connector: https://a.co/d/9YMnd1q
 - 40cm of 30 AWG Kynar wire: https://a.co/d/ix2YHia
 
# Detailed Build Instructions
Can be found <a href="https://github.com/AC8L/QMX_Plus_Autotuner_Internal_Battery_Speaker/blob/main/QMX%2B_ATU_Bat_Speaker_Assembly_Instructions_v1.0.pdf">here.</a> Work is still in progress and daily edits will be committed to the repository until done.

# Some work to be done:
- Test ATU and battery charger implications into the QMX+ performance in the context of the parasitic interference
- The speaker and amplifier was a last moment addition with a brief breadbord prototyping. Schematics will definitely benefit from fine tuning.
- Implement band switching for external amps through AUX port. Utilize LPF0 to LPF5 signals from QMX+.
