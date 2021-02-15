# PS2-Modders-ToolKit

In my own experience modding a PS2, I ran into tutorial after tutorial with crappy instructions and outdated information. Hopefully with this guide you can mod yours without spending the hours I did sifting through information and documentation.

## What you'll need

### HARDWARE

* [Recordable DVD-R](<https://www.microcenter.com/product/434201/philips-dvd-r-16x-47-gb-120-minute-disc-2-pack-zip-pouch>) - $0.99 - Just a simple recordable DVD you can buy anywhere. **MUST BE DVD, PS2 DOESN'T READ CDs (LEARNED THE HARD WAY)**
* [CD/DVD Reader/Writer](<https://www.amazon.com/External-Blingco-Protable-Notebook-Computer/dp/B072BR5VWK/ref=sr_1_16?crid=I9NZPGU0XGEJ&dchild=1&keywords=external+dvd+drive&qid=1613108803&sprefix=External+DVD+%2Caps%2C273&sr=8-16>) - $15 - My laptop had one built in but you can buy external USB ones off Amazon
* [USB 2.0/3.0/3.1 Drive (+8GB Recommended)](<https://www.amazon.com/SanDisk-Cruzer-128GB-Flash-SDCZ36-128G-B35/dp/B00TKFCYP0/ref=sr_1_3?dchild=1&keywords=USB&qid=1613108962&sr=8-3>) - $15 - Most games take up around 2-4GB so you're gonna want a lot of space
* [Playstation 2 MagicGate Memory Card](<https://www.amazon.com/gp/product/B0007DFIK2?pf_rd_r=7SQRE34PC97BKEWY40P8&pf_rd_p=5ae2c7f8-e0c6-4f35-9071-dc3240e894a8&pd_rd_r=b534c71d-a091-4173-8fca-79d4fa349d0b&pd_rd_w=sFVrT&pd_rd_wg=rzuPl&ref_=pd_gw_unk>) - $10 - Will store FMCB Config files **(recommend using MC that came w/ PS2)**

### SOFTWARE
* [USBUtil](<https://www.ps2-home.com/forum/viewtopic.php?t=1240>) - Used for writing ISOs to Flash Drive **(download v2.2 EN/SP)**
* [OPL v0.9.2](<https://www.ps2-home.com/forum/viewtopic.php?t=43>) - Software for actually running games **(download OPL 0.9.2.7z)**
* [FMCB v1.966](<https://www.ps2-home.com/forum/viewtopic.php?t=1890>) - Software for loading OPL **(download FMCB v1.966 Install (2019-04-13).7z)**
* [OPL Manager v21.7](<https://oplmanager.com/site/>) - Software for adding game art and compatibility modes to games
* [FreeDVDBoot](<https://github.com/CTurt/FreeDVDBoot/blob/master/PREBUILT%20ISOs/All%20PS2%20Slims%20-%20English%20language.iso>) - .iso to be written to DVD
* [Auslogics Disk Defrag](<https://www.auslogics.com/en/software/disk-defrag/?mode=desktop>) - Software for defragging USB Drive **(if files are fragmented games won't run)**
* [ImgBurn](<https://www.imgburn.com/index.php?act=download>) - **(optional)** I used the built-in windows feature for burning images to DVDs but in case you can't I recommend this one

## Burning FreeDVDBoot to DVD, preparing USB Flash Drive, and Installing FMCB and OPL on PS2 MagicGate Memory Card

### FreeDVDBoot - Windows Method

Insert your DVD into your DVD Drive and then go to your FreeDVDBoot iso (it should be called something like All PS2 Slims - English language.iso) and right click on it. A pop-up should appear ``` Burn iso ``` or ``` Burn to DVD ``` or something, click it. From their a window should appear, click ``` Verify after burning ``` and run. Your iso should burn to the DVD and your done!

### FreeDVDBoot - ImgBurn Method

Insert your DVD into your DVD Drive and then run ImgBurn. From there, select ``` Write Image file to disc ``` and set Source to the iso and "Destination" to your USB drive. Next, set the ``` Write Speed ``` to the slowest one your DVD allows (it should be printed on DVD) and then click on the ``` File -> Disc ``` icon to burn.

### Prepping USB Flash Drive

Insert your USB Flash drive into your computer and then right click on it in file explorer and click format. Set your capacity to the max, file system to FAT32, and allocation unit size to default, then click format. Now copy the FreeMCBoot folder to the drive and, in the OPL folder, copy the .elf file into the USB. Then eject.

### Installing FMCB and OPL on PS2

Insert the DVD into the player and the USB into the first slot (left one) and then turn the PS2 on. You should boot in a gray file explorer called ``` LaunchELF ``` and from there click on ``` mass:/ ``` and then the FMCB folder. Click on the file ``` FMCBInstaller.elf ``` to run the installer and click on ``` Install ``` (NOT multi-install).

Once FMCB is installed, restart the PS2 and you should boot into a new Menu UI. Scroll down to ``` uLaunchELF ``` and click on it, taking you back to the file explorer. This time, go to ``` mass:/ ``` and then press R1 on ``` OPL 0.9.2.ELF ``` and then ``` Copy ```. Now go to ``` mc0:/BOOT/ ``` and on ``` ../ ``` press R1 and then ``` Paste ``` to paste it. Then restart the PS2.

Once back in the menu, click on Free MCBoot Configurator and click on ``` Configure OSDSYS options... ```. Now scroll down to ``` Configure Item 1: LaunchELF ``` and press ``` -> ``` on the dpad until you get to a blank space, then press enter. Set the name to OPL and click on ``` Path1: ``` and navigate to ``` mc0:/BOOT/OPL 0.9.2.ELF ``` and press enter. Then go to return and click ``` Save CNF to MC0 ``` and then ``` Exit ```

Lastly, run OPL in the menu, go to Settings and set ``` Disable Debug Colors ``` to ``` Off ```, ``` Check USB Fragmentation ``` to ``` On ```, ``` USB device start mode ``` to ``` Auto ```, and ``` Default menu ``` to ``` USB Games ```. Then click ``` Ok ``` and go to ``` Display Settings``` and set ``` Automatic Sorting ```, ``` Automatic Refresh ```, ``` Enable Cover Art ```, and ``` Dispaly info page ``` all to ``` On ```. Then click ``` Ok ``` and then ``` Save changes ```

Then that's it! You've successfully installed FMCB v1.966 and OPL v0.9.2 to your PS2 and you can now turn it off, remove the disc (you won't need it anymore), and remove the USB (you will need this).

## Writing and Configuring PS2 games to USB with USBUtil, OPL Manager v21.7, and Auslogics Disk Defrag Tool

### Prepping USB Drive for Games

Now that we've successfully installed FMCB and OPL, format your drive once more (Max capacity, FAT32, Default Allocation) and create 2 folders in it called ``` CD ``` and ``` DVD ```.

### Writing Game ISOs with USBUtil v2.2

Now run USBUtil v2.2 and go to ``` File > Create GAME from ISO ``` and set your Source to a compatible PS2 ROM ISO and your Destination to the root of your USB Drive (F:\, D:\, etc...). Then select ``` DVD ``` for ``` Media ``` and then ``` Create ```.

### Setting OPL Compatibility with OPL Manager v21.7

Now that your game is written to the drive, run OPL Manager and set your filepath to the drive root (again F:\, D:\, etc...). From there select your game (which should already be formatted, if not it's an easy fix but I'm lazy so look it up or figure it out :) ) and click ``` Manage ARTs ``` and click the **middle icon** to import game art for the OPL menu. That's it!

### Defragging USB Drive with Auglogics Disk Defrag Tool

The last and most important step is to defrag our drive, if any files are fragmented the game won't be able to run. Unfortunately, Windows doesn't support USB Drive Defragging so we will use Auglogics.

Run Auglogics Disk Defrag, uncheck all drives, and then check your drive and click ``` Defrag ```. It should defrag and that's it, you're done! Plug the USB back into your PS2, run OPL, and your games should appear in the menu and all be playable!

## Simpler Instructions

Running Games off USB
==========================
1. write ISO to USB w/ USBUtil v2.2
2. Use OPL Manager v2.17 to optimize compatibility
3. Use Auslogics Disk Defrag to defrag USB (if fragmented game won't run)
4. eject and pop in PS2, then run OPL, press circle, and run games.

Installing FMCB & OPL
==========================
1. Burn FreeDVDBoot iso to DVD
2. Copy FMCB dir to USB
3. Copy OPL elf
4. pop DVD, USB, and MagicGate MC in and turn on
5. in eLaunchELF run FMCB installer, copy OPL elf to mc0:/BOOT/
6. in FMCB Config go to OSDSYS, add OPL option and set filepath to mc0:/BOOT/OPLfile.elf, and then click Save CNF to MC0
7. run OPL, go to settings and set 'Check USB Fragmentation' to 'On', Display settings and turn "Notifications, Cover Art, and Auto Refresh" all "On".
8. Restart PS2
9. Run OPL and run games!

## Things I Don't Recommend

1. Using an external HDD or SDD. PS2 just froze trying to read even a blank 2.5".

2. Using the SMB method. I tried crossover cables, using the router, and a whole host of different settigs for windows but couldn't get it to work. People hail this method as the fastest but I think USB works just fine.

3. Do **NOT** try to delete games off drive manually. **Don't touch the ul.cfg** file as it has very specific spaces for its syntax and delete or adding an extra one could mess up the entire registry and thus, your game data as well ( lost a good 2 hours on Shadow of the Colossus for this :( ). If you want to delete a game off the USB drive **use the delete button in OPL**, it was made for this purpose.

4. Using a small USB drive. I tried putting as many games as I could on a 14 GB GB, the last game I added was permanently fragmented and it took a re-format to fix it. Bigger drives will always be more dependable.

## Working Games

* Shadow of the Colossus
* Monter Hunter
* Resident Evil 4
* Katamari Damacy
