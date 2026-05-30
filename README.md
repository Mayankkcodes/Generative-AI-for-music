# Generative AI for Music: MusicGen Fine-Tuning on NSynth

This project explores fine-tuning a pre-trained generative music model for audio generation. The main goal is to understand how MusicGen works, how text conditioning affects music generation, and how fine-tuning on a music dataset changes the generated audio output.

The project uses **Facebook MusicGen Small** through the **AudioCraft** framework and fine-tunes it on a subset of the **NSynth** dataset. Audio samples are generated before and after fine-tuning and then compared using basic audio features.

---

## Project Objective

**Task 2: Generative AI for Music**

The objective of this task is to fine-tune a pre-trained generative music model and explore its ability to generate music audio.

The project covers:

* Studying MusicGen architecture, conditioning, and training objective
* Fine-tuning a pre-trained MusicGen model on NSynth
* Generating audio samples before and after fine-tuning
* Comparing generated outputs
* Observing how training data affects generation quality

---

## Model and Framework

| Component       | Details                      |
| --------------- | ---------------------------- |
| Base Model      | `facebook/musicgen-small`    |
| Framework       | AudioCraft                   |
| Training System | Dora                         |
| Dataset         | NSynth subset                |
| Conditioning    | Text-to-music prompts        |
| Output          | Generated `.wav` audio files |

---

## Dataset

This project uses a subset of the **NSynth dataset**.

NSynth contains isolated musical instrument notes from different instruments, pitches, and timbres. Since the dataset contains clean note-level recordings, it is useful for studying how fine-tuning affects instrument-like generation and timbral characteristics.

---

## Project Workflow

The complete workflow followed in this project is:

1. Installed AudioCraft and required dependencies in Google Colab.
2. Loaded and prepared a subset of the NSynth dataset.
3. Created an AudioCraft-compatible dataset structure.
4. Generated baseline audio samples using the pre-trained MusicGen model.
5. Fine-tuned MusicGen-small on the NSynth subset.
6. Exported the fine-tuned model.
7. Generated audio samples using the fine-tuned model.
8. Compared pre-trained and fine-tuned outputs using basic audio features.
9. Saved generated samples and comparison results.

---

## Repository Structure

```text
Generative-AI-for-music/
│
├── README.md
├── requirements.txt
│
├── notebook/
│   └── Generative_AI_for_Music_MusicGen_NSynth.ipynb
│
└── results/
    ├── comparison.csv
    │
    ├── pretrained_samples/
    │   ├── generated audio samples before fine-tuning
    │   └── manifest.json
    │
    └── fine-tuned_samples/
        ├── generated audio samples after fine-tuning
        └── manifest.json
```

---

## Fine-Tuning Configuration

The model was fine-tuned using AudioCraft's Dora training system.

Important training settings used:

| Parameter         | Value                     |
| ----------------- | ------------------------- |
| Base model        | `facebook/musicgen-small` |
| Dataset           | NSynth subset             |
| Batch size        | 1                         |
| Segment duration  | 4 seconds                 |
| Epochs            | 2                         |
| Updates per epoch | 100                       |
| Learning rate     | `1e-5`                    |
| Conditioning      | Text-to-music             |

A smaller test run was first used to verify that training was working correctly before running the main fine-tuning experiment.

---

## Text Prompts Used

The same prompts were used before and after fine-tuning for fair comparison:

```text
Indian classical inspired plucked string note with tanpura like drone
Carnatic inspired violin phrase with sustained acoustic tone
Hindustani inspired bansuri like melodic phrase with soft drone
Veena inspired plucked string improvisation with raga like ornamentation
Sitar like acoustic plucked string phrase with Indian classical mood
Meditative Indian classical instrumental texture with sustained notes
```

---

## Results

The generated samples are stored in the `results` folder.

### Pre-trained Model Outputs

```text
results/pretrained_samples/
```

These samples were generated using the original pre-trained MusicGen-small model.

### Fine-Tuned Model Outputs

```text
results/fine-tuned_samples/
```

These samples were generated after fine-tuning the model on the NSynth subset.

### Feature Comparison

```text
results/comparison.csv
```

The comparison file contains basic audio features extracted from the generated samples.

---

## Audio Feature Comparison

The following audio features were used for comparison:

| Feature            | Meaning                                   |
| ------------------ | ----------------------------------------- |
| Duration           | Length of generated audio                 |
| RMS Energy         | Average loudness/energy of the signal     |
| Spectral Centroid  | Brightness of the sound                   |
| Zero Crossing Rate | Frequency of sign changes in the waveform |

These features provide a basic quantitative comparison between the pre-trained and fine-tuned outputs.

---

## Observations

After fine-tuning, the generated outputs show noticeable differences in texture and timbre compared to the original pre-trained samples.

Since NSynth contains isolated instrument-note recordings, the fine-tuned model tends to generate outputs that are more instrument-note-like and timbre-focused. This shows that the fine-tuning dataset has a direct influence on the characteristics of generated audio.

The pre-trained MusicGen model produces more general music-like outputs, while the fine-tuned model reflects the properties of the NSynth dataset more strongly.

---

## How to Run

To reproduce the project:

1. Open the notebook in Google Colab.
2. Select a GPU runtime.
3. Run the setup and installation cells.
4. Prepare the NSynth subset.
5. Generate baseline samples using the pre-trained MusicGen model.
6. Fine-tune MusicGen-small using AudioCraft.
7. Export the fine-tuned model.
8. Generate fine-tuned samples.
9. Compare pre-trained and fine-tuned samples.
10. Download the final results.

The full implementation is available in:

```text
notebook/Generative_AI_for_Music_MusicGen_NSynth.ipynb
```

---

## Requirements

The main libraries used are:

```text
torch
torchaudio
audiocraft
librosa
pandas
numpy
soundfile
matplotlib
dora-search
```

---

## Model Weights

The exported fine-tuned model contains:

```text
state_dict.bin
compression_state_dict.bin
```

These files are not uploaded directly to GitHub because they are large. They are included separately in the submitted results zip file or can be shared through an external drive link if required.

---

## Conclusion

This project demonstrates the complete workflow of fine-tuning a pre-trained generative music model. It provides hands-on experience with MusicGen, AudioCraft, text-conditioned generation, model fine-tuning, audio sample generation, and feature-based comparison.

The experiment shows that fine-tuning changes the generated audio characteristics and that the choice of dataset strongly affects the final generation style and quality.
