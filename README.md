# AllStar Transceiver for Android

**Version 1.1**  
**WT / App Authentication · Direct IAX2 / IAXRpt · Node Mode**  
**Android 12+ · ARM64 (arm64-v8a)**

[Android GitHub releases](https://github.com/TerryClaiborne/AllStarWebTransceiver-Android/releases) · [Windows app on Microsoft Store](https://apps.microsoft.com/detail/9nk9jn5kcq1d?hl=en-US&gl=US)

<a href="screenshots/android-main.png"><img src="screenshots/android-main.png" alt="AllStar Transceiver on Android" width="350"></a>

AllStar Transceiver connects your Android phone to the AllStarLink amateur radio network. It includes Favorites, node/callsign lookup, Connected Nodes, PTT, VOX, audio controls, Activity messages, and background/screen-off session support.

## Download and install

Get the APK only from the [official GitHub Releases page](https://github.com/TerryClaiborne/AllStarWebTransceiver-Android/releases). Download **`AllStarTransceiver-Android.apk`** from the v1.1 release.

1. Download the APK from the official release.
2. Verify its SHA-256 using the **Verify the APK SHA-256** instructions below. Compare it with the checksum published for **that exact APK**.
3. Open the APK from Downloads. If asked, allow installation from your browser or file manager. Review any Play Protect warning before proceeding.
4. Follow the installation prompts, then open **AllStar Transceiver**.

**Already have an earlier APK (v1.0 or v1.1)? Install this APK over it — do not uninstall the existing app first.** An uninstall can erase Favorites, settings, saved profiles, and AndroidKeyStore-protected remembered passwords. A normal update requires the same package identity and signing certificate.

The Android app is distributed through GitHub, **not Google Play**. A network connection and microphone permission are needed. Some networks restrict the UDP/IAX traffic used for AllStar connections.

## Choose the right connection mode

| Mode | Identity | Password or secret |
|---|---|---|
| **WT / AA** | Your AllStarLink Portal callsign | Your **AllStarLink website password** |
| **IAX2** | The destination node's authorized IAX username | That node's **IAX secret** |
| **NM** | **Register As:** an AllStar node you own | That node's **AllStarLink Node Password** |

**The three passwords are different and are not interchangeable.**

### WT — App Authentication (AA)

WT now uses **AllStarLink App Authentication** with your usual callsign and website password. A fresh, one-time-use token is requested for each connection. There is **no separate AA password** and no need to configure a Direct IAX login or Node Mode identity.

1. Open **Settings → Web Transceiver Account**.
2. Enter your callsign, website password, and matching password confirmation.
3. Choose **Remember Credentials** if desired, then tap **Save**.
4. On the main screen select **WT**, enter the **Destination Node**, and tap **Connect**.

AppAuth changes **how WT authenticates**, not how you talk to other nodes.

### IAX2 — Direct IAX2 / IAXRpt

Use this when a node operator provides an IAX username and secret. An IAX login is associated with its **specific destination node**; you may save multiple profiles.

1. Open **Settings → Direct IAX2 / IAXRpt → Add Direct IAX Login**.
2. Enter the destination node, IAX username (often `iaxrpt`), IAX secret, and matching confirmation.
3. Normally leave **automatic AllStarLink IAX host/port lookup ON**. It locates the appropriate host and UDP port, which might not be 4569.
4. Only if required by the destination operator, turn off automatic lookup and enter a manual hostname/IP and UDP port. **Called Context** is normally blank; **Called Extension** can use `%NODE%` for the destination node number.
5. Save the login and Settings. Choose **IAX2** and the saved profile, then tap **Connect**.

**Reset Defaults** restores typical technical fields (username `iaxrpt`, automatic lookup on, host `%NODE%.nodes.allstarlink.org`, port `4569`, blank context, extension `%NODE%`) without erasing your destination node or IAX secret. Removing a profile can leave Favorites that need editing.

### NM — Node Mode

Node Mode uses the identity of an AllStar node **you own**. It does not use your Portal password or an IAX secret.

1. In **Settings → Node Mode → Add Node**, enter the owned node number and its **AllStarLink Node Password**, twice.
2. Save the identity and Settings. You can save multiple owned-node identities.
3. Select **NM**, choose **Register As** (your owned identity), enter the **Destination Node**, and tap **Connect**.

**Register As** and **Destination Node** are different: the destination must not equal the Register-As node. Avoid competing registrations of the same identity from multiple devices. Removing an owned identity may require updating related Favorites.

## Everyday operation

### Connecting and disconnecting

Select WT, IAX2, or NM; enter or choose the required node/profile; tap **Connect**. Watch the connection status and **Activity** panel for success or errors. Use **Disconnect** to end the session and unkey.

**Settings:** **Save** stores valid changes; **Cancel** or Android Back leaves unsaved edits behind. Password confirmation must match even if Remember Credentials is off.

### Push-to-talk (PTT)

- **HOLD:** press and hold PTT to transmit; release to unkey.
- **TOGGLE:** tap once to key and again to unkey.
- **VOX:** speech above the threshold keys automatically, with Attack and Hang timing and a Maximum Transmit safety limit.

If you tap manual PTT while VOX is active, the app unkeys, exits VOX, switches to TOGGLE, and remains unkeyed; the **next** tap keys normally. Always make sure PTT is unkeyed when finished. Disconnect or connection loss also releases transmit.

### Audio and VOX

Adjust **Receive Volume** for incoming audio and **Microphone Gain** for transmitted audio. The **Mic Level** indication helps check microphone input.

VOX controls: **Threshold** (speech sensitivity), **Attack** (time before keying), **Hang** (time before unkeying), and **Maximum Transmit** (safety cutoff). VOX Reset Defaults: Threshold **8%**, Attack **120 ms**, Hang **700 ms**, Maximum Transmit **180 seconds**. Tap **Save** to keep reset values.

**Audio Reset Defaults** restores Receive Volume and Microphone Gain to **100%**; it does not erase passwords, Favorites, or profiles.

Use a headset when possible to avoid received audio retriggering VOX.

### Favorites, lookup, and connected stations

**Favorites** store a destination plus its connection mode and, when needed, its IAX profile or Node Mode identity. The same node may appear in multiple Favorites for different modes. You can add a Favorite manually or from Connected Nodes, then connect, edit, remove, or open its callsign in **QRZ**.

**Connected Nodes / Stations** can expand to show linked nodes and stations. **Node Lookup** and **Callsign Lookup** help find destinations; a callsign may own more than one node. Check the selected node number before connecting or saving a Favorite.

### Activity, alerts, and background use

The **Activity** view reports connection progress, errors, and radio/session events; consult it first when troubleshooting. Optional spoken disconnect notification can alert you when a session ends.

The Android app supports continuing an active connection in the background or with the screen off, subject to Android permissions and device power management. Moving between Wi-Fi and cellular can interrupt IAX/UDP connections; reconnect if needed. The app includes connection-loss and transmit-unkey safeguards.

## Verify the APK SHA-256

**SHA-256 verifies that your downloaded file matches the exact file published by the project.** The 64-character APK checksum changes when a new APK is built or signed. It is **not** the same as the signing-certificate fingerprint.

On a Windows computer:

1. Download the APK from the official GitHub release.
2. Open **File Explorer**, navigate to the folder containing the downloaded APK (usually **Downloads**).
3. Click the File Explorer address bar, type `powershell`, and press **Enter**. This opens PowerShell **in that folder**.
4. Run this command for the v1.1 APK:

```powershell
Get-FileHash .\AllStarTransceiver-Android.apk -Algorithm SHA256
```

5. Compare **all 64 characters** of the displayed hash with the **v1.1 APK SHA-256 published on the GitHub release page**. They must match exactly. If PowerShell cannot find the APK, check the folder and exact downloaded filename.

**Official Android v1.1 APK SHA-256:**

`6846160F4952462DF6B061E8A1A205B7A66BF2ACB59B1D18D0D2611A14507FBC`

If the values differ, do not install the file; download it again from the official release. The older v1.0 checksum does **not** verify v1.1.

### Signing-certificate fingerprint

Official Android production signing-certificate **SHA-256**:

`66BE7641C9E9F5A0AE796BC25541E64BFBD43FBB4E5F23CEF4386ADF4A6DF1F0`

This identifies the **signing certificate**, not the APK's file contents. That fingerprint stays the same across official updates even though each APK file has a different SHA-256.

## Troubleshooting

| Problem | Check |
|---|---|
| WT / AppAuth login fails | Correct AllStarLink callsign and **website password**; check Activity and network access |
| IAX2 fails | Correct destination-specific IAX username/secret, profile, hostname/port and any required context/extension |
| NM fails | Owned **Register As** node, correct **Node Password**, and a **different** Destination Node |
| Password mismatch in Settings | Enter both password fields identically, regardless of Remember Credentials |
| No receive audio | Connection status, Receive Volume, phone audio route, and network |
| No or weak transmit audio | Microphone permission, PTT state, microphone gain, and input level |
| VOX keys unexpectedly | Raise threshold or use a headset to prevent speaker feedback |
| Connection drops during Wi-Fi/cellular change | Check Activity and reconnect |
| Favorite connects in wrong mode | Edit its saved WT/IAX2/NM mode and associated profile or identity |

If a problem persists, note the phone model, Android/app version, connection mode, Wi-Fi or cellular, and the relevant **Activity** message. Never share passwords, IAX secrets, or Node Passwords.

## Privacy and support

Favorites, profiles, mode choices, audio/VOX settings, and opted-in remembered credentials are held locally. Avoid posting screenshots or logs containing private information. Remembered passwords use protected local storage; **uninstalling may erase data and stored credentials**.

For support, contact **[KC3KMV on QRZ](https://www.qrz.com/db/KC3KMV)**.

