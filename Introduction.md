#Description of Bindings and Macros

## Introduction ##

The linux-g13-driver allows a user to bind any key on their G13 keyboard to any key on their normal keyboard.  This is called the passthrough mode.  The driver also allows a user to bind a G13 key to a macro.

A macro is a set of key sequences and delays.  The UI allows the capture of keys to create macros.  Once a macro is created, it can be bound to a G13 key.  Optionally, the macro can auto-repeat as long as the G13 key is held down.

These key bindings (G13 keys to normal keyboard keys or macros) are saved in a configuration file which is called bindings.  There are 4 bindings files.  A bindings file is loaded into the driver by selecting one of the 4 keys right below the LCD screen on the G13 Gamepad.

All bindings and macro definitions are saved under your home directory in ./g13 ($home/.g13).  The bindings and macros are created the first time the Java UI is executed.

In most cases a user will never have to modify a bindings or macro file by hand.  The java user interface should provide the functionality needed.

If the user's configuration files become corrupt or unusable, the user can delete their configuration directory (~/.g13) and then restart the java user interface.  This will reconstruct the default bindings and macro files.


---

## Bindings Definition ##

In ~/.g13 you can find your bindings files.  The file names contain the binding mapping to the G13 gamepad key mapping.  The leftmost bindings key on the G13 keyboard loads bindings-0.properties (B0 key on image below).  The second from the left loads bindings-1.properties(B1 key on image below) and so forth.


---

