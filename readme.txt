
======================================================================================================
## iCHAT v3.1 - open source MysticBBS IRC client 2021-2022
======================================================================================================

https://github.com/opicron/mysticbbs-irc

For questions, private channels or operator status contact me:

    TheForze BBS:
	bbs.opicron.eu:23
	bbs.opicron.eu:22

    Netmail [opicron]:
	fsxnet 21:3/126
	araknet 10:104/4


======================================================================================================
## Changelog
======================================================================================================

v3.1
- [FIX] empty chat prompt caused error

v2.20
- [!!!] NEW CONFIG FILE REQUIRED (lots of config changes)
- [ADD] SSL support
- [ADD] check user on kick/part/quit/join/ban
- [FIX] removed pushover
- [FIX] part channel/quit app in correctly
- [FIX] reworked away status poll, no more flood kicks
- [ADD] remember joined channels
- [ADD] easily switch between joined channels
- [ADD] ZNC support (server pass, autojoins)
- [FIX] user name tab code cleanup
- [FIX] tab completion
- [ADD] remember user name when writing /R reply privmsgs

v2.15
- [ADD] /NAMES command to toggle name tab
- [FIX] dont draw footer if nametab too long
- [FIX] show correct localtime in pagers
- [ADD] option to poll away status of users (set to False by default to prevent flood kick)
        enable this option on irc channel with +/- 10 users to show live away status
v2.14
- [FIX] make sysop name for pager configurable
- [FIX] remove trailing slash from pager notify
v2.13
- [FIX] properly flush data (thanks CJ)
- [FIX] empty keypress bug
- [FIX] unable to use other servers than [0] or [1]
- [FIX] /SERVER X command
v2.12
- [FIX] two incorrect color conversions
- [FIX] crash when incorrect irc code is received
v2.11
* thanks to GngrDr3dM4n and 0zZ *
- [FIX] when changing topic modt is shown
- [FIX] crash on other iChat clients when converting MCI > IRC colors
- [FIX] edge case crash on reading buffer size from socket
v2.1
- [ADD] increase text prompt to 128 chars
- [ADD] hide cursor during redraws
- [ADD] move through text prompt left/right
- [ADD] tab to complete names (rotates on last found)
- [ADD] config options
- [ADD] /r to reply to last private msg
- [ADD]	save private user name while using /r to avoid send to incorrect recipient
- [ADD] convert MCI colors to IRC colors
- [ADD] codepage translations to ASCII
- [ADD] draw prompt MCI codes on buffer scroll
- [FIX] prompt draw improved and optimized for speed and functionality (MCI colors)
- [FIX] use server defined channel names
- [FIX] match user name capitalization on sending private message
v2.01
- [FIX] change ansi file to 23 rows to avoid scroll
- [FIX] avoid redraw on each keypress
- [FIX] add carriage return on chat key draw
v2.0
- [!!!] FULL REINSTALL REQUIRED (major ANSI and CFG changes)
- [ADD] prefix erroneous nicknames with underscore
- [FIX] restore color after underscore in nicknames
- [FIX] channels with one user would crash namelist -d0h-
- [ADD] proper user name list poll
- [ADD] channel switching
- [FIX] further improve text prompt
v1.9
- [ADD] use default values in case configuration is incorrect
- [ADD] option to auto set capitol letter in text prompt
- [FIX] improve text prompt
v1.8a
- [FIX] extended keys capture
v1.7
- [ADD] scroll chat logs with arrows
- [ADD] scroll irc logs with page-up / page-down
- [ADD] automatic name and away status collection
- [ADD] improve error logging (trace)
- [FIX] further improve cpu utilization in threads
- [FIX] some small bugs and optimizations
v1.6
- [FIX] optimize redraw of chat and name tab
- [FIX] avoid overlap chat over name tab (avoids redraws)
- [FIX] occasional wrong fg/bg color on split lines 
v1.5
- Refactor main listen thread
- [ADD] toggle channel users tab
- [ADD] keep track of away status
- [FIX] high cpu usage fixed
- [FIX] improved chat line splits
v1.4
- [ADD] Check irc nickname allready used, change nickname if in use
- [FIX] Change timeout on connect to server, move timeout to main listen loop
- [FIX] Significantly reduce CPU load by adding small timeout to chat thread
v1.3
- [FIX] Add check to pushover calls
v1.2
- [FIX] Make pushover optional because of required python libraries
v1.1
- [ADD] error reporting in threads
- [FIX] pager did not have delay between ticks
v1.0
- Initial release


======================================================================================================
## Installation
======================================================================================================

important: 
	edit your config.py.sample file and rename it to config.py in the /scripts/irc/ directory.

