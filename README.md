# DirectConnect

Encrypted chat with an admin-controlled server, optional internet relay, and (Pro) voice chat and file sharing.

## Download

| Platform | Download | Contents |
| --- | --- | --- |
| Windows x64 | [DirectConnect-win-0.0.4.1.7z](https://github.com/HowyF/DirectConnect/releases/download/windows-v0.0.4.1/DirectConnect-win-0.0.4.1.7z) | `DirectConnect.exe` (client), `DirectConnect-Server.exe` (Server Host, with relay mode) |
| Linux x64 | [DirectConnect-linux-0.0.4.2.7z](https://github.com/HowyF/DirectConnect/releases/download/linux-v0.0.4.2/DirectConnect-linux-0.0.4.2.7z) | `DirectConnect` (client), `DirectConnect-Server` (Server Host), Docker files, `README.md` |

All versions: [Releases](https://github.com/HowyF/DirectConnect/releases). The current version of each build is listed in [`versions.json`](versions.json).

The archives are 7-Zip files. On Windows use [7-Zip](https://www.7-zip.org/); on Linux `sudo apt install 7zip` (or `p7zip-full`), then `7z x DirectConnect-linux-*.7z`.

## Connecting

Every server has its own code (`XXXX-XXXX`), created by the Server Host. In the client, enter the server's address as `CODE@address`:

- Directly (a VPS, UPnP or a forwarded port): `K7Q2-M9XD@203.0.113.5:47800`
- Through a relay: `K7Q2-M9XD@relay.example.com`
- On your network: press **SCAN LAN**

The Server Host shows and copies these addresses for each server.

## Windows

Extract and run `DirectConnect.exe` to chat, or `DirectConnect-Server.exe` to host servers.
The **RELAY MODE** button (or `DirectConnect-Server.exe --relay`) runs it as a relay instead.

## Linux

Needs glibc 2.31+ (Ubuntu 20.04 or newer):

```sh
sudo apt install libgtk-3-0 libssl3 libpulse0 fonts-noto-core fonts-symbola
chmod +x DirectConnect DirectConnect-Server
./DirectConnect-Server        # or ./DirectConnect for the client
```

On a server without a desktop (for example a VPS over SSH), run it on GTK's Broadway backend and open `http://localhost:8087/` through an SSH tunnel:

```sh
sudo apt install libgtk-3-bin screen
screen -dmS server bash -c '(broadwayd --address 127.0.0.1 --port 8087 :5 &) && sleep 2 && GDK_BACKEND=broadway BROADWAY_DISPLAY=:5 ./DirectConnect-Server --start; exec bash'
```

`--start` starts every server immediately with the saved settings. The included `README.md` also covers running in Docker.

## Standard and Pro

Standard is free. A Pro license key unlocks voice chat and file sharing.
