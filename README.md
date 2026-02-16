# [Colab Link:](https://colab.research.google.com/drive/1ieUu0-CkOj6YDPcTJh8_7aV_d5wxOV_z?usp=sharing) 

#  YouTube Technical Tutorial Note-Taker

An automated, GPU-accelerated NLP pipeline that generates highly structured, timestamped study notes from technical YouTube tutorials. 

Instead of relying on YouTube's flawed auto-captions, this project downloads the audio directly, transcribes it locally using OpenAI's Whisper, and leverages a Causal Language Model (Qwen 2.5) to extract code syntax and core concepts into a beautifully formatted Markdown cheat sheet.

##  Features
* **Pristine Transcription:** Uses `yt-dlp` to extract audio and `faster-whisper` for highly accurate, locally-run transcription that handles proper nouns and punctuation beautifully.
* **Smart Time-Chunking:** Groups the transcript into 90-second blocks to ensure dense, technical details aren't lost in the summarization process.
* **Syntax Extraction:** Instructs `Qwen2.5-3B-Instruct` to hunt down and format specific programming concepts, keywords, and code blocks rather than just writing generic summaries.
* **Interactive Export:** Automatically renders the notes in the Colab interface and provides a clickable HTML button to download a `.md` file.
* **Clickable Timestamps:** Every section in the generated Markdown includes a deep-link that jumps straight to that exact second in the original YouTube video.

##  Tech Stack
* **Audio Processing:** `yt-dlp`
* **Transcription:** `faster-whisper` (CTranslate2 optimized for CUDA)
* **LLM Engine:** `Qwen/Qwen2.5-3B-Instruct` via Hugging Face `transformers`
* **Compute:** PyTorch (configured for `float16` execution on Nvidia T4 GPUs)

##  How to Run
This project is built to run effortlessly in Google Colab, taking advantage of the free T4 GPU tier.

1. Open the `YTSummariser.ipynb` notebook in Google Colab.
2. Go to **Runtime > Change runtime type** and ensure the Hardware Accelerator is set to **T4 GPU**.
3. Run **Cell 1** to install the required dependencies (`yt-dlp`, `faster-whisper`, `transformers`, etc.).
4. Run the remaining cells to load the Whisper and Qwen models into VRAM.
5. In the final execution cell, paste any YouTube tutorial URL when prompted.
6. Click **Download Notes (.md)** when the generation finishes!

##  Notes on Colab Widgets
If you are viewing this notebook directly on GitHub, you may see rendering errors regarding `application/vnd.jupyter.widget-state+json`. This is a known GitHub limitation with the interactive loading bars (`tqdm`) used by Hugging Face. The code itself is perfectly intact—just open it in Colab to run!

---
**Author:** Amartya Chaudhuri  
**Contact:** amartyac@usc.edu
