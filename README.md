# Valla Amp Modeler GPU

![Valla Amp Modeler GPU interface](assets/valla-amp-modeler-gpu.png)

**Valla Amp Modeler GPU** is an independent, GPU-accelerated amp modeler based on NeuralAmpModelerCore and optimized for Apple Metal.

It supports **NAM A2 model profiles** and external **Impulse Response (IR)** files, providing an efficient workflow for guitar and bass amp modeling on Apple Silicon systems.

> [!IMPORTANT]
> Valla Amp Modeler GPU processes **NAM A2 profiles only**.
>
> Legacy NAM models and NAM profiles using architectures other than A2 are not supported.

## Features

* GPU-accelerated NAM processing through Apple Metal
* Support for **NAM A2 model profiles**
* External cabinet **Impulse Response loading**
* Dedicated **LITE** and **FULL** processing modes
* VST3, Audio Unit, and standalone application formats
* Native Apple Silicon support

## Processing Modes

Valla Amp Modeler GPU provides two processing modes designed for different stages of production.

### LITE Mode

Use **LITE** mode when working with larger projects or when running multiple plug-in instances simultaneously.

LITE mode reduces the processing requirements of each instance, allowing the system to sustain a higher number of active amp models.

Recommended for:

* Recording and arrangement
* Large sessions
* Multiple guitar or bass tracks
* Real-time monitoring
* Projects requiring many simultaneous plug-in instances

### FULL Mode

Use **FULL** mode when maximum processing quality is required.

Recommended for:

* Final sound selection
* Critical listening
* Track rendering
* Mixing and export

The number of simultaneous FULL instances that can be used depends on the selected model, audio buffer size, sample rate, host application, and available GPU resources.

## Recommended Workflow

For the most efficient production workflow:

1. Load and audition NAM A2 profiles using **LITE** mode.
2. Select the profile and IR that best suit the track.
3. Switch the final instance to **FULL** mode.
4. Render, bounce, or freeze the processed track.
5. Disable or remove the live plug-in instance when it is no longer required.

Rendering completed tracks reduces real-time GPU usage and makes additional processing resources available to the rest of the project.

### Ableton Live Example

In Ableton Live:

1. Select the track containing Valla Amp Modeler GPU.
2. Right-click the track header.
3. Select **Freeze Track**.
4. After confirming the result, optionally select **Flatten** to convert the frozen track into audio.

Consider duplicating the original track before flattening if you want to preserve an editable version of the plug-in chain.

The same principle can be applied in other DAWs using their respective **Freeze**, **Bounce**, **Render**, **Commit**, or **Print to Audio** functions.

## Supported Content

| Content type                  | Support       |
| ----------------------------- | ------------- |
| NAM A2 profiles               | Supported     |
| Legacy or non-A2 NAM profiles | Not supported |
| External IR files             | Supported     |

## macOS Compatibility

The current release is built for **Apple Silicon Macs**.

### Requirements

* Apple Silicon Mac
* macOS 15.0 or newer
* VST3- or Audio Unit-compatible host application

### Included Formats

* `Valla Amp Modeler GPU.app`
* `Valla Amp Modeler GPU.vst3`
* `Valla Amp Modeler GPU.component`

## Installation

Copy the plug-in files to the appropriate macOS folders.

### VST3

System-wide installation:

```text
/Library/Audio/Plug-Ins/VST3/
```

Current-user installation:

```text
~/Library/Audio/Plug-Ins/VST3/
```

### Audio Unit

System-wide installation:

```text
/Library/Audio/Plug-Ins/Components/
```

Current-user installation:

```text
~/Library/Audio/Plug-Ins/Components/
```

Restart your DAW and perform a complete plug-in rescan after installation.

## macOS Security Notice

> [!NOTE]
> On first launch, macOS may block Valla Amp Modeler GPU or report that Apple cannot verify the developer.

This warning does not automatically indicate that the plug-in is unsafe. It appears because the current macOS build is distributed independently and is not yet signed and notarized through the Apple Developer Program.

For security, download the plug-in only from the official Releases section of this repository.

### Remove the Quarantine Attribute

Close your DAW before running the following command.

For a system-wide VST3 installation:

```bash
sudo xattr -rd com.apple.quarantine "/Library/Audio/Plug-Ins/VST3/Valla Amp Modeler GPU.vst3"
```

For a current-user VST3 installation:

```bash
xattr -rd com.apple.quarantine "$HOME/Library/Audio/Plug-Ins/VST3/Valla Amp Modeler GPU.vst3"
```

When using `sudo`, macOS may request your password. No characters will appear while entering it; this is normal.

Restart your DAW and perform a complete VST3 rescan.

### If the Plug-in Is Still Blocked

Apply a local ad-hoc signature:

```bash
sudo codesign --force --deep --sign - "/Library/Audio/Plug-Ins/VST3/Valla Amp Modeler GPU.vst3"
```

Restart your DAW and scan the plug-in again.

> [!TIP]
> These commands affect only Valla Amp Modeler GPU. They do not disable Gatekeeper or the general security protections of macOS.

Apple notarization may be added in a future release.

## Plug-in Identity

* Bundle identifier: `com.vallaproductions.vallaampmodelergpu`
* VST3 class ID: `EF9C4601-7760-4C18-B2D5-14B2DD37C370`
* Audio Unit identity: `aufx` / `VAMG` / `VaPr`

## Attribution and Licensing

Valla Amp Modeler GPU is an independent and unofficial derivative work based in part on **NeuralAmpModelerPlugin** and **NeuralAmpModelerCore** by Steven Atkinson.

* NeuralAmpModelerPlugin is Copyright © 2022 Steven Atkinson and is distributed under the MIT License.
* NeuralAmpModelerCore is Copyright © 2023 Steven Atkinson and is distributed under the MIT License.
* Modifications and GPU integration are Copyright © 2026 Francesco Valla / Valla Productions Original.

Valla Amp Modeler GPU is not affiliated with, sponsored by, approved by, or endorsed by Steven Atkinson or by the official Neural Amp Modeler project.

Complete copyright notices, license texts, and third-party attributions are available in [`ThirdPartyNotices.txt`](ThirdPartyNotices.txt).

## Disclaimer

This software is provided without warranty. Test the plug-in in a non-critical session before using it in production, and always keep backups of important projects.
