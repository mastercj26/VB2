<img width="1224" height="754" alt="image" src="https://github.com/user-attachments/assets/4443f323-5892-403b-9bb0-cbd5cc9622d2" />
This diagram shows the "virtual hand" in action. The DesktopManager  uses Go functions in xorg.go which, in turn, use a special feature called Cgo to talk to the lower-level C code that directly interacts with the Xorg system on the Linux server.
<img width="1462" height="929" alt="image" src="https://github.com/user-attachments/assets/bffc5030-5daf-418c-bb71-d942b3885efb" />
Key Files to Remember



    server/internal/desktop/manager.go: This is the main orchestrator for the virtual desktop. It sets up the Xorg display and starts the Xevent loop.
    server/internal/desktop/xorg.go: Contains Go functions that wrap calls to the Xorg C library for mouse, keyboard, and screen management.
    server/internal/desktop/xevent/xevent.go: Handles capturing events from the Xorg system, like clipboard updates and cursor changes, and sends them through Go channels.
    server/internal/desktop/clipboard/clipboard.go: Specific functions for reading from and writing to the virtual desktop's clipboard.
    server/internal/types/desktop.go: Defines the data structures (like ScreenSize or CursorImage) used to communicate information about the desktop.
    .docker/base/xorg.conf: This configuration file is super important. It tells the Linux system how to set up a "dummy" virtual display for our browser to run on. It defines supported resolutions and refresh rates, ensuring our Virtual-Browser has a screen even when there's no physical monitor!
