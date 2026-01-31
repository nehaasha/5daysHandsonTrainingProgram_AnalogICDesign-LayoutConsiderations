# Day 4
## Overview of Semiconductor Fabrication and Analog Layout Design
### Purpose of the session:
In this session, we learned about semiconductor fabrication techniques, doping processes, and IC manufacturing steps. We also gained an understanding of the analog layout flow, the different process technologies involved, partial layout design, and the layout patterns used in IC design.
### Semiconductor Fabrication Basics:
Semiconductor fabrication is the process of manufacturing integrated circuits by forming electronic devices such as NMOS and PMOS transistors on a silicon wafer using a sequence of controlled physical and chemical steps. In CMOS technology, both NMOS and PMOS transistors are fabricated on the same substrate to achieve low power consumption and high noise immunity.
### NMOS and PMOS Structure Overview:
An NMOS transistor is fabricated on a p-type silicon substrate, where n⁺ regions form the source and drain. A thin oxide layer separates the substrate from the polysilicon gate, which controls channel formation.
A PMOS transistor is fabricated on an n-type well, with p⁺ source and drain regions. Similar to NMOS, the polysilicon gate controls carrier flow through the channel. The complementary arrangement of NMOS and PMOS forms the basis of CMOS circuits.
**Key Steps in CMOS Fabrication Process**
1. Wafer Preparation and Oxidation
+ The fabrication process begins with a high-purity silicon wafer. A thin layer of silicon dioxide (SiO₂) is grown on the wafer surface using thermal oxidation. This oxide layer acts as an insulator and provides electrical isolation.
2. Photolithography
+ Photolithography is used to transfer geometric patterns onto the wafer. A photoresist material is applied, exposed to ultraviolet light through a mask, and developed to define specific regions for further processing.
3. Ion Implantation and Doping
+ Dopants are introduced into selected regions of the wafer using ion implantation. This step modifies the electrical properties of silicon by creating n-type or p-type regions required for source, drain, and well formation.
4. Deposition and Etching
+ Thin films of materials such as polysilicon and metal are deposited using chemical or physical deposition techniques. Etching processes remove unwanted material to form precise device structures.
5. Contacts and Metallization
+ Contact holes are etched through insulating layers, and metal layers are deposited to create electrical connections between devices. Metallization forms interconnects that link transistors to build complete circuits.
6. Testing and Packaging
+ After fabrication, the wafer undergoes electrical testing to identify functional dies. The good dies are then packaged to protect the circuit and provide external connections.
  
### Cross Section of CMOS (NMOS and PMOS):

<img width="2048" height="1157" alt="Image" src="https://github.com/user-attachments/assets/c11486f7-28a0-4887-a3f1-5bc31083b533" />

The cross-sectional view of a CMOS device illustrates the physical structure and layer arrangement of NMOS and PMOS transistors fabricated on a silicon substrate. CMOS technology integrates both transistor types on a single chip to achieve low power consumption and high performance.

**NMOS Cross-Section Explanation**
The NMOS transistor is fabricated on a p-type silicon (p-Si) substrate or p-well region. The source and drain regions are formed by n⁺ doped areas within the p-type substrate. A thin gate oxide layer separates the silicon substrate from the polysilicon gate, which controls channel formation between the source and drain.
Above the polysilicon gate, interlayer dielectric (oxide) is deposited for insulation. Metal contacts (M1, M2) are used to connect the gate, source, and drain to higher metal routing layers. The shallow trench isolation (STI/STA) regions electrically isolate the NMOS from neighboring devices, preventing leakage and latch-up.

**PMOS Cross-Section Explanation**
The PMOS transistor is fabricated inside an n-well region formed within the p-type silicon substrate. The source and drain are created using p⁺ doped regions inside the n-well. Similar to NMOS, the PMOS gate consists of a polysilicon layer separated from the silicon by a thin gate oxide.
A p-type guard ring is provided around the PMOS device to suppress noise coupling and latch-up effects. Metal layers (M1 and M2) form vertical and horizontal interconnections, enabling signal routing across the chip. Shallow trench isolation is also used to electrically isolate the PMOS transistor from surrounding structures.

**Metal and Interconnect Layers**
The CMOS cross-section shows multiple metal layers (M1, M2) separated by dielectric layers. These metal layers provide interconnections between devices, allowing complex circuit implementation. Vias connect different metal layers vertically.

