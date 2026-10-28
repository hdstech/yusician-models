# Yusician models

Model files the Yusician app downloads when a feature first needs them, kept here so the downloads don't depend
on anyone else's server. Each file is attached to a release; the app checks its SHA-256 before using it.

## htdemucs.onnx (release `htdemucs-1`)

**Used for:** Split into stems (drums, bass, other, vocals).

- **Model:** HT-Demucs (Demucs v4, the `htdemucs` checkpoint) by Meta AI Research, from
  [facebookresearch/demucs](https://github.com/facebookresearch/demucs). MIT licence: see [LICENSE](LICENSE).
- **Made from:** the MIT-licensed ONNX export [StemSplitio/htdemucs-onnx](https://huggingface.co/StemSplitio/htdemucs-onnx)
  (`htdemucs_fp16weights.onnx`), with its 16-bit weights and its 64-bit values converted to 32-bit floats so it runs in
  [rten](https://github.com/robertknight/rten). The output matches the original to within 3e-8.
- **Input:** `mix`, float32 `[1, 2, 343980]`: 7.8 s of 44.1 kHz stereo. **Output:** `stems`, float32
  `[1, 4, 2, 343980]` in the order drums, bass, other, vocals. Longer audio is split into windows a quarter
  overlapping, faded and added.
- **Size:** 310,896,755 bytes. **SHA-256:** `4d6f8ec3cbb9e74522c27e5d6da937bb3e7a4cabec8e857e3cf115335e362513`
