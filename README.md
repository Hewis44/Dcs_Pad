## DCS World Macropad – “Sukhoi Control Pad” by Hewis Lamilton
So yeah, I’ve been flying around in DCS World for a while now, mostly in the Su-27 and F/A-18, and it was just super annoying trying to hit 20 keyboard shortcuts every time I wanted to fire a missile, toggle flaps, or adjust trim. I got tired of fumbling keys and decided to just make my own macropad — something that feels like it belongs in a real cockpit. This whole project is my attempt to bring that control panel vibe right onto my desk, with the clickiness and smooth analog feel you only get from physical controls.

![image](https://github.com/user-attachments/assets/63e9425c-ff0c-4fce-8bdb-98e976d0ce4f)



I didn’t want to go for those premade macro boards or overpriced HOTAS setups. Instead, I designed my own PCB from scratch using EasyEDA, placed the components carefully, routed everything, added some fighter jet graphics and even stamped my name on it — “MADE BY HEWIS LAMILTON” — just for that personal flex. The board has 9 mechanical switches arranged in a 3x3 grid and 3 rotary encoders at the top for analog input like radar zoom, trims or throttle. These encoders also have push buttons, so they double as click inputs when needed.
![Screenshot 2025-07-05 112842](https://github.com/user-attachments/assets/6f11926d-800b-4775-86c3-e5b9b6284e1d)


![Screenshot 2025-07-05 112834](https://github.com/user-attachments/assets/485328e2-cc83-414f-9ae5-e2be2d53153d)



The core of the board is powered by the RP2040 microcontroller, soldered during the PCBA process done at JLCPCB. I skipped the Arduino Pro Micro this time because RP2040 is just too good — it gives more performance, is widely supported, and is future-proof. I got two boards assembled (bottom side SMT) from JLC, which means all the micro stuff and passives are already done, so now I just need to add the switches and encoders by hand. I made the board hotswappable using Kailh sockets, so I can just pop switches in and out without worrying about soldering. Makes life easy, especially if you like experimenting with switch feel.

![Screenshot 2025-07-05 113028](https://github.com/user-attachments/assets/214076bd-ea8a-4538-b12f-aaa6b9a77fe9)


![Screenshot 2025-07-05 113035](https://github.com/user-attachments/assets/463546ef-6da0-4ecf-a80e-9075225396b7)



![Screenshot 2025-07-05 113043](https://github.com/user-attachments/assets/34487366-ce58-4f5d-abe1-2668d2d040f6)




The case design was done in Fusion 360 and looks pretty sleek — all black, with curved corners and a low profile. I’ll probably 3D print it with matte black PLA or maybe even make it from leftover acrylic sheets from my old FPV drone projects. The USB port is Type-C, of course micro-USB is mid and breaks too often. And yes, I’m flashing it with QMK firmware once it arrives. Since QMK now supports RP2040, I can map each key and encoder action to whatever DCS command I want — radar lock, missile launch, you name it.



![Screenshot 2025-07-05 122949](https://github.com/user-attachments/assets/af2aa8fa-b69d-4ffc-8484-8c28ad95855a)



![Screenshot 2025-07-05 123004](https://github.com/user-attachments/assets/b2a718bd-713f-49f0-90c3-6f275a94aad9)

[ANIMATION.webm](https://github.com/user-attachments/assets/4924f250-5f39-4459-b63d-888619986233)



🧾 Detailed Bill of Materials (BOM)
Component	Description / Purchase Link	Qty	Approx. Cost (USD)	Cost (INR)
Microcontroller	RP2040 MCU (JLCPCB SMT) – Soldered during PCBA process	1	$6 (included in PCBA)	₹500
Rotary Encoders	EC11 Rotary Encoder – Robu.in – smooth 20-step with push button	3	$2.5	₹210
Mechanical Switches	Gateron G Pro 3.0 Blue – Meckeys – clicky, tactile, perfect for flight feel	9	$3	₹250
Hot-swap Sockets	Kailh Hot-Swap Sockets – Meckeys	9	$1.5	₹125
Keycaps	Grey Black PBT Keycaps – Meckeys – using numpad/extra keys from the full set	9	$4	₹335
Diodes	1N4148 Diode – Robu.in – standard for matrix scanning	10	$0.5	₹42
USB-C Port	USB-C SMT – JLCPCB SMT assembly – Included in PCBA	1	$0.6 (included)	₹50
Custom PCB (5 pcs)	JLCPCB PCB Prototype – 2-layer, black, HASL finish	5	$23.39	₹1950
PCBA (2 pcs)	JLCPCB PCBA Service – Bottom-side SMT assembly (RP2040, passives, connectors)	2	$84.95	₹7100
Shipping	DHL Express – arrives fast, decent customs handling	1	$24.34	₹2036
Case	3D Printed (Black PLA) or Laser-cut Acrylic – home job	1	$5	₹420

The total estimated cost of the entire build comes out to approximately $123.68, which in Indian rupees is roughly ₹10,600 based on a dollar rate of ₹85. This includes everything — PCB fabrication, PCBA service, components, and shipping.

Visually, it looks super clean. The PCB has black solder mask, aircraft graphics on the silkscreen, and that Sukhoi logo adds serious style. It's not just a functional tool — it actually looks like a part of the cockpit. The renders turned out mad good too, and I can already imagine how cool it’ll feel mounted next to my keyboard during a dogfight.

To be honest, this is not just a project. It’s a passion piece. Built from scratch, by hand, with desi jugaad and late-night soldering vibes. It's for those moments when you're mid-air in DCS and want a smooth, no-nonsense interface to interact with your aircraft. This macropad adds soul to the sim. 







[ANIMATION.webm](https://github.com/user-attachments/assets/f4643310-f5c0-4364-adad-6bed1c14704e)
