# slimpend

Background service that enables Slim Pen 2 haptic feedback by binding to bluetooth, hidapi, and evdev.

Requires the pen to be previously paired. On IPTS devices (e.g. Surface Pro 7-10) [IPTSD](https://github.com/linux-surface/iptsd) must be running; on devices with a native HID digitizer (e.g. Surface Pro 11 with Intel) the stylus input device is detected automatically. Use `--stylus <name>` to pick a device manually.

Automatically listens for connections up/down on bluetooth and starts haptic feedback when bluetooth is detected.

## installation

Prerequisites - 

* IPTSD running
* User is in `input` group (or at least has access to IPTSD input device)
* **important** - Slim Pen 2 has been paired before

1. `cargo install --path .`
2. `mkdir -p ~/.config/systemd/user && cp slimpend.service ~/.config/systemd/user/`
3. 'export PATH="/home/jan/.cargo/bin:$PATH"' (and add the line to ~/.bashrc)
4. `systemctl --user daemon-reload`
5. `systemctl --user enable --now slimpend`