### Step-by-step CMOS Fabrication Process (Layer by Layer):
Fabricating a MOSFET is a layered, sequential process, starting from a bare silicon wafer. Here’s the simplified flow:
1. Start with Silicon Wafer
+ Pure p-type silicon (for NMOS) or n-type (for PMOS).
+ Acts as the substrate.
2. Well Formation (n-well or p-well)
+ For CMOS, PMOS devices are built in n-well, NMOS in p-type substrate.
+ Done using ion implantation or diffusion.
3. Field Oxide for Isolation
+ Two techniques exist to isolate devices:
+ LOCOS (LOCal Oxidation of Silicon)
+ STI (Shallow Trench Isolation)
+ This prevents current leakage between transistors.
4. Gate Oxide Layer
+ A thin SiO₂ layer grown thermally on the wafer.
+ Serves as the insulating layer between gate and channel.
5. Gate Polysilicon Deposition
+ Polysilicon is deposited and patterned to form the gate electrode.
6. Source/Drain Formation
+ N+ regions for NMOS, P+ regions for PMOS.
+ Achieved using ion implantation.
+ Lightly doped drain (LDD) may be added to reduce hot carrier effects.
7. Sidewall Spacer Formation
+ Small oxide or nitride spacers added on the sides of the gate.
+ Helps with self-aligned source/drain implantation.
8. Metal Contacts
+ Openings etched in oxide layers to connect source, drain, and gate to metal.
9. Metal Layers (M1, M2…)
### LOCOS v/s STI 
(a) LOCOS – LOCal Oxidation of Silicon
Process:
+ Grow thin pad oxide on silicon.
+ Deposit nitride mask where devices will remain.
+ Oxidize exposed silicon → thick field oxide forms.
+ Remove nitride mask.
+ Pros: Simple and established.
+ Cons: Bird’s beak effect → wastes space, not suitable for high-density ICs.

(b) STI – Shallow Trench Isolation
+ Process:
+ Etch shallow trenches between devices.
+ Fill trenches with oxide.
+ Planarize surface (CMP).
+ Pros: Minimizes area loss, sharper edges, suitable for high-density ICs.+ Cons: Slightly more complex than LOCOS.

**Why STI is better:**
+ Less lateral encroachment → smaller cell size → higher integration.
+ Better for modern CMOS nodes (< 0.18 μm).
+ Reduces leakage current between transistors.
+ Metals deposited and patterned to form interconnections between transistors.
10. Passivation Layer
+ A protective oxide or nitride layer is deposited to protect the device.

<img width="1280" height="703" alt="Image" src="https://github.com/user-attachments/assets/d13f149f-d962-450e-ab32-10730cc2a7fa" />

### Analog Layout Flow:

1. Design Specifications
+ Define requirements like gain, bandwidth, power, noise, supply voltage, area, and technology node.
+ This is the target the design must meet.
2. Schematic Design (Symbol Creation)
+ Create the circuit schematic using transistors, resistors, capacitors, etc.
+ Generate symbols for reuse in higher-level designs.
3. Pre-layout Simulation
+ Simulate the schematic (DC, AC, transient, noise, etc.).
+ Ideal connections → no layout parasitics yet.
4. Did spec meet? (Decision)
+ NO: Modify schematic → resimulate.
+ YES: Proceed to layout.
5. Layout Design
+ Convert the schematic into a physical layout (placing and routing devices).
+ Follow matching, symmetry, shielding, and analog layout rules.
6. Physical Verification (DRC & LVS)
+ DRC (Design Rule Check): Ensures layout follows fabrication rules.
+ LVS (Layout vs Schematic): Confirms layout matches the schematic.
7. Parasitic Extraction
+ Extract real-world parasitics (resistance, capacitance) from the layout.
+ Creates an extracted netlist.
8. Post-layout Simulation
+ Simulate again using extracted parasitics.
+ Results are more realistic than pre-layout simulations.
9. Did spec meet? (Final Decision)
+ NO: Go back to layout or schematic and fix issues.
+ YES: Finalize the design.
10. GDSII
+ Generate the final GDSII file.
+ This is sent to the foundry for chip fabrication.
<img width="1500" height="869" alt="Image" src="https://github.com/user-attachments/assets/1cff6e42-285c-4423-81e3-160dab3c89ef" />

### FloorPlanning:

<img width="1220" height="694" alt="Image" src="https://github.com/user-attachments/assets/2ab02c5f-ad77-4433-bd24-621ec2a27d2a" />

Floorplanning is the initial step of analog layout where the chip area is divided into functional blocks and their relative positions are decided.

**Core ideas:**
+ Analog circuits are sensitive to noise, so they must be isolated from noisy digital circuits.
+ Bias circuits should be placed close to analog blocks to ensure stable voltage/current delivery.
+ Power distribution must be uniform to avoid voltage drops and mismatch.
+ Proper block aspect ratio helps in easier routing and better matching.

### Device Placement Strategies

