# Getting IP Address of Zebra RFID Reader

> You'll need a grid-os device with `rfid` edge module.

1. Setup zebra scanner using this instructions: https://www.zebra.com/content/dam/zebra_new_ia/en-us/manuals/rfid/fx9600-qrg-en.pdf

2. Connect antenna

3. Connect to ethernet

4. Open the setup ui

5. Make sure the version is 3.10, if not, install update from here: https://www.zebra.com/content/dam/zebra_new_ia/en-us/software/operating-system/fx7500-series-operating-system/FXSERIES-3.10.30.ZIP

6. Unzip locally

7. In the ui open `firmware update` > `from local files`

8. Select all files from unpacked folder, press `update`

9. When logging in the ui should ask for a new password and whether it should enable https

10. Enter new password

11. Enable https

12. Find `Communication` > `Zebra IoT Connector` item in main menu, like here: Introduction — Zebra IoT Connector  documentation 

13. If not present try a different browser or try cleaning the cache

14. Setup `http post` endpoint

15. Enter http://<grid-os-device-ip-address>:3001/zebra as url and press `add endpoint`

16. Select this endpoint in `tag data interface`

17. Enable `local rest management` and `local rest control`

18. Open Communication > Zebra IoT Connector > Connection and press `connect`

19. Enter reader ip address in rfid module settings

20. Watch the leds on the reader

    - First led will blink green for 10 seconds once grid-os is connected to it and started reading the tags
    - Second led will glow red if the reader is unable to export data to grid-os
    - Third led will blink green when a tag is detected (every second)
    - Fourth led will glow green when the reader is powered on

