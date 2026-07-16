# Valla Amp Modeler GPU

![Valla Amp Modeler GPU interface](assets/screen1.png)

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

Use **LITE** mode when working with large projects or when running multiple plug-in instances simultaneously.

LITE mode reduces the processing load of each instance, allowing the system to sustain a greater number of active amp models.

LITE mode is recommended for:

* Recording and arrangement
* Large sessions
* Multiple guitar or bass tracks
* Real-time monitoring
* Auditioning different NAM A2 profiles
* Projects requiring many simultaneous plug-in instances

### FULL Mode

Use **FULL** mode when maximum processing quality is required.

FULL mode is recommended for:

* Final tone selection
* Critical listening
* Track rendering
* Mixing
* Final export

The number of simultaneous FULL-mode instances depends on several factors, including:

* The selected NAM A2 profiles
* The loaded IR files
* Audio buffer size
* Sample rate
* Host application
* Additional plug-ins in the session
* Available CPU and GPU resources

## Reference Performance

On my system an **Apple M4 Max with a 14-core CPU**—Valla Amp Modeler GPU can run **48 = simultaneous FULL-mode instances with buffer at 64 (4.7ms), with each instance processing both a **NAM A2 profile and an IR**. 

48 channels, each running one FULL NAM A2 profile and one IR at a 64-sample buffer, while substantially offloading NAM inference from the CPU and leaving more processing resources available for instruments, mixing, effects, and the rest of the DAW session.

Beyond 48 simultaneous FULL-mode instances, real-time performance becomes increasingly unpredictable and should not be considered reliable. Audio dropouts, processing overloads, or instability may occur depending on the selected profiles, IR files, sample rate, DAW session, and overall system load.

> [!NOTE]
> This result is provided as a practical reference, not as a guaranteed instance count.
>
> Performance may vary between systems, projects, DAWs, NAM profiles, and IR files.

For sessions requiring more simultaneous instances, use **LITE mode** or render completed tracks to audio once the desired NAM A2 profile and IR have been selected.

## Recommended Workflow

For the most efficient production workflow:

1. Load and audition NAM A2 profiles using **LITE** mode.
2. Select the NAM A2 profile and IR that best suit the track.
3. Switch the final instance to **FULL** mode.
4. Render, bounce, commit, or freeze the processed track.
5. Disable or remove the live plug-in instance when it is no longer required.

Rendering completed tracks reduces real-time processing usage and makes additional resources available to the rest of the project.

### Ableton Live Example

In Ableton Live:

1. Select the track containing Valla Amp Modeler GPU.
2. Right-click the track header.
3. Select **Freeze Track**.
4. Listen to the frozen result and confirm that it sounds correct.
5. Optionally select **Flatten** to convert the frozen track permanently into audio.

> [!TIP]
> Duplicate the original track before using **Flatten** if you want to preserve an editable version of the plug-in chain and its settings.

The same workflow can be used in other DAWs through their respective **Freeze**, **Bounce**, **Render**, **Commit**, or **Print to Audio** functions.

## Supported Content

| Content type        |       Support |
| ------------------- | ------------: |
| NAM A2 profiles     |     Supported |
| Legacy NAM profiles | Not supported |
| Non-A2 NAM profiles | Not supported |
| External IR files   |     Supported |

## macOS Compatibility

The current release is built for **Apple Silicon Macs**.

### Requirements

* Apple Silicon Mac
* macOS 15.0 or newer
* A VST3- or Audio Unit-compatible host application

## Included Formats

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

After installation, restart your DAW and perform a complete plug-in rescan.

## macOS Security Notice

> [!NOTE]
> On first launch, macOS may block Valla Amp Modeler GPU or report that Apple cannot verify the developer.

This warning does not automatically indicate that the plug-in is unsafe. It appears because the current macOS build is distributed independently and is not yet signed and notarized through the Apple Developer Program.

For security, download the plug-in only from the official **Releases** section of this repository.

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

This software is provided without warranty.

Performance figures are based on the developer's test system and are not guaranteed on other hardware or in different DAW sessions.

Test the plug-in in a non-critical session before using it in production, and always keep backups of important projects.
