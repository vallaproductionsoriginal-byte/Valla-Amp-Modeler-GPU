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
