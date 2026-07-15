# Valla Amp Modeler GPU 0.7.11 

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
by the Neural Amp Modeler project. See the source repository and included
licenses for full attribution.
