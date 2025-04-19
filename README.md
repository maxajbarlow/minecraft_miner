Max's Ultimate Multi-Layer Checkerboard Quarry Bot

Overview

This script is a fully automated, fuel-aware, smart mining program for the Minecraft ComputerCraft Turtle. It mines a checkerboard pattern of 2×2 shafts layer by layer, identifies valuable ores (including optional tech mod ores), manages fuel, torches, and chests, and returns to its chest to unload inventory when needed.

Features

Multi-layered 2×2 shaft quarry

Ore whitelist-based smart mining (supports modded ores)

Automated fuel management

Torch placement every few steps

Chest placement and inventory handling

Position tracking and resuming

Depth prompt for configurable starting Y level

Auto-return and resume functionality

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

Run the script.

Enter the Y coordinate to dig down to (e.g., 11 for diamond level).

When prompted:

Use default 100x100x10 mine? (y/n)

Enter y to use the default.

Enter n to specify:

X direction shafts

Y direction shafts

Number of layers

Mining Pattern

Mines a checkerboard pattern: every 3 blocks a 2×2 shaft is created

Each layer is handled one at a time, from top to bottom

Odd-numbered layers use a 3-block offset to stagger shafts for better coverage

Whitelisted Ores

Includes default vanilla ores and mod support (optional):

Vanilla:

minecraft:coal_ore
minecraft:iron_ore
minecraft:gold_ore
minecraft:diamond_ore
minecraft:redstone_ore
minecraft:lapis_ore
minecraft:emerald_ore

Modded (set to true in script to enable):

mekanism:osmium_ore
mekanism:lead_ore
mekanism:tin_ore
mekanism:uranium_ore
thermal:tin_ore
thermal:silver_ore
thermal:lead_ore
thermal:nickel_ore
create:zinc_ore
immersiveengineering:aluminum_ore

Key Functions

Function

Description

mine2x2Shaft()

Mines a 2×2 shaft and inspects all sides

checkAllSides()

Digs all 6 adjacent blocks if whitelisted

refuelIfNeeded()

Refuels automatically when low

returnToChest()

Returns to (0,0,surfaceZ) to unload and resupply

resumeFrom(pos)

Returns to last known shaft and resumes mining

placeLayerChest()

Places chest at the end of each layer

moveCoalToSlot1()

Keeps Slot 1 stocked with coal if available

startZ Prompt

Lets user define starting depth (Y coordinate)

Torch & Chest Placement

A torch is placed every 9 steps (default)

At the end of each layer, the Turtle places a chest behind itself and offloads inventory

Smart Inventory Management

Auto-drops items when inventory is full

Auto-sorts coal into fuel slot

Pauses and prompts user if out of fuel

Returns to surface (based on surfaceZ) to drop items when needed

Error Handling

If the Turtle fails (e.g., out of fuel, torches, or chests):

Logs last known coordinates

Logs shaft details

Returns to surface if possible

Example log:

❌ TURTLE FAILED!
X: 27, Y: 33, Z: 5
At shaft: Layer 4, Row 9, Col 11

Tips for Best Results

Bring LOTS of coal: each move or dig consumes fuel

Stack torches and chests efficiently

Set up a main chest at (0,0,surface) for inventory drops

Use Ctrl+T to safely stop — Turtle will resume when re-run

Adjust WHITELIST in code to enable modded ores

Example Usage

Dig down to which Y coordinate before mining?
11
Use default 100x100x10 mine? (y/n)
n
Number of shafts in X direction:
10
Number of shafts in Y direction:
10
Number of layers:
5

To-Do / Ideas for Expansion



License

MIT License. Free to use, modify, and share.

Happy Mining! ⛏️

