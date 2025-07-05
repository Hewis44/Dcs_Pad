---
Title: "custom RP2040 Macropad"
Author: "Hewis44"
Description: "Everyone using xiao , imma make my own rp2040"
created_at: "2025-07-01"
Total time spent: 
---




## July 1 – Idea , PCB , Design (7 hours)

This whole thing sparked late one night after a long DCS sortie where I totally missed deploying flares because my fingers got tangled on the keyboard. That was the final straw. I kept thinking — how sick would it be to have a small dedicated control panel, with actual mechanical switches and encoders, that feels like a real cockpit module? Not those readymade gaming keypads, but something I could build, tune, and proudly say “I made this.” So yeah, mission initiated.



![image](https://github.com/user-attachments/assets/856a1228-17d5-416b-bc5b-002234eff6d0)


Started sketching out layout ideas. Wanted it to be compact  something that fits in one hand but still gives you control over essentials like radar, ECM, flaps, trim, weapon select etc. I settled on 9 switches in a 3x3 matrix and 3 rotary encoders up top. The encoders are for zooming, camera view, and trimming. Honestly, this layout hit that sweet spot  balanced and flight-friendly.




![image](https://github.com/user-attachments/assets/a6b5eb6f-a398-4489-aa75-3fdbf9f6fb37)







For the brain, I instantly chose the RP2040. Bro, Pro Micro is outdated now RP2040 has more GPIOs, handles USB-C better, and it works with QMK now. I dropped the footprint into EasyEDA, added decoupling caps (100nF), a 12MHz crystal with 15pF caps, and proper filtering on power rails. I also added an external W25Q128 QSPI flash chip — you need this on RP2040 since it has no internal storage.



![image](https://github.com/user-attachments/assets/784d6ae8-07e9-420e-962c-b483fed9fb97)



This yt bro guided me to make the microcontroller PCB



![image](https://github.com/user-attachments/assets/5c0b3f5e-7fc2-4036-ba82-e31ff79c0a03)





![image](https://github.com/user-attachments/assets/794cde7f-f96a-441d-9021-e07d1c7a65c0)





![image](https://github.com/user-attachments/assets/ce2c0b6d-180e-4502-a85c-2b9154a89219)


Bro made a macropad exactly like i wanted imma start making based on his schematic and his yt tutorial


![image](https://github.com/user-attachments/assets/97cf4fd8-924f-4901-ad09-546e8028b539)






The USB-C part was fun to figure out. Added ESD protection diodes, 5.1k resistors on CC lines, and used a linear LM3940 regulator to step 5V to 3.3V. I threw in a Power LED with a 1kΩ resistor for vibes — gotta see something glow when you plug it in na?

By the end of the day, I had a working schematic. RP2040, crystal, USB-C, flash, power, decoupling  everything sorted. I felt good about the foundation. The plan was locked, and my PCB journey had officially begun.






## July 2 – matrix,encoders and routing Chaos (8.5-10 hours)



Woke up with pure dev energy. Had chai, threw on some Lofi beats, and jumped into circuit finalization. Today’s mission: build the matrix logic, add the rotary encoders, and somehow route all this chaos into a neat two-layer PCB. Little did I know I’d be crying over vias by the end.


![image](https://github.com/user-attachments/assets/5882c191-9cdb-489a-9353-596860d95146)




Started with the key matrix 3 rows, 3 columns. Every key sits between a row and a column with a 1N4148 diode to prevent ghosting. Pretty standard stuff. Each line connects to the RP2040 directly. I gave rows 0Ω resistors just in case I wanna break them out externally later. The column lines I routed through the bottom layer  space saver.



![image](https://github.com/user-attachments/assets/be526d96-63af-46a1-86ef-83c17eaab5a3)




Next came the encoders. I used those classic EC11-type rotary encoders. Each one gives two outputs (A/B) for direction and a push button in the middle. For debounce, I added 10k pull-up resistors and 10nF filter caps to GND. The encoder lines eat up a lot of GPIOs — six for A/B, and three more for switch presses  but RP2040 had enough to spare.





![image](https://github.com/user-attachments/assets/7fce29c6-e042-4a4a-ab9d-a5647f27dc24)




Then I added the WS2812 LEDs for some cockpit underglow. These take 5V and expect a strong digital signal. RP2040 outputs 3.3V, so I added a SN74LVC1G17 buffer to step it up. DIN goes in, and the first LED gets clean 5V logic. Each LED also has a 100nF ceramic cap close by for stability.



![image](https://github.com/user-attachments/assets/a3b05a63-00b8-4792-aacd-39565e860d69)






The routing part was MAD. With switch matrix, encoder lines, power rails, LED tracks  my board looked like spaghetti at one point. Had to slow down, push traces around manually, and optimize for minimum vias. I used wider traces for power lines, threw down GND planes on both layers, and added mounting holes for a future case AS HELPED BY ROBERT THE PCB GUY ON YT. 





![image](https://github.com/user-attachments/assets/888f8223-c6cb-46d9-8524-194564b79975)








ADDED SILKSCREEN OBVIOUSLY




Ended the day mentally drained but proud  my PCB was ready to order.








## July 3 – BOM Breakdown, Firmware Work & Case Prep (4.5 hours)



![image](https://github.com/user-attachments/assets/62b95393-5b42-4619-a2aa-86fc53221b6a)




Today was more chill but still packed with essential stuff. First thing I did was sit and finalize the Bill of Materials (BOM). I hit up neomacro.in and Amazon.in, comparing prices and matching part numbers. Found a 72-pack of Gateron Blue switches on Amazon for around ₹5,300 — used 9 for this build, so ₹663 went into the BOM. The Kailh hot-swap sockets were on neomacro for ₹450. The rotary encoders I grabbed from Robu.in for about ₹210 each. Diodes and resistors came from my local box of components.





![image](https://github.com/user-attachments/assets/2b05f3b4-bd71-48d9-9796-1fa74e75dc8e)




Next, I went to JLCPCB via neomacro and uploaded the Gerbers. Ordered 5 PCBs (black soldermask, HASL finish), and also did PCBA for 2 boards with RP2040, USB-C, flash, all passives soldered. Saved me a ton of time — hand soldering QFN chips is hell. Total JLC cost with shipping came around ₹9,050. Shipping alone was ₹2,036 but worth it for DHL  I want this thing before the weekend, not next month.


![image](https://github.com/user-attachments/assets/f819b825-41dd-45c2-983b-3cf7ab8f79c4)


![image](https://github.com/user-attachments/assets/72dda394-f42b-4410-8e57-f5a382dcb3c7)

![image](https://github.com/user-attachments/assets/5740f5d0-2d4d-4e78-bed3-cdbc34490f55)

![image](https://github.com/user-attachments/assets/d8bb0830-28ff-4c5d-b194-49da9483cfd0)

![image](https://github.com/user-attachments/assets/6dc7fcd5-1109-4240-b538-d2e5cdb2eb27)


Then I opened Fusion 360 and designed the outer shell. Simple box-type case with cutouts for USB, encoders, and key caps. Added screw posts, snapped dimensions tight, and left some room for a future acrylic top panel. Planning to 3D print it in black PLA.


i ALSO TRIED ANIMATIONS( VERY BAD)

![image](https://github.com/user-attachments/assets/ebb0cae8-cbda-45b4-9333-88d15f3cd007)

[ANIMATION.webm](https://github.com/user-attachments/assets/8ee8b1c9-feb6-40c3-911c-d5dce06c1714)


I HOPE THIS GETS APPROVED AND IT WILL GET ME MORE POINTS SO THAT I CAN COME TO UNDERCITY :)

























































































