# Max's Ultimate Multi-Layer Checkerboard Quarry Bot

## 🧽 Overview  
This script is a fully automated, fuel-aware, smart mining program for the Minecraft ComputerCraft Turtle. It mines a checkerboard pattern of 2×2 shafts layer by layer, identifies valuable ores, manages fuel, torches, and chests, and returns to its chest to unload inventory when needed.

---

## 🚀 Features  
- ✅ Multi-layered 2×2 shaft quarry  
- ⛏️ Ore whitelist-based smart mining  
- ⛽ Automated fuel management  
- 💡 Torch placement every few steps  
- 📦 Chest placement and inventory handling  
- 🧽 Position tracking and resuming  
- ♻️ Auto-return and resume functionality  

---

## 🧰 Setup Instructions  

### 🧱 Inventory Slot Configuration  

| Slot | Item              |
|------|-------------------|
| 1    | Fuel (coal)       |
| 15   | Chests            |
| 16   | Torches           |
| 2-14 | Free for mining   |

### ▶️ Starting the Bot  

1. Place the Turtle at the surface of your intended quarry.  
2. Load inventory as per above.  
3. Run the script:

   ```
   lua turtle_miner.lua
   ```

4. When prompted:

   ```
   Use default 100x100x10 mine? (y/n)
   ```

   - Enter `y` to start the default area.  
   - Enter `n` to enter custom shaft dimensions and layer count.  

---

## 🧱 Mining Pattern  

- Mines a **checkerboard pattern**: every 3 blocks a 2×2 shaft is created.  
- Each layer is handled one at a time, from top to bottom.  
- Odd-numbered layers use a 3-block offset to stagger shafts for better coverage.  

---

## 🎯 Whitelisted Ores  

Only the following ores will be mined:

```
minecraft:coal_ore  
minecraft:iron_ore  
minecraft:gold_ore  
minecraft:diamond_ore  
minecraft:redstone_ore  
minecraft:lapis_ore  
minecraft:emerald_ore  
```

---

## 🔧 Key Functions  

| Function               | Description                                          |
|------------------------|------------------------------------------------------|
| `mine2x2Shaft()`       | Mines a 2×2 shaft and inspects all sides             |
| `checkAllSides()`      | Digs all 6 adjacent blocks if whitelisted            |
| `refuelIfNeeded()`     | Refuels automatically when low                       |
| `returnToChest()`      | Returns to (0,0,0) to unload and resupply            |
| `resumeFrom(pos)`      | Returns to last known shaft and resumes mining       |
| `placeLayerChest()`    | Places chest at the end of each layer                |

---

## 🔦 Torch & Chest Placement  

- A **torch** is placed every 9 steps (default).  
- At the **end of each layer**, the Turtle places a chest behind itself and offloads inventory.  

---

## 🧠 Smart Inventory Management  

- Auto-drops items when inventory is full.  
- Auto-sorts coal into fuel slot.  
- Will pause and wait for user to insert fuel if out.  

---

## ❌ Error Handling  

If the Turtle fails (e.g., out of fuel or resources):  
- Logs **last known coordinates**  
- Logs **shaft details**  
- Returns to surface if possible  

Example log:

```
❌ TURTLE FAILED!
X: 27, Y: 33, Z: 5
At shaft: Layer 4, Row 9, Col 11
```

---

## 💡 Tips for Best Results  

- Bring LOTS of coal: each move or dig consumes fuel.  
- Stack torches and chests efficiently.  
- Set up a main chest at `(0,0,0)` for inventory drops.  
- Use `Ctrl+T` to safely stop — Turtle will resume when re-run.  

---

## 🧪 Example Usage  

```
-- Use custom size
Number of shafts in X direction:
10
Number of shafts in Y direction:
10
Number of layers:
5
```

---

## 📌 To-Do / Ideas for Expansion  

- [ ] Add blacklist support  
- [ ] Add live status display (via rednet/websocket)  
- [ ] Integrate auto-smelter chest  
- [ ] Add remote command receiver  

---

## 📜 License  

MIT License. Free to use, modify, and share.  

---

**Happy Mining!** ⛏️

