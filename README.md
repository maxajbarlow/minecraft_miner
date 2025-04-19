# minecraft_miner


🛠️ What It Does
This script automates mining a checkerboard-style quarry, layer by layer. It:

Mines 2×2 vertical shafts spaced 3 blocks apart

Checks for whitelisted ores in all directions

Manages fuel, torches, and chests

Returns to surface to unload when inventory is full or out of supplies

Places torches and chests strategically

📦 Inventory Setup
Before running the script, load the turtle like this:

Slot 1: Fuel (e.g., Coal or Charcoal)

Slot 15: Chests (for drop-off at the end of each layer)

Slot 16: Torches (to prevent mob spawns)

Other slots will be used for mined blocks.

🧾 Getting Started
When you run the script, it will ask:

text
Copy
Edit
Use default 100x100x10 mine? (y/n)
Type y or yes to run a 100x100 block area with 10 layers.

Type n or no to manually define dimensions.

It will then ask for:

Number of shafts in X direction (columns)

Number of shafts in Y direction (rows)

Number of vertical layers

Each "shaft" is a 2x2 hole, and shafts are spaced 3 blocks apart.

🧭 Navigation System
The bot tracks its own x, y, z position and direction (facing):

x: East-West (left-right)

y: North-South (forward-back)

z: Vertical (up-down)

face: 0=North, 1=East, 2=South, 3=West

It uses this to navigate back to the chest when full.

🔄 Checkerboard Mining Pattern
1. Layered Digging
It digs layers from top to bottom.

Each layer is made up of rows and columns of 2x2 shafts.

2. Checkerboard Offset
On odd-numbered layers, it starts with a 3-block offset to maintain a checkerboard pattern for better coverage and visibility between shafts.

⛏️ Mining Behavior
mine2x2Shaft()
Mines a 2x2 shaft down to the current layer.

Digs forward-right, forward-left, down, and inspects all 6 directions.

Mines only whitelisted ores:

lua
Copy
Edit
["minecraft:coal_ore"]
["minecraft:iron_ore"]
["minecraft:gold_ore"]
["minecraft:diamond_ore"]
["minecraft:redstone_ore"]
["minecraft:lapis_ore"]
["minecraft:emerald_ore"]
🔦 Torch Placement
After every TORCH_SPACING steps (default: 9), the bot tries to place a torch underneath itself using Slot 16.

This helps light up the area to prevent mobs.

📝 Tip: Ensure you have enough torches to match your layer size (1 per ~9 steps).

📤 Inventory Management
Full Inventory:
When inventory is full, it returns to the chest (0,0,0), drops off all items, and resumes from the last position.

Chest Placement:
At the end of each layer, the bot places a chest (Slot 15), drops everything into it, and goes down to the next layer.

⛽ Fuel Management
Checks fuel level before every movement.

If below 100, tries to refuel from Slot 1.

If Slot 1 is empty, it will prompt the user to insert fuel.

📝 Tip: Each block moved/dug costs 1 fuel. A full 100x100x10 quarry can use thousands of fuel points—bring lots!

🔁 Resuming
If the bot needs to stop (e.g., to refuel or unload), it saves its position and resumes exactly where it left off.

⚠️ Errors and Debugging
If an error occurs (like running out of fuel, torches, or chests), the bot:

Logs its last known coordinates

Describes which shaft it was mining

Attempts to return to the chest

Example log:

yaml
Copy
Edit
❌ TURTLE FAILED!
X: 27, Y: 33, Z: 5
At shaft: Layer 4, Row 9, Col 11
🔧 Useful Functions Summary

Function	Description
refuelIfNeeded()	Checks and refuels if fuel is low
isWhitelisted(name)	Checks if a block is in the whitelist
checkAllSides()	Looks around in all directions and mines if whitelisted
returnToChest(reason)	Goes back to (0,0,0), drops inventory, refuels, resupplies
resumeFrom(position)	Returns to saved mining location
placeLayerChest()	Places chest and unloads at end of each layer
inspectAndDigIfWhitelisted()	Inspects and digs only whitelisted ores
🧠 Pro Tips
Fuel First: Keep Slot 1 stocked with Coal. Even better, mine coal ore so it auto-stocks itself.

Stack Smart: Use compact inventory (stack torches/chests).

Obstacle Handling: It will dig blocks in its way. But it won’t tunnel large open caves unless instructed.

Storage Base: Set up a chest at (0,0,0) to catch all drop-offs.

Pause and Resume: You can Ctrl+T to stop and restart the turtle later—it will auto resume if fuel/inventory issues are solved.

✅ Running Recap
sh
Copy
Edit
1. Fill Slot 1 with coal
2. Fill Slot 15 with chests
3. Fill Slot 16 with torches
4. Place turtle at quarry starting point
5. Run script
6. Follow prompts (default or custom size)
7. Let it mine!
