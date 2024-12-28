# voice-cloning

---

# **Voice Cloning with Fine-Tuning on Kaggle**

This project demonstrates how to perform voice cloning using a speaker-adaptive TTS model from [Coqui TTS](https://github.com/coqui-ai/TTS). The notebook allows you to preprocess audio, fine-tune the model on a custom voice dataset, and generate realistic voice clones.

---

## **Features**
- Preprocessing audio files for training and testing.
- Fine-tuning the TTS model using a custom dataset (segmented audio clips and transcriptions).
- Voice cloning with high-quality text-to-speech generation.

---

## **Setup Instructions**

### **Step 1: Environment Setup**
Install the required dependencies:
```bash
!pip install TTS librosa pydub soundfile --quiet
```

### **Step 2: Data Preparation**
1. Upload a clear audio sample (minimum of 3 minutes) as a WAV file.
2. Segment the audio into smaller clips (5–15 seconds) using the script provided in the notebook.
3. Create a `metadata.csv` file with transcriptions for each clip in the format:
   ```
   clip_1.wav|Transcription of clip 1
   clip_2.wav|Transcription of clip 2
   ```

### **Step 3: Fine-Tuning**
Run the fine-tuning script in the notebook:
```bash
!python TTS/bin/train_tts.py --config_path=TTS/configs/tacotron2.json --dataset_path=./dataset
```

---

## **Project Workflow**

1. **Preprocessing**: 
   - Audio is downsampled to 16 kHz and converted to mono.
   - Audio clips are segmented for fine-tuning.

2. **Dataset Preparation**:
   - Segmented audio clips and corresponding transcriptions are organized into a dataset directory.

3. **Fine-Tuning**:
   - The pre-trained TTS model is fine-tuned on your dataset to adapt it to your voice.

4. **Voice Cloning**:
   - Generate audio outputs using the fine-tuned model and test various texts.

---

## **Results**
After fine-tuning, the model generates realistic audio in the speaker’s cloned voice. Test results can be evaluated using the generated WAV files.

---

## **Folder Structure**
```plaintext
├── dataset/
│   ├── wavs/
│   │   ├── clip_1.wav
│   │   ├── clip_2.wav
│   │   └── ...
│   └── metadata.csv
├── outputs/
│   ├── cloned_voice.wav
│   ├── fine_tuned_output.wav
│   └── ...
├── TTS/
│   ├── configs/
│   ├── output/
│   └── ...
```

---

## **To-Do**
- Improve the transcription quality for better fine-tuning results.
- Experiment with different TTS models to enhance cloning accuracy.
- Extend to multi-lingual or emotion-adaptive models.

---

## **Acknowledgments**
- [Coqui TTS](https://github.com/coqui-ai/TTS): A powerful text-to-speech library.
- [Librosa](https://librosa.org/): For audio preprocessing.
- [Pydub](https://github.com/jiaaro/pydub): For audio segmentation.

