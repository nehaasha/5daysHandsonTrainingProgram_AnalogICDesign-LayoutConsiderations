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
