**Development has come to a stop. There will be no bug fixes. I recommend using this script on the tested platforms.**


Autocrack was featured on Hackaday.com! [Link](http://hackaday.com/2011/09/15/hackaday-links-september-15-2011/)

To see a video of this script in action (pre 4.0) [Youtube link](http://www.youtube.com/watch?v=gcDcAyW9JZA)

Remember that cracking a wireless network that you do not own is, in some areas, highly illegal. Please insure that you have permission from the owner of the target wireless network before using this script. thank you.

Autocrack is a script i built to demonstrate to potential clients how easily their wireless networks can be hacked in to. (But now i use autocrack to show just how unsafe using WEP is.)

I originally built a script called startaircrack to do this. Startaircrack was designed so that i can simply start the script, select the clients wireless network, and sit back chuckling to my self as his key appears on the screen. After i finished startaircrack i started to wonder how easy it could be.

Thus autocrack was born. All that is needed is to run autocrack, and it will automatically scan for your wifi card, then scan for wireless networks around you, and attack the ones it thinks it can crack.

This is really a dirty way to do this but it works very well on my Ubuntu 9.10 computer. anyone is free to use this if they like. Improve it if you like.

As time goes on, and new releases of Ubuntu comes out i will be making improvements to this script.

This has probably been done to some extent:

  * http://www.aircrack-ng.org/doku.php?id=wesside-ng
  * http://code.google.com/p/airoscript/
  * http://xkyle.com/2009/06/01/my-wireless-cracking-tool/
  * http://code.google.com/p/wepbuster/
  * http://code.google.com/p/aircrack-supplement-script/

but i am a DIY kind of person, and I learn more from building my own tools, then using someone else's.


I did not write the programs that are used to by my script. You will them find at http://www.aircrack-ng.org
This suite includes:

  * airmon-ng
  * airodump-ng
  * aireplay-ng
  * airecrack-ng
  * packetforge-ng

This script only works in Linux, and the current version has been tested under Ubuntu 9.10 - 10.04 LTS, and BackTrack 3/4/5 and unconfirmed reports that it works under [ArchLinux](http://www.archlinux.org/)


autocrack Usage:

Run the script from the terminal.

  * ./autocrack.sh
without any arguments it will scan for your wireless card, then scan wireless networks, then attack all WEP networks in range.

  * ./autocrack.sh auto
with "auto" as the only argument it will repeat it self, intermittently checking its current target's single strength. if out of range it will moved on to the next one in the list.

  * ./autocrack voice
with "voice" as the only argument it will start and use the TTS program Festival. It wil vocalize key outputs so without looking at the screen you can get a basic idea of what is going on.

  * ./autocrack.sh auto voice
with "auto" and "voice" as the only two arguments, it will combine both "auto" and "voice" features listed above.

  * ./autocrack.sh locate
with "locate" as the only argument it will search though the folders in it's current folder looking for files that contain a list of MAC address, then it will connect to SkyHook's database and approximate the network's location. Completely optional, and requires an active internet connection.

  * ./autocrack.sh eth0
with the name of your wireless card as the only argument it will use that card instead of scanning for a card.

  * ./autocrack.sh eth0 auto
with the name of your wireless card and auto as the only two arguments it will use that card instead of scanning for a card, and keep repeating it's self.

  * ./autocrack.sh cleanup
with "cleanup" as the only argument it will clean up the temp files it uses in the current directory.

  * ./autocrack.sh cleanupmon
with "cleanupmon" as the only argument it will clean up the temp files it uses in the current directory, and remove the temporary wifi cards used by airmon-ng.

  * ./autocrack.sh listhacked
with "listhacked" as the only argument it will compile a list of wireless networks it has hacked so far by going though the folders in the current directory.

there are some other arguments that you can invoke but those are experimental.

startaircrack Usage:

Run the script from the terminal.

  * ./startaircrack.sh
without any arguments it will automatically detect your wifi card, scan the wireless networks around, and list all WEP networks for the user to choose.

  * ./startaircrack.sh NETGEAR
with the name of the target wireless network as the only argument it will automatically detect your wifi card, then scan for that SSID, gather the mac and channel from airodump-ng then launch an attack against that network.

  * ./startaircrack.sh 00:00:00:00:00 1 NETGEAR
with the MAC, channel and SSID as the only 3 arguments, it will automatically detect your wifi card, then launch an attack against that network.

  * ./startaircrack.sh 00:00:00:00:00 1 NETGEAR mon0
with the MAC, channel, SSID and wireless card as the only 4 arguments, it will not automatically detect your wifi card, using the one specified instead, then launch an attack against that network. Most commonly invoked by autocrack.