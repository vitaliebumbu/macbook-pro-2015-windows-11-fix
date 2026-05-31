# Troubleshooting

## Wi-Fi Still Shows No Networks

Check Location settings first:

```text
Settings > Privacy & security > Location
```

Make sure these are on:

- Location services
- Let apps access your location
- Let desktop apps access your location

Then restart Windows.

## Sound Still Does Not Work

Open Device Manager.

Look under:

```text
Sound, video and game controllers
```

Good:

```text
Cirrus Logic CS4208
```

Not ideal:

```text
High Definition Audio Device
```

If you still see only generic audio, reinstall Boot Camp support software and reboot.

## Two-Finger Scroll Still Does Not Work

Open Boot Camp Control Panel.

Look for the **Trackpad** tab. If the Trackpad tab is missing, the Apple trackpad driver is not installed correctly.

Try:

1. Reinstall Boot Camp support software.
2. Reboot.
3. Open Boot Camp Control Panel again.

If the Apple driver works but feels poor, consider:

```text
https://github.com/imbushuo/mac-precision-touchpad
```

## Fans Are Still Loud

First, let Windows sit idle for 10 minutes after boot. Updates, indexing, and driver installs can temporarily use CPU.

Then check Task Manager:

1. Press `Ctrl + Shift + Esc`.
2. Click **Processes**.
3. Sort by **CPU**.

If one app is using lots of CPU, close or update that app.

If CPU use is low but fans stay loud:

1. Make sure Boot Camp drivers are installed.
2. Set maximum processor state to `99%`.
3. Consider a fan control tool.

## Device Manager Still Shows Unknown Devices

Some child devices may show as unknown on newer Windows builds. The important part is that the main devices work.

Important devices that should be OK:

```text
Apple SMC device
Apple panel backlight
Apple graphics mux
Apple Multi-Touch
Cirrus Logic CS4208
Intel SMBus Controller
Apple Broadcom Built-in Bluetooth
```

If those are missing, reinstall Boot Camp support software.

