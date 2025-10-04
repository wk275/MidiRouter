
![](https://img.shields.io/badge/release-v6.1.1.8-blue)                 
![](https://img.shields.io/badge/windows-yellow)

## MidiRouter
1. Introduction
##### MidiRouter is a Windows application for MIDI and audio device management, routing, and monitoring. It features a flexible tabbed interface, allowing you to organize devices, create connections, define automation rules, and customize your MIDI/audio environment.

Release 6.1.1.2+
##### MIDI Channel Assignment is missing in MuseScore 4. I use MidiRouter to get the Instrument/Track MetaData from an exported Musescore4 .mid file and apply Logic at run time to change the Midi Channels
As from release 6.1.1.2+ Track- and Instrument info are available as fields in a Logic Condition block. Keep in mind that logic will only be executed for Rules executed in the same Media button Block!

E.G. When configuing rules for a Preset enter following parameters

| Media  Button | Command Type | Command | Midi Channels |  Out Ports | Delay |
|-----------------|-------------------|------------|------------------|------------|--------|
|Load | Logic |if Channel == 2 then {Channel = 14}<BR> (Make sure that Channel 2 is not used before assigning a new instrument to a channel) <BR>if Instrument contains Harp then {Channel = 2} <BR>if Channel == 3 then {Channel = 14}<BR> (Make sure Channel 3 is not used)<BR>if Instrument contains Flute then {Channel =3} |  | All | | 
|Load	|My Midi 	  |TestV2.mid	| All | All	|  |



Use <CTRL+ENTER> to create a new line in the Logic. Use ENTER to accept if statement.

Do not forget to setup 'My Midi' as a dynamic loaded command type
> File > Load Dynamic Commands will open a Command Form
Enter

| Target | Category | Style | CommandType | Command |
|--------|------------|------|------------------|-------------|
| My Midi |must be empty |Must be empty | Midi | "C:\Users\willy\Documenten Willy\Guitar - Keyboard\Musescore\Partituren\Musescore4" (Enter the target directory surrounded by quotes) |
> Close

After defining the Dynamic Command Type, "My Midi" will be available in the Preset Rule configuration. 
When entering the cell "Command" a popup shows the filles in the target dir defined above. Choose a .mid file and fill in other parms and close.
Back on the main page focus the preset just defined and hit the space bar. It will start playing the midi file and applies the logic.
Hitting the space bar a second time will stop the midi playback. Except if you defined multiple media buttons. Then you need to use the command type Midi-Stop to stop playback.
Logging reports the changes made by the Logic to a Midi event.

---
2. Application Layout
   <br>The main window displays a tab control where each tab can contain any combination of MIDI or audio devices.
   <br>Menu Bar: Access device management, color customization, logging, and configuration options.
   <br>Logging Window: Monitor real-time MIDI events.
   <br> Tab Management: Add, rename and delete tab
---
3. Device Management
<br>Automatic device detection: On startup, MidiRouter scans and lists available MIDI and audio devices.
<br>Manual Addition: Use the context menu on a tab page to add devices manually.
<br>Device Types: Supported types include MIDI Input, MIDI Output, Audio In, Audio Out, and Preset.

---
5. Device Operations
<br>Drag & Drop: Move devices within a tab by dragging. Snap-to-grid can be enabled for precise alignment.
<br>Copy Device: Right-click a device and select "Copy" to duplicate it to a tab.
<br>"Copy with dependencies" will also copy linked devices and rules.
<br>Rename Device: Select a device and press F2 to edit its name.
<br>Delete Device: Right-click and select "Delete" or press Delete when the device is selected.
---
6. Creating and Managing Links
<br>Create Link: Click the connector panel on a device to select it for connection. Then select another device to establish a link. If you click the connection panel on many devices of the same type and then click a device connection of another type, links will be established between all selected devices.
<br>Link Visualization: Links are drawn between devices. You can choose between straight, curved, or arrowed lines via the menu.
<br>Link Context Menu: Right-click a link label to access options such as "Remove Connection", "Define Ports", or "Set Volume" (for audio links).
<br>Customizing Link Appearance: Use the "Define Colors" menu to set link colors or enable random link colors for distinction.
---
7. Rule Editor and Dynamic Commands
<br>Accessing Rules: Right-click a Preset device and select "Define Rules" to open the rule editor.
<br>Rule Types: Automate MIDI messages, audio playback, external application launch, and more.
<br>Media Buttons: Preset devices display media buttons for quick rule execution. A media button is assigned for a unique rule action. Selecting a device and hitting the space bar will wrap around the different media buttons.
<br>Dynamic Loaded Commands: You can define recurring commands, styles, app directory, midi directory, audio directory, etc for command types ("SysEx", "CVP-Tempo", "MSB", "LSB", "PC", "CC", "MSB-LSB-PC", "NoteOn", "Logic", "Midi", "Audio", "App") using the "Load MIDI Commands" option in the menu. These commands become available for use in device preset rules as RuleCommandTypes, allowing you to extend the app’s functionality.
Dynamic commands are managed, exported and uploaded via a command editor. An example MidiRouterCommands.csv is available as part of the downloaded zip file.
---
8. Logging and Monitoring
<br>Enable Logging: Use the menu to start or stop event logging. It opens the log window to monitor MIDI and audio events in real time. Info about logic applied to an event is shown.
<br>Log Filtering: Filter log messages by keyword or skip dropped messages.
<br>Log Color Customization: Change log highlight, MIDI event, SysEx event, and audio colors via the menu.
---
9. Saving and Loading Configurations
<br>Save Setup: Use "Save" or <CTRL+s> or "Save As" to store your current configuration, including devices, links, rules, colors, dynamic commands, etc.
---
10. Advanced Features
<br>Snap to Grid: Enable or disable grid snapping for device placement from the menu.
<br>External App Integration: Rules can launch or stop external applications as part of automation.
<br>Color Customization: Set custom colors for devices, links, and logs for improved clarity.
---
11. Tips and Best Practices
<br>Use tooltips for quick device and rule information. Toggle tooltips from the menu.
<br>Use context menus for fast access to device and link actions.
<br>Regularly save your configuration to prevent data loss.
<br>Use the log window to diagnose issues and monitor system activity.
---
12. Troubleshooting
<br>Device Not Detected (device grayed out): Attach your device and use "Refresh MIDI State" to rescan devices.
<br>Connection or Rule Issues: Check the log window for error messages and details.
<br>Performance: If the application becomes slow or unresponsive, disable logging. You are probably logging a lot of midi messages. 
---
14. Support
For further assistance, consult the official documentation or log an issue on git hub.
---

## Installation
Goto the release section under About in the github main window. 
Goto assets and click on the latest reslease.
Download the app binaries and a windows setup command to install the application.
If you install a new version please delete the previous version first via windows delete installed APPs. 
