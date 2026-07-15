# Valla Amp Modeler GPU 0.7.11 
![Valla Amp Modeler GPU interface](assets/screen1.png)
Independent NAM-compatible GPU amp modeler by Valla Productions.

It work only with A2 NAM profile.

## macOS arm64 artifacts

- `Valla Amp Modeler GPU.app`
- `Valla Amp Modeler GPU.vst3`
- `Valla Amp Modeler GPU.component`

The bundles require macOS 15.0 or newer and the GPU Audio LTS v2 runtime.
They are ad-hoc signed for local development and testing.

Install the VST3 and Audio Unit in:

- `~/Library/Audio/Plug-Ins/VST3/`
- `~/Library/Audio/Plug-Ins/Components/`

## macOS Security Notice

> [!NOTE]
> On first launch, macOS may block **Valla Amp Modeler GPU** or report that Apple cannot verify the developer.
>
> This warning does not automatically mean that the plug-in is unsafe. It appears because the current macOS build is distributed independently and is not yet signed and notarized through the Apple Developer Program.

> [!IMPORTANT]
> For your security, download the plug-in only from the official **GitHub Releases** page of this repository.

### Installation

Copy:

```text
Valla Amp Modeler GPU.vst3
```

to one of the following folders:

```text
/Library/Audio/Plug-Ins/VST3/
```

or, for the current user only:

```text
~/Library/Audio/Plug-Ins/VST3/
```

### Allow the plug-in on macOS

Close your DAW, open **Terminal**, and run:

```bash
sudo xattr -rd com.apple.quarantine "/Library/Audio/Plug-Ins/VST3/Valla Amp Modeler GPU.vst3"
```

If you installed it in your user folder, run:

```bash
xattr -rd com.apple.quarantine "$HOME/Library/Audio/Plug-Ins/VST3/Valla Amp Modeler GPU.vst3"
```

When using `sudo`, macOS may ask for your password. Nothing will appear while typing it — this is normal.

Restart your DAW and perform a full VST3 rescan.

### If the plug-in is still blocked

Apply a local ad-hoc signature:

```bash
sudo codesign --force --deep --sign - "/Library/Audio/Plug-Ins/VST3/Valla Amp Modeler GPU.vst3"
```

Then restart your DAW and scan the plug-in again.

> [!TIP]
> These commands affect only **Valla Amp Modeler GPU**. They do not disable Gatekeeper or the general security protections of your Mac.

Apple notarization may be added in a future release. Until then, thank you for supporting a free and independent audio project.




Identity:

- bundle base: `com.vallaproductions.vallaampmodelergpu`
- VST3 class ID: `EF9C4601-7760-4C18-B2D5-14B2DD37C370`
- Audio Unit: `aufx` / `VAMG` / `VaPr`

This is an unofficial derivative of NeuralAmpModelerPlugin and
NeuralAmpModelerCore by Steven Atkinson. It is not affiliated with or endorsed
by the Neural Amp Modeler project. 

Attribution and licensing

Valla Amp Modeler GPU is an independent and unofficial derivative work based in part on NeuralAmpModelerPlugin and NeuralAmpModelerCore by Steven Atkinson.
NeuralAmpModelerPlugin is Copyright (c) 2022 Steven Atkinson and is distributed under the MIT License.
NeuralAmpModelerCore is Copyright (c) 2023 Steven Atkinson and is distributed under the MIT License.
Modifications and GPU integration are Copyright (c) 2026 Francesco Valla / Valla Productions Original.
Valla Amp Modeler GPU is not affiliated with, sponsored by, approved by, or endorsed by Steven Atkinson or by the official Neural Amp Modeler project.
Complete copyright and license notices are included in ThirdPartyNotices.txt, distributed both with and inside the plug-in bundle.
