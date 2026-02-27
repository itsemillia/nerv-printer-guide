# Nerv Printer - Multi-User + Multiple Maps Guide

*This guide is made strictly for the Carpet Printer module, it may or may not apply to other modules in Nerv Printer.*

*Testing was concluded on 9b9t, not checked on other servers.*

Comprehensive guide to Nerv Printer and the use of Multi-User + handling multiple maps, written by Emi.

---
### Basics
For the basics, follow [this](https://github.com/Julflips/nerv-printer-addon/blob/master/Documentation/CarpetGuide.md) documentation.

### Recommended Settings

- **Lines Per Run** = 3
- **Place Range** = 4
- **Min Place Distance** = 0.8
- **Ignored Blocks** = quartz_slab
- **Place Delay** = 23
- **Start Block** = Default (All Buttons)
- **Map Fill Square Size** = 1
- **Sprint Mode** = Off
- **Activation Reset** = Unchecked
- **Rotate** = Unchecked
- **Custom Folder Path** = Checked
- **Nerv Printer Folder Path** = Occluded, see Multi-User + Handling Multiple Maps
#### Advanced Tab
- **Pre Restock Delay** = 10
- **Inventory Action Delay** = 2
- **Post Restock Delay** = 10
- **Pre Swap Delay** = 4
- **Post Swap Delay** = 4
- **Reset Chest Close Delay** = 40
- **Retry Interact Timer** = 80
- **Pos Reset Timeout** = 10
- **Checkpoint Buffer** = 0.2
- **Break Carpet Above Reset** = Checked
- **Move To Finished Folder** = Checked
- **Disable On Finished** = Checked
- **Debug Prints** = Unchecked
#### Multi User (see Multi-User + Handling Multiple Maps)

#### Error Handling
- **Log Errors** = Checked
- **Error Action** = Repair
#### Render
**All Default Settings**

### Modules Outside of Nerv Printer

#### Timer = 1.6
#### Anti Afk = Swing

---

### Explanation of The Main Settings

**Lines Per Run** defines how many lines the printer places down per run (from top to bottom of the map), values lower than 3 will result in a more stable, but slower result, values higher than 3 will result in a faster, but less reliable result, more errors may occur when using high values.

**Place Range** is pretty self explanatory, it means how far the printer can place carpets, higher values could lead to a faster result but very slightly. 

**Min Place Distance** defines how close the printer can place a carpet, measured in blocks.

**Ignored Blocks** simply means what blocks to ignore in the .nbt file.

**Place Delay** states how many ticks to wait before placing the carpets.

**Start Block** specifies which blocks are used as "starting blocks" to tell the printer to start doing its job.

**Map Fill Square Size** means how far the bot has to walk to fill the map in hand.

**Sprint Mode** defines if/and/or when to sprint or not.

**Activation Reset** determines if the bot should resume printing after a reconnect or not. Unticked = Yes, Ticked = No.

**Rotate** tells the printer to rotate your camera to comply with the Anti-Cheat.

Advanced Tab

**Pre Restock Delay** defines how many ticks to wait before taking out the items out of the chest.

**Inventory Action Delay** defines how many ticks to wait before moving stacks into inventory.

**Post Restock Delay** defines how many ticks to wait after restocking.

**Pre Swap Delay** defines how many ticks to wait before swapping to another item slot.

**Post Swap Delay** defines how many ticks to wait after swapping to another item slot.

**Reset Chest Close Delay** defines how many ticks to wait before closing the Reset Chest.

**Retry Interact Timer** defines how many ticks to wait before interacting with a chest again.

**Pos Reset Timeout** defines how many ticks to wait before moving the player, if the server changes the players position.

**Checkpoint Buffer** defines the buffer area of checkpoints, lesser values meaning a more precise path, higher values meaning a less precise path (to checkpoints).

**Break Carpet Above Reset** (undefined).

**Move To Finished Folder** defines if the .nbt file should be moved to the "finished" folder inside the nerv-printer folder.

**Disable On Finished** defines if the module should auto-disable after finishing all maps.

**Debug Prints** debugs printing.

Multi User occluded, see Multi-User + Handling Multiple Maps.

Error Handling

**Log Errors** logs errors in chat.

**Error Action** defines what the bot should do about errors.

Render occluded.

---
## Multi-User + Handling Multiple Maps

For handling multiple user accounts and multiple maps, it is ***required*** to run the instances locally, cloud based path directories could be possible, but untested and not recommended.

In order to "connect" accounts with each other, one instance must and will be the **Master**, while the other ones act as **Slaves**. Simply get all the accounts into the render distance of the **Master** account and press ***Register players in range***, following the settings mentioned later in the guide will result in the **Master** account sending a "register" message to all the **Slaves**, they then send a "accept" message to the **Master** account. You will see the accounts listed under the "Slaves" category in the module. After that is done, you have to press the start button/block and the accounts will all come to life and print in their sides. Two accounts result in a 50/50 split etc.

#### Important!
Connecting the accounts to each other is very strict, these are the settings NEEDED in order to operate the multi-user functionality (*on 9b9t*).
- **Direct Message Command** = `w`
- **Sender Prefix** = `From ` (space is required) 
- **Sender Suffix** = `: ` (space is required)
- **Chat Message Delay** = 50
- **Random Suffix Length** = 0

Handling multiple maps is also extremely strict, make sure you have these settings set, and the profile in Meteor saved.

- **Activation Reset** = Unchecked
- **Custom Folder Path** = Checked
- **Nerv Printer Folder Path** = see **Folder Path**

Activation Reset NEEDS to be unchecked to handle multiple maps, as the **Slaves** will NOT start working on the next (going from map_0 to map_1) maps if it is checked.

---

## Folder Path

The **Nerv Printer Folder Path** defines a custom path for the nerv-printer to pull config and .nbt files from, it is ***recommended*** but not required to:
- Make a folder (for the guide's purpose, let's call it `NervPrinterFolder`) **outside** of your minecraft folder, that means it isn't located where your `saves`, `mods`, `resourcepacks` are.
- Add the folder path to **Nerv Printer Folder Path** on the **Master** account, it should look like this (the drive and name may vary) `D:\Games\NervPrinterFolder`. Disable and enable the module, you should be able to see `_configs` and `_finished_maps` folders inside of `NervPrinterFolder`.
- After that is done, add the ***same*** folder path on the **Slave** accounts. 
This will allow for multiple instances (Master and Slaves) to pull aforementioned files into memory and load them in-game.

---

FAQ:

Q: Why can't I use multi user on 2 seperate computers?

A: The printer is not able to determine if a map is moved to the finished_maps folder on the Master account.

Q: I have an issue! Is there a way to ask you about it?

A: Yes, @ex.emia on discord.
