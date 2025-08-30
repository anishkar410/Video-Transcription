# Video-Transcription
A state-of-the-art, production-ready system for converting video and audio into accurate, clean transcripts and subtitles. This pipeline combines the power of OpenAI's Whisper with advanced audio preprocessing and intelligent text post-processing to deliver studio-quality results, even from noisy recordings.
# ✨ Features
High-Accuracy Transcription: Leverages the best available faster-whisper and Whisper large-v3 model for unmatched multilingual speech recognition.

Intelligent Audio Enhancement: Automatically normalizes audio levels and applies noise reduction to improve input quality.

Voice Activity Detection (VAD): Uses Silero VAD to detect and only transcribe speech, ignoring silence and background noise.

Advanced Post-processing: Proprietary algorithms to remove repetitions, fix spacing (especially for Hindi/English mixes), and correct common speech-to-text errors.

Multi-Input Support: Accepts direct video/audio file uploads or YouTube URLs.

Professional Outputs: Generates a clean transcript (.txt), precise subtitles (.srt), and detailed word-level timestamps (.json).
# 🛠️ Tech Stack & Architecture
Core Model: faster-whisper (with CTranslate2) for fast, efficient inference. Falls back to openai-whisper for compatibility.

Preferred Model: large-v3 for highest accuracy. Automatically selects medium on CPU for optimal performance.

Audio Processing: FFmpeg, librosa, pydub, and noisereduce.

Text Post-processing: Custom algorithms using Jaccard similarity for deduplication and rule-based filters for cleanup.

Hardware Optimization: Automatically uses GPU (CUDA) with int8_float16 quantization for speed, or CPU with int8.
# 🧠 How It Works
The pipeline follows a meticulous multi-stage process:

Ingestion: Input is converted to a standardized 16kHz mono WAV file.

Pre-processing: Audio is normalized to -23 LUFS and processed with a noise reduction algorithm.

Transcription: The enhanced audio is transcribed by Whisper using Beam Search and VAD for high accuracy.

Post-processing: The raw text is cleaned by:

Removing repetitive sentences and words using similarity matching.

Applying context-aware corrections (e.g., "u" -> "you").

Fixing spacing issues in multilingual text.

Export: The final results are compiled into user-friendly formats.
# 🚀 Usage
Running the project is straightforward:

Open the Video_Transcription.ipynb notebook in Google Colab.

Run the initial setup cells to install all dependencies.

Choose your input method when prompted:

1) to upload a video/audio file from your computer.

2) to paste a YouTube URL.

Wait for the pipeline to process the audio and generate the transcription.

Download the resulting .txt, .srt, and .json files directly from Colab.

The system automatically handles audio extraction, enhancement, transcription, and cleanup.
# 🙏 Acknowledgments
OpenAI for the powerful Whisper models.

The authors of faster-whisper for their incredible optimization work.

The Silero VAD team for their best-in-class voice activity detection model.