<img width="1087" height="665" alt="Image" src="https://github.com/user-attachments/assets/6509fce2-16d6-49f4-b737-10d706a6c6a0" />

Device placement determines how transistors are positioned inside each block.

**Key concepts:**
+ Relative placement is more important than absolute position.
+ Matched devices must be placed close and symmetrically to experience identical conditions.
+ Critical devices (input pairs, current mirrors) are placed first.
+ Dummy devices are added at edges to protect real devices from edge effects.
+ Device orientation (rotation and mirroring) is chosen carefully to maintain matching.

### Matching & Layout Techniques:

<img width="1271" height="636" alt="Image" src="https://github.com/user-attachments/assets/bae18a63-33dd-4dd9-b498-76de11bfd649" />
<img width="250" height="205" alt="Image" src="https://github.com/user-attachments/assets/828e79f2-f912-4781-8e8a-306763375373" />
Matching is crucial in analog circuits like differential pairs and current mirrors.

Common techniques:
**Common-Centroid Layout**
+ Devices are arranged around a central point.
+ Cancels linear process and temperature gradients.
+ Used when high precision is required.
**Interdigitation**
+ Devices are split into smaller units and interleaved.
+ Ensures all devices see the same environment.
+ Useful when space is limited but matching is needed.
**Dummy Devices**
+ Non-functional devices placed at array boundaries.
+ Protect active devices from lithography and edge effects.

### Fingers vs Multipliers:

<img width="1266" height="630" alt="Image" src="https://github.com/user-attachments/assets/8ed5b835-76eb-46a7-8c75-b288212593bd" />

These are two methods to realize a required transistor size.

**Fingering**
+ A single transistor is divided into multiple parallel gate fingers.
+ Reduces parasitic resistance.
+ Improves current distribution and matching.
+ Preferred for high-performance analog circuits.
**Multipliers**
+ Multiple identical transistors connected in parallel.
+ Easier to implement but introduces higher parasitics.
+ Suitable for less critical applications.
**Comparison:**
+ Both achieve the same effective area.
+ Fingering gives lower on-resistance and better performance.
+ Multipliers may increase resistance and mismatch.
### Introduction to Analog Layout Design
Steps to Use Cadence for Layout Design:
1. Launching Layout
+ Go to Launch → Layout XL.
+ For a new layout, click New; for an existing layout, select Existing and choose Automatic.
+ Click OK, then select Generate All from Source and enable PR Boundary.
2. Block Alignment
+ Right-click near the Cadence toolbar name, go to Toolbar, and enable Align.
+ Group the blocks, then click Align Top.
+ Again go to Create → Group, and use Align Vertical for proper alignment.
3. Running DRC
+ Go to Assura → Technology, click the three dots, navigate to Install → Foundry → Analog → 45nm_REV, and select assura_tech.lib, then click OK.
+ Set the technology to GPDK045_AV, configure the switches, apply the changes, and run DRC.
+ To get the scale Click K.


<img width="1345" height="769" alt="Image" src="https://github.com/user-attachments/assets/a987320f-0077-43bd-ac32-fa7c119cbc87" />

<img width="1344" height="703" alt="Image" src="https://github.com/user-attachments/assets/916511af-3a8f-43cb-839a-de7c0795a99c" />

<img width="1340" height="744" alt="image" src="https://github.com/user-attachments/assets/4fb4f6f6-dc87-4b20-81f5-88cb7692c8e6" />

<img width="1339" height="760" alt="image" src="https://github.com/user-attachments/assets/dbf41eb4-974e-4a7a-9feb-d8b04ecc40b2" />

<img width="1291" height="751" alt="image" src="https://github.com/user-attachments/assets/deabe1b5-a458-491a-b844-d41e13debf31" />

<img width="1337" height="747" alt="image" src="https://github.com/user-attachments/assets/c0ed8c6e-7a6a-4c07-89e8-6e3632877352" />

### Conclusion:
Day 4 provided a comprehensive understanding of semiconductor fabrication and analog layout design, bridging the gap between device physics and physical IC implementation. The session covered CMOS fabrication steps from wafer preparation to metallization, along with detailed insights into NMOS and PMOS structures and isolation techniques such as LOCOS and STI, highlighting why STI is preferred in modern technologies. Additionally, the analog layout flow was explained clearly, emphasizing the importance of pre- and post-layout simulations, parasitic extraction, and physical verification (DRC & LVS). Concepts like floorplanning, device placement, matching techniques, and fingering vs multipliers reinforced the need for precision and symmetry in analog design. Overall, the session strengthened the understanding of how careful fabrication and layout practices directly impact circuit performance, reliability, and manufacturability.


