# DirectConnect

Encrypted chat with an admin-controlled server, optional internet relay, and (Pro) voice chat and file sharing.

## Download

| Platform | Download | Contents |
| --- | --- | --- |
| Windows x64 | [DirectConnect-win-0.0.4.0.7z](https://github.com/HowyF/DirectConnect/releases/download/windows-v0.0.4.0/DirectConnect-win-0.0.4.0.7z) | `DirectConnect.exe` (client), `DirectConnect-Server.exe` (server / relay) |
| Linux x64 | [DirectConnect-linux-0.0.3.1.7z](https://github.com/HowyF/DirectConnect/releases/download/linux-v0.0.3.1/DirectConnect-linux-0.0.3.1.7z) | `DirectConnect` (client), `DirectConnect-Server` (server / relay), Docker files, `README.md` |

All versions: [Releases](https://github.com/HowyF/DirectConnect/releases)

The archives are 7-Zip files. On Windows use [7-Zip](https://www.7-zip.org/); on Linux `sudo apt install 7zip` (or `p7zip-full`), then `7z x DirectConnect-linux-*.7z`.

## Connecting

Every server has its own code (`XXXX-XXXX`), created by the server app. In the client, enter the server's address as `CODE@address`:

- Through a relay: `K7Q2-M9XD@relay.example.com`
- Directly (UPnP or a forwarded port): `K7Q2-M9XD@203.0.113.5:47800`
- On your network: press **SCAN LAN**

The server app shows and copies these addresses for each server.

## Windows

Extract and run `DirectConnect.exe` to chat, or `DirectConnect-Server.exe` to host a server.
Run `DirectConnect-Server.exe --relay` for relay mode.

## Linux

Needs glibc 2.31+ (Ubuntu 20.04 or newer):

```sh
sudo apt install libgtk-3-0 libssl3 libpulse0 fonts-noto-core fonts-symbola
chmod +x DirectConnect DirectConnect-Server
./DirectConnect-Server        # or ./DirectConnect, or ./DirectConnect-Server --relay
```

On a server without a desktop (for example over SSH), run it on GTK's Broadway backend:

```sh
sudo apt install libgtk-3-bin
broadwayd --address 127.0.0.1 --port 8087 :5 &
GDK_BACKEND=broadway BROADWAY_DISPLAY=:5 ./DirectConnect-Server --relay --start
```

`--start` begins hosting immediately with the saved settings. The included `README.md` also covers running in Docker.

## Standard and Pro

Standard is free. A Pro license key unlocks voice chat and file sharing.
