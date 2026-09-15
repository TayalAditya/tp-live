# tp-live

Where the TestPlatform on the IIT Mandi network is right now.

The Pi that runs it gets its address from DHCP and that address moves, so
this site is a fixed door: every page here forwards to the platform's
current address. Open https://tayaladitya.github.io/tp-live/ from the
campus WiFi. `/admin`, `/teacher`, `/student` and `/login` go straight to
those routes; any other path is forwarded as typed. Add `?stay` to read the
address instead of being sent on, or `?port=4010` for another service on the
same machine. `address.txt` and `address.json` hold the bare address for
scripts.

The Pi rewrites and pushes these files itself whenever its address changes.
