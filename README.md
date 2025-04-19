Overview

This script is a fully automated, fuel-aware, smart mining program for the Minecraft ComputerCraft Turtle. It mines a checkerboard pattern of 2x2 shafts layer by layer, identifies valuable ores, manages fuel, torches, and chests, and returns to its chest to unload inventory when needed.

Features

✅ Multi-layered 2x2 shaft quarry

⛏️ Ore whitelist-based smart mining

⛽ Automated fuel management

💡 Torch placement every few steps

📦 Chest placement and inventory handling

🧭 Position tracking and resuming

🔄 Auto-return and resume functionality

Setup Instructions

Inventory Slot Configuration

Slot

Item

1

Fuel (coal)

15

Chests

16

Torches

2-14

Free for mining

Starting the Bot

Place the Turtle at the surface of your intended quarry.

Load inventory as per above.

Run the script:

lua turtle_miner.lua

When prompted:

Use default 100x100x10 mine? (y/n)

Enter y to start the default area.

Enter n to enter custom shaft dimensions and layer count.

Mining Pattern

Mines a checkerboard pattern: every 3 blocks a 2x2 shaft is created.

Each layer is handled one at a time, from top to bottom.

Odd-numbered layers use a 3-block offset to stagger shafts.

Whitelisted Ores

Only the following ores will be mined:

minecraft:coal_ore
minecraft:iron_ore
minecraft:gold_ore
minecraft:diamond_ore
minecraft:redstone_ore
minecraft:lapis_ore
minecraft:emerald_ore

Key Functions

Function

Description

mine2x2Shaft()

Mines a 2x2 shaft and inspects all sides

checkAllSides()

Digs all 6 adjacent blocks if whitelisted

refuelIfNeeded()

Refuels automatically when low

returnToChest(reason)

Returns to (0,0,0) to unload and resupply

resumeFrom(pos)

Goes back to last known position and resumes

placeLayerChest()

Places chest and drops off inventory at the end of each layer

Torch & Chest Placement

A torch is placed every 9 blocks (default spacing).

At the end of each layer, a chest is placed behind the Turtle to store mined materials.

Smart Inventory Management

Auto-drops items when inventory is full.

Auto-sorts coal into fuel slot.

Will pause and wait for fuel if out.

Error Handling

If the Turtle fails (e.g., runs out of fuel, no chests or torches):

Logs position and shaft info

Returns to chest if possible

Waits for manual refill

Example:

❌ TURTLE FAILED!
X: 27, Y: 33, Z: 5
At shaft: Layer 4, Row 9, Col 11

Tips for Best Results

Bring LOTS of coal: Each movement/block uses fuel.

Use stacked torches and chests to save inventory space.

Set up a base chest at (0,0,0) to collect drops.

Use Ctrl+T to safely terminate. Turtle resumes if re-run.

Example Usage

-- Use custom size
Number of shafts in X direction:
10
Number of shafts in Y direction:
10
Number of layers:
5

To-Do / Ideas for Expansion



License

MIT License. Feel free to modify and share.

Happy Mining! ⛏️
