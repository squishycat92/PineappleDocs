# Server Codes
This document is available in the following languages: [English](servercodes-english.md), [简体中文](placeholder), [日本語](placeholder), [Tiếng Việt](servercodes-vietnamese.md)

Pineapple offers a server code tracker for the online game [florr.io](https://florr.io) which can be useful when hunting Super mobs or finding servers to farm in. The following offers a overview of its functions.

## Servers Tracker
The primary server tracking function can be accessed with `.servers`, or `.sv` for short. The command syntax is `.servers (map)`. If you prefer to use slash commands in your server, you can also access this utility using `/servercodes servers`, or `/servers` for short. There are a few shortcuts for the different maps, outlined below:
```
g → Garden
d → Desert
o → Ocean
j → Jungle
ah → Ant Hell
h → Hel
sw → Sewers
bg → Battle Ground
all → All Servers
```
This function returns the server codes of all servers if no argument is passed, or `all` is specified. The slash command equivalent also has Discord selection options, meaning that you are not strictly limited to these shortcuts and your Discord client will do its best job to infer which map you were trying to select.

Server codes are given with their `cp6.forceServerID` command prefilled and with a copy button at the corner of the code box for easy copying. As of Pineapple v5.0.0, this code can be directly pasted into the florr.io console; it no longer contains ANSI data to color the text.

### Server Warnings
Pineapple also tracks certain attributes of servers and annotates the `cp6.forceServerID` command to include them as needed.

| Warning | Meaning |
| --- | --- |
| `CRASHED` | This server is on a version that fails to load correctly. Connecting to this server will likely fail. |
| `REVERTED` | This server is on a version that has been reverted, most likely for a bug. Connecting to this server is possible by forcing your way in. |
| `OLD` | This server is on an old version and therefore is not directly connectable. Connecting to this server is possible by forcing your way in. |
| `FULL` | This server is unconnectable. This is most likely caused by it either being full, but this can sometimes happen when 2nd servers expire and shut down. |

Warnings are displayed in the UI as a comment next to the force-server command, such as `cp6.forceServerID('code')  // OLD`. When these comments exist, there is no need for you to strip the comment from the command. The JavaScript console ignores the warning by default.

![image](https://github.com/user-attachments/assets/ebcb4c34-a507-4adf-b18f-7b3078903c14)
| Key | Meaning |
| --- | --- |
| `A` | Map (or maps) that the command is providing maps for. |
| `B` | Copy button (appears on mouseover). |
| `C` | The raw server code. |
| `D` | Force-server command (see [Forcing Servers](#forcing-servers)). |

### Forcing Servers
#### Current Servers
Current servers can be forced by executing the `cp6.forceServerID` command in the JavaScript console. You can do this in a multitude of ways, but the most common way is to use the Developer Console ([Chrome & Chromium](https://developer.chrome.com/docs/devtools/open), [Safari](https://developer.apple.com/library/archive/documentation/NetworkingInternetWeb/Conceptual/Web_Inspector_Tutorial/EnableWebInspector/EnableWebInspector.html)).

A quicker way to do this without needing to open Developer Tools is available by executing JavaScript directly in the address bar, eliminating the need to open the Console. On Chrome, simply prepend `javascript:` to the force-server command, so type `javascript:cp6.forceServerID('code')` in the address bar. This requires you to have Console access, and must **manually** type the `javascript:` part of the command (this is a [security feature](https://stackoverflow.com/questions/7698009/why-is-javascript-pseudo-protocol-stripped-from-url-bar-when-pasted) on Chrome). This is also why the bot does not give the command with `javascript:` already prepended to it.

#### Old and Reverted Servers
Forcing your way into old servers or reverted servers can be done by spamming the force-server command **while connected to the corresponding map in the new build**. This will reload your page as you are sent to a different game version, you should continue spamming the command until the `Ready` button appears. Note that after some time, old and reverted servers are closed, so usually connecting to these servers is only possible within a few minutes of a new game version being pushed. A video tutorial is attached below.

![video](https://github.com/user-attachments/assets/ea61d092-31fa-4ff0-855b-0e6eae6ee8a4)
