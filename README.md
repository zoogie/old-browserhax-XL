# old-browserhax-XL

## Thanks 
- webkit test cases 
- MrNbaYoh for his blogs
- Yellows8 for the hbmenu loader code: https://github.com/yellows8/3ds_browserhax_common

## Intro

Old-browserhax-XL is another primary userland exploit for the old3ds browser, Spider. It's the successor to [old-browserhax](https://github.com/zoogie/old-browserhax), which was murdered by firmware 11.14. RIP.

## What's needed

An old3ds (or old2ds) on firmware:<br>
```
11.14.0-46 on regions US,EU,JP,KR,CH,TW
```

## Directions (hbmenu)
1) In the [release folder](https://github.com/zoogie/old-browserhax/releases/download/v1.0/release_old3ds_v1.0.zip) (same as old-browserhax), find your region (USA, EUROPE, JAPAN) and take all files *inside* that folder and put them on the root of your sd card. Do not copy the entire region folder over, just its contents.
2) Place the homebrew launcher boot.3dsx from [here](https://github.com/fincs/new-hbmenu/releases/tag/v2.2.0) also on the root of your sd card.
3) With wifi on and working, scan [this QR](http://api.qrserver.com/v1/create-qr-code/?color=000000&bgcolor=FFFFFF&data=https%3A%2F%2Fzoogie.github.io%2Fweb%2Fnbhax&qzone=1&margin=0&size=400x400&ecc=L) after pressing L+R should buttons together and tapping the QR button on the bottom screen. The link to the sploit page is https://zoogie.github.io/web/nbhax if you want to type it in manually and/or bookmark it.
4) Click on the "PROCEED TO HAXX" button, then press A twice to confirm two pop-ups. The exploit should then load the homebrew menu. Make sure to add homebrews to the sdmc:/3ds folder first in order to have something to run. See other guides online about what you can do with homebrew.

- Note that CH & TW regions cannot run hbmenu homebrew. Only cfw options like AGBhax are possible with these regions. This is a limitation of the *hax homebrew environment, not this exploit.

## Directions (boot9strap, aka cfw)
https://3ds.hacks.guide (coming soon, probably)

## Exploit details

A certain line of javascript moves an object from an iframe to its parent while the iframe is still being parsed. This results in a Use-After-Free crash. It's based on the webkit test case [here](https://github.com/WebKit/WebKit/blob/main/LayoutTests/fast/parser/resources/move-during-parsing-iframe.html).

## Troubleshooting (hbmenu)

- Problem: The 3ds freezes on a yellow screen.<br>
Solution: Try again. Boot rate is about 75-80%. This has always been an issue with *hax homebrew and not specific to this implementation.* If this keeps occurring over and over, it's likely being caused by running browserhax while cfw (luma3ds + boot9strap) is already installed -- don't do this! Follow https://3ds.hacks.guide for proper instructions on how to launch .3dsx homebrew under cfw. Hard freezing with regular screens (ie no solid colored screen) can also indicate running under cfw.

- Problem: The 3ds freezes on some other color screen or "An error has occured" prompt shows up.<br>
Solution: Make sure you have *all* the correct files. Check your region is correct.<br>
At minimum, make sure to have the below 3 files in the sd root as shown.<br>
```
sdmc:/arm11code.bin
sdmc:/browserhax_hblauncher_ropbin_payload.bin
sdmc:/boot.3dsx
```

- Problem: I still can't get the exploit to work and the two solutions above didn't help.<br>
Solution: Go to your browser's settings and select Clear History and Delete Cookies. Now create a bookmark with https://zoogie.github.io/web/nbhax as the address (or just edit an existing bookmark). Exit the browser, then launch it again (this saves your changes), and then finally launch that nbhax bookmark you just made. It may also be helpful to power cycle the 3ds in between attempts if the exploit is still being stubborn.


## FAQ
Q: Will this exploit be fixed in a firmware update?<br>
A: Last time I suggested about 50% odds new-browserhax being fixed which turned out to be 100% odds. So I guess that means we average those two and get a 75% chance of it being fixed this time :p<br>I really don't know.

Q: Will this work with [unSAFE_MODE](https://github.com/zoogie/unSAFE_MODE) and [AGBhax](https://github.com/TuxSH/universal-otherapp)?<br>
A: Works for me! The directions for these exploit chains are out of scope for this readme though.