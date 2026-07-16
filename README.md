# Valla Amp Modeler GPU

![Valla Amp Modeler GPU interface](assets/screen1.png)

**Valla Amp Modeler GPU** is an independent, GPU-accelerated amp modeler based on NeuralAmpModelerCore and optimized for Apple Metal.

It supports **NAM A2 model profiles** and external **Impulse Response (IR)** files, providing an efficient workflow for guitar and bass amp modeling on Apple Silicon systems.

> [!IMPORTANT]
> Valla Amp Modeler GPU processes **NAM A2 profiles only**.
> Legacy NAM models and NAM profiles using architectures other than A2 are not supported.

## Why GPU Acceleration?

GPU acceleration is not primarily intended to reduce the latency of a single NAM instance. Its main advantage is to expand the total processing capacity available in large projects.

In complex DAW sessions, the CPU often becomes the primary bottleneck while a significant amount of GPU processing power remains unused. By moving NAM A2 inference and IR convolution to the GPU, Valla Amp Modeler GPU makes use of these otherwise idle computational resources and preserves CPU capacity for:

* Virtual instruments
* Audio effects
* Mixing and bus processing
* Automation
* Oversampling
* Other real-time DAW operations

The objective is not simply to make one amp model faster, but to distribute the processing workload more efficiently across the system.

This can be particularly useful in large projects where CPU resources are already heavily occupied but GPU processing capacity is still available.

## Performance Reference

The plug-in has been tested on the following system:

* **Computer:** MacBook Pro
* **Processor:** Apple M4 Max, 14-core CPU
* **Audio buffer:** 64 samples
* **Processing mode:** FULL
* **Simultaneous channels:** 48
* **NAM processing:** One FULL NAM A2 profile per channel
* **Cabinet processing:** One external IR per channel

The system was able to run:

> **48 simultaneous channels, each running one FULL NAM A2 profile and one external IR at a 64-sample buffer.**

Beyond 48 simultaneous FULL instances, reliability became less consistent and depended on the selected models, IR files, host workload, and overall project configuration.

This result should be considered a practical reference rather than a guaranteed performance specification.

Actual performance depends on:

* Apple Silicon model and GPU configuration
* Selected NAM A2 profiles
* Selected IR files
* Audio buffer size
* Sample rate
* DAW and plug-in host
* Project complexity
* Other active GPU workloads
* Other plug-ins and virtual instruments

## Features

* GPU-accelerated NAM processing through Apple Metal
* Support for NAM A2 model profiles
* External cabinet Impulse Response loading
* Dedicated LITE and FULL processing modes
* VST3 plug-in
* Audio Unit plug-in
* Standalone application
* Native Apple Silicon support

## Processing Modes

Valla Amp Modeler GPU provides two processing modes designed for different stages of production.

### LITE Mode

Use **LITE mode** when working with larger projects or when running many plug-in instances simultaneously.

LITE mode reduces the processing requirements of each instance, allowing the system to sustain a higher number of active amp models.

Recommended for:

* Recording
* Arrangement
* Large sessions
* Multiple guitar or bass tracks
* Real-time monitoring
* Profile and IR auditioning
* Projects requiring many simultaneous plug-in instances

### FULL Mode

Use **FULL mode** when maximum processing quality is required.

Recommended for:

* Final sound selection
* Critical listening
* Track rendering
* Mixing
* Export
* Final production work

The number of simultaneous FULL instances that can be used depends on the selected model, IR file, audio buffer size, sample rate, host application, project complexity, and available GPU resources.

## Recommended Workflow

For the most efficient production workflow:

1. Load and audition NAM A2 profiles using **LITE mode**.
2. Select the NAM profile and IR that best suit the track.
3. Switch the final instance to **FULL mode**.
4. Render, bounce, freeze, commit, or print the processed track to audio.
5. Disable or remove the live plug-in instance when it is no longer required.

Rendering completed tracks reduces real-time GPU usage and makes additional processing resources available to the rest of the project.

This workflow is especially recommended in large sessions containing many amp-modeling instances.

### Ableton Live Example

In Ableton Live:

1. Select the track containing Valla Amp Modeler GPU.
2. Right-click the track header.
3. Select **Freeze Track**.
4. Listen to the frozen result and verify that it sounds correct.
5. Optionally select **Flatten** to convert the frozen track permanently into audio.

Consider duplicating the original track before flattening if you want to preserve an editable version of the plug-in chain.

The same principle can be applied in other DAWs using their respective:

* Freeze
* Bounce
* Render
* Commit
* Print to Audio

functions.

## Supported Content

