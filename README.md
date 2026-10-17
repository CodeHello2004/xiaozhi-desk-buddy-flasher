# Simple Circuits Xiaozhi TEST Web Flasher 1.3.3

This browser installer adds a country/time-zone selector to the tested breadboard firmware.
During first-time setup, the face shows scrolling instructions below the eyes and narrates each Wi-Fi configuration step through the speaker.
The three setup reminders repeat every 10 seconds until Wi-Fi configuration succeeds.
After Wi-Fi connects, the OLED shows the six-digit activation code. Open xiaozhi.me,
add a device, and enter that code to bind the newly installed desk buddy to an agent.

Upload the complete contents of this folder to one HTTPS static-site directory. Keep the
`firmware`, `manifests`, and `timezones` subdirectories unchanged. Open `index.html`
using desktop Chrome or Microsoft Edge.

The selected timezone file is a clean 16 KB NVS image containing only:

- namespace: `clock`
- key: `timezone_offset`
- type: signed 32-bit integer
- value: fixed minutes from UTC

It contains no Wi-Fi SSID or password. A new installation erases previous settings and
starts the Xiaozhi Wi-Fi setup hotspot.

A firmware installer cannot remove a binding stored in a xiaozhi.me account. Before reinstalling
an already-bound physical board, delete its old device entry in xiaozhi.me so the server will
issue a new six-digit activation code.

The offset is fixed and does not automatically follow daylight-saving transitions. Users
in regions with daylight saving should choose their current UTC offset when installing.

This package uses the TEST breadboard audio mapping. The manufactured PCB still needs a
separate pin-mapped firmware build.
