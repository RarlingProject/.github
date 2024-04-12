# Rarling Project
#### *An attempt at running Roblox on Darling (ROL Revival).*

### What's "Rarling"?
Rarling is a combination of the words "Roblox" and "Darling".     
- **Roblox** is an online game platform and game creation system developed by Roblox Corporation that allows users to program and play games created by themselves or other users.
- **Darling** is a free and open-source macOS compatibility layer for Linux.

### What Does This Project Aim To Solve?
As Roblox transitioned to a better Anti-Cheat implementation due to popular request and to combat cheaters on it's platform, GNU/Linux support was largely left behind.      
- [**Hyperion**](https://roblox.fandom.com/wiki/Hyperion) *also referred as Byfron* is the Anti-Cheat that would make it's Debut to Roblox's Client.     
- [Initial attempts](https://devforum.roblox.com/t/the-new-roblox-64-bit-byfron-client-forbids-wine-users-from-using-it-most-likely-unintentional/2305528) were made to restore GNU/Linux support from Roblox and for a period of time between May of 2023 and March of 2024, Roblox's Client worked almost perfectly on [Wine](https://en.wikipedia.org/wiki/Wine_(software)).     
- After first of March 2024, Wine would be [blocked again](https://devforum.roblox.com/t/why-isnt-hyperion-an-anti-cheat/2840095/33) from GNU/Linux, Essentially making it impossible to play the PC Builds of Roblox's Clients on GNU/Linux without a Virtual Machine.
- Unfortunately, it seems like this was the final nail in the coffin for playing PC Versions Roblox on GNU/Linux.    
*But there is one glimmer of hope*...   

**The Rarling Project aims to bring back Roblox Support on Linux using the macOS Builds of Roblox and Darling**

### How Would this Even Work?

While there are still a lot of stuff that needs to be implemented, Roblox's macOS Builds don't actually rely too much on macOS Exclusive libraries. The main ones (Most notably Cocoa) are actually decently implemented already.
**Here's how it would play out**:
- Since Roblox on macOS has the ability to use OpenGL, We can largely ignore implementing Metal functionality (Other than live capture).
- Roblox doesn't rely on StoryBoard *which is notoriously difficult to implement in Darling* and uses Cocoa and AppKit instead. Some functionality is missing and other parts are questionable at best.
- Hyperion on Roblox's macOS Client is more relaxed than the Windows Client. While we should still proceed with caution, this should make it much easier to find fixes for Hyperion's Anti cheat implementation.
- Most Networking stacks that Roblox requires are __already implemented__ within Darling.

### What's The Current Objective Of this Project?
There's still a long road to achieving Roblox on Linux. Here's what we will be currently doing:   
1) Iron out crashes and Segmentation faults.
2) Implement missing classes and headers (some can be stubbed)
3) Ensure that the client would run at a very basic form

## Current Status of Rarling
**Console Output**:
```sh
$ /Applications/Roblox.app/Contents/MacOS/RobloxPlayer
2024-04-13 01:06:31.685 RobloxPlayer[42:3e8] Attempting to load nibFile MainMenu
2024-04-13 01:06:31.701 RobloxPlayer[42:3e8] NSScanner: nil string argument
2024-04-13 01:06:31.874 RobloxPlayer[42:3e8] FreeType font face is not scalable
[42:42:20240413,010634.396314:ERROR xattr.cc:39] getxattr size org.chromium.crashpad.database.initialized on file /Users/RarlingProject/Library/Logs/Roblox/crashes: Operation not supported on socket (102)
[42:42:20240413,010634.399611:ERROR xattr.cc:39] getxattr size com.googlecode.crashpad.initialized on file /Users/RarlingProject/Library/Logs/Roblox/crashes: Operation not supported on socket (102)
[42:42:20240413,010634.403627:ERROR xattr.cc:64] setxattr org.chromium.crashpad.database.initialized on file /Users/RarlingProject/Library/Logs/Roblox/crashes: Operation not supported on socket (102)
libc++abi: terminating with uncaught exception of type std::runtime_error: Failed to initialize crash reporter
Abort trap: 6 (core dumped)
```

Binary details:   
1) `/Applications/Roblox.app/Contents/MacOS/RobloxPlayer`: Roblox's Player and Wrapper.
2) `/Applications/Roblox.app/Contents/MacOS/Roblox.app/Contents/MacOS/Roblox`: Roblox's Internal Client.

***Any and all contributions here would be welcome***.