| Content type             | Support       |
| ------------------------ | ------------- |
| NAM A2 profiles          | Supported     |
| Legacy NAM profiles      | Not supported |
| Non-A2 NAM architectures | Not supported |
| External IR files        | Supported     |

## macOS Compatibility

The current release is built for Apple Silicon Macs.

### Requirements

* Apple Silicon Mac
* macOS 15.0 or newer
* VST3- or Audio Unit-compatible host application

### Included Formats

* `Valla Amp Modeler GPU.app`
* `Valla Amp Modeler GPU.vst3`
* `Valla Amp Modeler GPU.component`

## Download

Download the latest build from the official GitHub Releases section:

[Download Valla Amp Modeler GPU](https://github.com/vallaproductionsoriginal-byte/Valla-Amp-Modeler-GPU/releases)

For security, download the plug-in only from this repository or its official Releases page.

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

After installation:

1. Restart your DAW.
2. Perform a complete plug-in rescan.
3. For the Audio Unit version, restart the Mac if the plug-in is not detected immediately.

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

When using `sudo`, macOS may request your password.

No characters will appear while entering the password in Terminal. This is normal.

After running the command:

1. Restart your DAW.
2. Perform a complete VST3 rescan.

### Audio Unit Quarantine Removal

For a system-wide Audio Unit installation:

```bash
sudo xattr -rd com.apple.quarantine "/Library/Audio/Plug-Ins/Components/Valla Amp Modeler GPU.component"
```

For a current-user Audio Unit installation:

```bash
xattr -rd com.apple.quarantine "$HOME/Library/Audio/Plug-Ins/Components/Valla Amp Modeler GPU.component"
```

After running the command, restart the DAW and rescan the Audio Unit plug-ins.

### Standalone Application Quarantine Removal

Run the following command, replacing the path if the application is installed somewhere else:

```bash
xattr -rd com.apple.quarantine "/Applications/Valla Amp Modeler GPU.app"
```

### If the Plug-in Is Still Blocked

Apply a local ad-hoc signature.

For a system-wide VST3 installation:

```bash
sudo codesign --force --deep --sign - "/Library/Audio/Plug-Ins/VST3/Valla Amp Modeler GPU.vst3"
```

For a current-user VST3 installation:

```bash
codesign --force --deep --sign - "$HOME/Library/Audio/Plug-Ins/VST3/Valla Amp Modeler GPU.vst3"
```

Restart your DAW and scan the plug-in again.

> [!TIP]
> These commands affect only Valla Amp Modeler GPU. They do not disable Gatekeeper or the general security protections of macOS.

Apple notarization may be added in a future release.

## Plug-in Identity

* **Bundle identifier:** `com.vallaproductions.vallaampmodelergpu`
* **VST3 class ID:** `EF9C4601-7760-4C18-B2D5-14B2DD37C370`
* **Audio Unit identity:** `aufx` / `VAMG` / `VaPr`

## Attribution and Licensing

Valla Amp Modeler GPU is an independent and unofficial derivative work based in part on NeuralAmpModelerPlugin and NeuralAmpModelerCore by Steven Atkinson.

* NeuralAmpModelerPlugin is Copyright © 2022 Steven Atkinson and is distributed under the MIT License.
* NeuralAmpModelerCore is Copyright © 2023 Steven Atkinson and is distributed under the MIT License.
* Modifications and GPU integration are Copyright © 2026 Francesco Valla / Valla Productions Original.

Valla Amp Modeler GPU is not affiliated with, sponsored by, approved by, or endorsed by Steven Atkinson or by the official Neural Amp Modeler project.

Complete copyright notices, license texts, and third-party attributions are available in [ThirdPartyNotices.txt](ThirdPartyNotices.txt).

## Disclaimer

This software is provided without warranty.

Performance results are system-dependent and should not be interpreted as guaranteed minimum or maximum instance counts.

Test the plug-in in a non-critical session before using it in production, and always keep backups of important projects.

## ☕ Support & More Projects

Valla Amp Modeler GPU is developed and distributed free of charge.

If you find the plugin useful and would like to support its continued development, you can buy me a coffee:

<p align="left">
  <a href="https://www.buymeacoffee.com/cicciovalla">
    <img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png"
         alt="Buy Me a Coffee"
         height="50">
  </a>
</p>

Your support helps fund testing, maintenance, and future improvements. Thank you!

### 🎹 Check Out My Other Music Apps

While you're here, you can also check out my other music applications available on Google Play:

<p align="left">
  <a href="https://play.google.com/store/apps/developer?id=Francesco+Valla">
    <img src="https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png"
         alt="View Francesco Valla apps on Google Play"
         height="70">
  </a>
</p>

Currently available:

* **Harmony Engine Plus**
* **Harmony Engine Lite**

