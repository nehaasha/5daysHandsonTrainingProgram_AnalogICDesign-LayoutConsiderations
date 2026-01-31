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