## Default Bindings ##
![http://i51.tinypic.com/1zgq9tv.jpg](http://i51.tinypic.com/1zgq9tv.jpg)


---

## Binding Files Definition ##

Binding files (bindings-0.properties, bindings-1.properties, etc) are property files with key/value pairing.  Any line that starts with # is a comment line and is ignored by the driver.

### Color ###
The color key defines the LCD color.  The value for this is an rgb value separated by commas.

ie: ` color=r,b,g ` where r/b/g are a value between 0 and 255

The Gxx keys define the gamepad key.  Please note that these keys have a numeric value of 1 less than what is on the G13 gamepad (because computers start at 0 and humans start at 1).  The value of these keys is either passthrough or macro.

### Passthrough ###
Passthrough is defined as p followed by the k.linux\_keycode

ie: G0=p,k.3

This line defines the G1 key on the gamepad to be a passthrough with keycode 3 (which is the "1" on the keyboard).  Linux keycodes are defined below.

### Macro ###
Macro is defined by m followed by macro\_id followed by repeat\_flag

ie: G1=m,12,1

This line defines the G2 key on the gamepad to be assigned to macro #12 and repeat while the key is pressed (1 for repeat, 0 for one time per key down).


---

## Macro Files Definition ##

Macro files (macro-id.properties) are property files with key/value pairing.  Any line that starts with # is a comment line and is ignored by the driver.

Up to 200 macros (and files) can be defined and used by the driver and UI.

### Name ###
The name key defines the name of the macro shown on the UI.

ie: name=My Macro

The above line defines the name of the macro.

### Id ###
The id key defines the id of the macro.

ie: id=2

The above line defines that this macro id is 2.  The file that it's saved in must contain the same id.  If the id is 2, than the file name must be macro-2.properties

### Sequence ###
The sequence key defines the sequence of events that take place in the macro.  There are 3 types of events: key down (kd), key up (ku) and delay (d).

Each of the events are followed by a period (.) and then the corresponding value of the event.  In the case of key down and key up events, an event code occurs.  In the case of delay events a time in milliseconds occurs.

ie: sequence=kd.29,d.395,kd.12,d.82,ku.12,d.365,ku.29

The above line defines a sequence of: L\_CTRL Key Down, delay of 395 ms (0.395 seconds), MINUS Key down, delay of 82 ms, MINUS key up, delay of 365 ms, L\_CTRL Key Up.


---

## Key Codes ##

|**Linux Keycode**|**Name**|**Java Keycode**|**Java Location**|
|:----------------|:-------|:---------------|:----------------|
|0                |        | | |
|1                |ESC     |KeyEvent.VK\_Escape|                 |
|2                |1       |KeyEvent.VK\_1  |                 |
|3                |2       |KeyEvent.VK\_2  |                 |
|4                |3       |KeyEvent.VK\_3  |                 |
|5                |4       |KeyEvent.VK\_4  |                 |
|6                |5       |KeyEvent.VK\_5  |                 |
|7                |6       |KeyEvent.VK\_6  |                 |
|8                |7       |KeyEvent.VK\_7  |                 |
|9                |8       |KeyEvent.VK\_8  |                 |
|10               |9       |KeyEvent.VK\_9  |                 |
|11               |0       |KeyEvent.VK\_0  |                 |
|12               |-       |KeyEvent.VK\_Minus|                 |
|13               |=       |KeyEvent.VK\_Equals|                 |
|14               |Backspace|KeyEvent.VK\_Backspace|                 |
|15               |Tab     |KeyEvent.VK\_Tab|                 |
|16               |Q       |KeyEvent.VK\_Q  |                 |
|17               |W       |KeyEvent.VK\_W  |                 |
|18               |E       |KeyEvent.VK\_E  |                 |
|19               |R       |KeyEvent.VK\_R  |                 |
|20               |T       |KeyEvent.VK\_T  |                 |
|21               |Y       |KeyEvent.VK\_Y  |                 |
|22               |U       |KeyEvent.VK\_U  |                 |
|23               |I       |KeyEvent.VK\_I  |                 |
|24               |O       |KeyEvent.VK\_O  |                 |
|25               |P       |KeyEvent.VK\_P  |                 |
|26               |[       |KeyEvent.VK\_Left Brace|                 |
|27               |]       |KeyEvent.VK\_Right Brace|                 |
|28               |Enter   |KeyEvent.VK\_Enter|                 |
|29               |L CTRL  |KeyEvent.VK\_Ctrl|KeyEvent.KEY\_LOCATION\_LEFT|
|30               |A       |KeyEvent.VK\_A  |                 |
|31               |S       |KeyEvent.VK\_S  |                 |
|32               |D       |KeyEvent.VK\_D  |                 |
|33               |F       |KeyEvent.VK\_F  |                 |
|34               |G       |KeyEvent.VK\_G  |                 |
|35               |H       |KeyEvent.VK\_H  |                 |
|36               |J       |KeyEvent.VK\_J  |                 |
|37               |K       |KeyEvent.VK\_K  |                 |
|38               |L       |KeyEvent.VK\_L  |                 |
|39               |;       |KeyEvent.VK\_Semicolon|                 |
|40               |'       |KeyEvent.VK\_Quote|                 |
|41               |`       |KeyEvent.VK\_Back Quote|                 |
|42               |L Shift |KeyEvent.VK\_Shift|KeyEvent.KEY\_LOCATION\_LEFT|
|43               |\       |KeyEvent.VK\_Back Slash|                 |
|44               |Z       |KeyEvent.VK\_Z  |                 |
|45               |X       |KeyEvent.VK\_X  |                 |
|46               |C       |KeyEvent.VK\_C  |                 |
|47               |V       |KeyEvent.VK\_V  |                 |
|48               |B       |KeyEvent.VK\_B  |                 |
|49               |N       |KeyEvent.VK\_N  |                 |
|50               |M       |KeyEvent.VK\_M  |                 |
|51               |,       |KeyEvent.VK\_Comma|                 |
|52               |.       |KeyEvent.VK\_Period|                 |
|53               |/       |KeyEvent.VK\_Slash|                 |
|54               |R Shift |KeyEvent.VK\_Shift|KeyEvent.KEY\_LOCATION\_RIGHT|
|55               |NumPad |KeyEvent.VK\_NumPad |                 |
|56               |L Alt   |KeyEvent.VK\_Alt|KeyEvent.KEY\_LOCATION\_LEFT|
|57               |Space   |KeyEvent.VK\_Space|                 |
|58               |Cap Lock|KeyEvent.VK\_Caps Lock|                 |
|59               |F1      |KeyEvent.VK\_F1 |                 |
|60               |F2      |KeyEvent.VK\_F2 |                 |
|61               |F3      |KeyEvent.VK\_F3 |                 |
|62               |F4      |KeyEvent.VK\_F4 |                 |
|63               |F5      |KeyEvent.VK\_F5 |                 |
|64               |F6      |KeyEvent.VK\_F6 |                 |
|65               |F7      |KeyEvent.VK\_F7 |                 |
|66               |F8      |KeyEvent.VK\_F8 |                 |
|67               |F9      |KeyEvent.VK\_F9 |                 |
|68               |F10     |KeyEvent.VK\_F10|                 |
|69               |Num Lock|KeyEvent.VK\_Num Lock|                 |
|70               |Scroll Lock|KeyEvent.VK\_Scroll Lock|                 |
|71               |NumPad 7|KeyEvent.VK\_NumPad-7|                 |
|72               |NumPad 8|KeyEvent.VK\_NumPad-8|                 |
|73               |NumPad 9|KeyEvent.VK\_NumPad-9|                 |
|74               |NumPad -|KeyEvent.VK\_Minus|                 |
|75               |NumPad 4|KeyEvent.VK\_NumPad-4|                 |
|76               |NumPad 5|KeyEvent.VK\_NumPad-5|                 |
|77               |NumPad 6|KeyEvent.VK\_NumPad-6|                 |
|78               |NumPad +|KeyEvent.VK\_Plus|                 |
|79               |NumPad 1|KeyEvent.VK\_NumPad-1|                 |
|80               |NumPad 2|KeyEvent.VK\_NumPad-2|                 |
|81               |NumPad 3|KeyEvent.VK\_NumPad-3|                 |
|82               |Numpad Ins|KeyEvent.VK\_Insert|                 |
|83               |Numpad Del|KeyEvent.VK\_Delete|                 |
|84               |        | | |
|85               |        | | |
|86               |        | | |
|87               |F11     |KeyEvent.VK\_F11|                 |
|88               |F12     |KeyEvent.VK\_F12|                 |
|89               |F13     |KeyEvent.VK\_F13|                 |
|90               |F14     |KeyEvent.VK\_F14|                 |
|91               |F15     |KeyEvent.VK\_F15|                 |
|92               |F16     |KeyEvent.VK\_F16|                 |
|93               |F17     |KeyEvent.VK\_F17|                 |
|94               |F18     |KeyEvent.VK\_F18|                 |
|95               |F19     |KeyEvent.VK\_F19|                 |
|96               |R Enter |KeyEvent.VK\_Enter|KeyEvent.KEY\_LOCATION\_NUMPAD|
|97               |R Ctrl  |KeyEvent.VK\_Ctrl|KeyEvent.KEY\_LOCATION\_RIGHT|
|98               |/       |KeyEvent.VK\_Slash|KeyEvent.KEY\_LOCATION\_NUMPAD|
|99               |PRT SCR |KeyEvent.VK\_Print Screen|                 |
|100              |R ALT   |KeyEvent.VK\_Alt|KeyEvent.KEY\_LOCATION\_RIGHT|
|101              |        | | |
|102              |Home    |KeyEvent.VK\_Home|                 |
|103              |Up      |KeyEvent.VK\_Up |                 |
|104              |PgUp    |KeyEvent.VK\_Page Up|                 |
|105              |Left    |KeyEvent.VK\_Left|                 |
|106              |Right   |KeyEvent.VK\_Right|                 |
|107              |End     |KeyEvent.VK\_End|                 |
|108              |Down    |KeyEvent.VK\_Down|                 |
|109              |PgDn    |KeyEvent.VK\_Page Down|                 |
|110              |Insert  |KeyEvent.VK\_Insert|                 |
|111              |Del     |KeyEvent.VK\_Delete|                 |
|112              |        | | |
|113              |        | | |
|114              |        | | |
|115              |        | | |
|116              |        | | |
|117              |        | | |
|118              |        | | |
|119              |Pause   |KeyEvent.VK\_Pause|                 |