(OPTIONAL FOR PAGING FUNCTIONALITY) 
	edit .pushover.sample file and rename it to .pushover in /scripts/irc/

#Copy files
------------------------------------------------------------------------------------------------------
Copy irc.mpy to your /script/ folder

Copy contents of /irc/ to the correct mystic theme /script/irc/ folder

Rename config.py.sample to config.py in /scripts/irc/

(optional)Rename .pushover.sample to .pushover in /scripts/irc/

(optional)if you want to used the pager module enable "enable_pushover = True" in config**

Add python script command to mystic menu configuration settings: Execute 'irc'


**python needs [Request] module for paging functionality


======================================================================================================
## Configuration
======================================================================================================

#iCHAT config file
------------------------------------------------------------------------------------------------------
Edit the renamed config.py in your /scripts/irc/ directory and adjust the settings as you prefer.

#Pushover config file
------------------------------------------------------------------------------------------------------
(OPTIONAL) If you wish to use pushover to receive paging notifications on various devices edit 
the renamed .pushover in /scripts/irc and fill in the correct information.



======================================================================================================
## IRC commands
======================================================================================================

/MSG [username]
------------------------------------------------------------------------------------------------------
Send private message to [username] in chat

/R [text]
------------------------------------------------------------------------------------------------------
Respond to last private message

/KICK [username]
------------------------------------------------------------------------------------------------------
Kick [username] from channel (if you are operator or half operator). Request operator status for 
channels on my board or through netmail.

/TOPIC [the new topic text]
------------------------------------------------------------------------------------------------------
Change the channel topic 

/ME [action text]
------------------------------------------------------------------------------------------------------
Display action in chat. Example "/ME dances" will output: "Username dances" in the action color.

/AWAY [reason]
------------------------------------------------------------------------------------------------------
Set AFK status. Reason is optional.

/BACK			Back from away
------------------------------------------------------------------------------------------------------
Return from AFK

/QUIT or /Q
------------------------------------------------------------------------------------------------------
Exit chat


**more to be included (any requests?)



======================================================================================================
## OPTIONAL PYTHON Parameters / Arguments
======================================================================================================

/SERVER 
------------------------------------------------------------------------------------------------------
iCHAT will by connect to the default configured server. By default this is the InterBBS #Trivia channel. 
If you wish to force iCHAT to use another server and/or channel use the /SERVER argument and set the 
ID (number) of the predefined irc server, channel and optional password in the configuration file.

For example:
	/SERVER 0
	/SERVER 1
	/SERVER 12


/PAGER
------------------------------------------------------------------------------------------------------
** (OPTIONAL)
** BEFORE USING PAGER FUNCTIONALITY BE SURE TO REQUEST AN PRIVATE CHANNEL, OR SET UP AN PRIVATE 
** CHANNEL ON YOUR OWN IRC SERVER. WITHOUT AN PASSWORD PROTECTED PRIVATE CHANNEL YOU COULD BE 
** IMPERSONATED. DO NOT USE PUBLIC CHANNELS!

By default iCHAT will to connect to the default channel without showing a pager. To open the sysop
pager before entering the private channel use the /PAGER argument.

The pager will page you through an pushover message on your iphone. Pushover is a free server which 
makes it possible to send texts to various devices. iCHAT sends an server and channel text your phone
which opens the default irc client on your phone. To read more about Pushover check the following
website: https://pushover.net/

When the sysop (you) responds in the irc channel the iCHAT pager will notice the response and open the 
channel for the user to chat. This is matched on sysop name, so again be sure to ONLY do this in a 
private channel!

If iCHAT detects that the sysop (you) leaves the channel or sets an away status the chat will close 
for the user. Closing the chat on sysop leaving will only happen when in /PAGER mode of course.

to request unlogged(!) private channel contact me..

    TheForze BBS:
	    bbs.opicron.eu:23
	    bbs.opicron.eu:22

    Netmail [opicron]:
            fsxnet 21:3/126
	    araknet 10:104/4


======================================================================================================
## Keys
======================================================================================================

#Chat
------------------------------------------------------------------------------------------------------
ESC 			Exit
ENTER 			Send message
CTRL-S 			Show irc raw data in background of chat (kludge style)
CTRL-N 			Show or hide name tab
CTRL-Z			Show help
Up / Down		Look up chatbuffer
PageUp / PageDown	Browse through IRC buffer
Home / End		Start / End of IRC buffer


======================================================================================================
## Greetings
======================================================================================================

#in no particular order
------------------------------------------------------------------------------------------------------
The Godfather, Paulie420, Xqtr, g00r00, Smooth, 0Zz, GngrDreadMan

Thank you all for encouraging me to continue this mod =)

L8er
oP!
