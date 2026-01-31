# Day 5
## Placement, FloorPlanning, Routing in Analog Layout Design
### Purpose of the Session
### Placement
During placement, circuit blocks and device instances were arranged systematically within the layout area while maintaining symmetry, alignment, and design constraints. Proper placement helps in reducing routing complexity and parasitic effects.
To protect devices from reverse current flow and substrate noise, guard rings were applied during the placement stage. Guard rings help isolate sensitive devices and prevent substrate injection, thereby improving circuit reliability.

**Steps to apply Guard Rings during Placement:**
+ Select all block > Press Q > Select only instances > OK
+ Go to Create → MPP Guard Ring
+ For P-substrate, apply P-TAP
+ For N-substrate, apply N-TAP
+ After placement, unnecessary layers or views were hidden for better clarity

### Shortcuts Used

Efficient hierarchical navigation was performed using predefined shortcut keys:
+ Hierarchy Descend in Place → X
+ Descend (Shift View) → Shift + X
+ Ascend One Level Up → Shift + B
+ Ascend Completely → Shift + C
+ to align select the block > Press A >F3 to align with user space requirements.
+ Partial Select > F4
+ R-to draw rectangle
+ F3-to copy the layout
+ to visual display options-Press E

### Floor Planning

Floor planning was carried out to define the overall structure of the layout before routing. Functional blocks were positioned to minimize interconnect length and improve signal integrity. Partial selection and rectangle-based selection were used for effective region handling. Visual display options were adjusted to enhance layout visibility and ease of editing.

### Routing

Routing was performed to create proper electrical connections between placed components using suitable metal layers. Care was taken to:

+ Avoid routing congestion
+ Maintain required spacing and width rules
+ Ensure clean and symmetric routing paths
+ Cross-coupled routing techniques were also considered for matched structures to reduce mismatch and parasitic effects.

### DRC Error Clearance

After completing routing, Design Rule Check (DRC) was executed to verify layout compliance with fabrication rules. Errors related to spacing, enclosure, and width violations were identified and corrected. Guard rings, P-TAPs, and N-TAPs were verified to ensure proper substrate isolation. Clearing all DRC errors confirmed that the layout was fabrication-ready.

### Screenshots taken during the layout design session:

<img width="1340" height="752" alt="image" src="https://github.com/user-attachments/assets/249f031c-2731-45d5-994f-ff6adf8279d3" />

<img width="1334" height="752" alt="image" src="https://github.com/user-attachments/assets/aa508345-9906-460d-a3f5-49bea5474bbe" />

<img width="1339" height="752" alt="image" src="https://github.com/user-attachments/assets/b4631377-38c5-47ae-a24f-171ba43ca191" />

<img width="1336" height="743" alt="image" src="https://github.com/user-attachments/assets/ddb7be04-e39f-4fbc-9811-ecae8a178671" />

<img width="1333" height="756" alt="image" src="https://github.com/user-attachments/assets/a463a2ed-cac1-49ec-9c8b-1cb62cc7f698" />

<img width="1338" height="749" alt="image" src="https://github.com/user-attachments/assets/6d299444-d570-49d1-9758-19deb66c7d34" />

