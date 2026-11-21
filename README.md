# HomePod Hotkey

Stream Windows 11 audio to a HomePod. Press **Ctrl + Shift + H** to switch from your PC speakers to the HomePod. Move the usual Windows volume slider to change the HomePod volume. Press the shortcut again to restore your PC speakers and their previous volume.

[Download the Windows 11 preview](https://github.com/ekrasniq/homepod-hotkey/releases/tag/v0.1.0) · [Watch the 20-second illustrated walkthrough](https://github.com/ekrasniq/homepod-hotkey/releases/download/v0.1.0/homepod-hotkey-demo.mp4)

![Illustration of the shortcut switching audio to a HomePod](https://raw.githubusercontent.com/ekrasniq/homepod-hotkey/main/media/walkthrough.png)

## Set up

1. Use Windows 11 on an x64 PC with **64-bit Python 3.12** installed. The PC and HomePod need to be on the same local network with AirPlay access. [Python 3.12 for Windows](https://www.python.org/downloads/release/python-31210/)
2. Download **homepod-hotkey-0.1.0-win11-x64.zip** from the release. Extract it to a folder you intend to keep.
3. Double-click **Setup.cmd**. It downloads the Python packages listed in `requirements.txt` into a virtual environment in that folder and creates a per-user **HomePod Hotkey** Start menu shortcut. No additional audio driver is required.
4. Play something at a comfortable volume. Press **Ctrl + Shift + H**, wait for the HomePod to connect, then try the Windows volume slider. Press the shortcut again to switch back. The Start menu entry does the same thing.

**Multiple HomePods?** Open a terminal in the extracted folder and run `.\Setup.cmd --device "Kitchen"`, replacing Kitchen with your HomePod name. Re-run setup after moving the folder. If another app uses the shortcut, open **HomePod Hotkey** from Start.

## Tested on Windows 11

One first-generation HomePod played system audio with the PC speakers muted, responded to the Windows slider and switched back using the shortcut. A microphone measurement on this setup put the delay from Windows audio capture to sound at **about 0.35 seconds**. This measures continuous playback. Connection startup takes longer. Audio is sent as 16-bit stereo at 44.1 kHz on the tested device.

HomePod mini, stereo pairs and other Windows audio drivers still need testing. Some drivers may also silence loopback capture when the local output is muted.

## Troubleshooting

- To see connection messages, run `.\HomePod.cmd` from a terminal. Stop with **Ctrl + C**. If the HomePod requires an AirPlay password, use this console command so you can enter it.
- Run `.\HomePod.cmd --test-tone` to send six short tones directly. If they play but desktop audio is silent, check which Windows playback device the app uses. Share the result in [Issues](https://github.com/ekrasniq/homepod-hotkey/issues).
- To uninstall, stop streaming, remove **HomePod Hotkey** from your Start menu's Programs folder and delete the extracted folder including its private Python environment.

## License and dependencies

The preview is free to use under the [use license](LICENSE.txt). The ZIP contains the compiled sender. Setup downloads third-party dependencies from the Python package index, including [pyatv](https://github.com/postlund/pyatv), [PyAudioWPatch](https://github.com/s0d3s/PyAudioWPatch), [pycaw](https://github.com/AndreMiras/pycaw), [NumPy](https://numpy.org/) and [samplerate](https://pypi.org/project/samplerate/). HomePod Hotkey is an independent project.
