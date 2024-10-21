# Voice Assistant Project: Multimodal AI with LLaVA and Whisper

Unlock the potential of AI to create your very own voice assistant with our project! This project combines cutting-edge technologies to build a multimodal voice assistant capable of understanding both images and text, and converting speech to text and text to speech.

The voice assistant leverages:
- **LLaVA 1.5 7B**: A large multimodal language model for image and text understanding.
- **Whisper by OpenAI**: A powerful model for accurate speech-to-text conversion.
- **Gradio**: An interactive web interface for real-time use.
- **gTTS**: Google’s Text-to-Speech library to convert the generated text into realistic speech.

## Installation

Follow these steps to install the necessary dependencies and run the project locally.

1. Clone the repository:
    ```bash
    git clone https://github.com/rafid29mehda/AI-powered-Voice-Assistant-App.git
    cd AI-powered-Voice-Assistant-App
    ```

2. Install the required Python packages:
    ```bash
    pip install -q -U transformers==4.37.2
    pip install -q bitsandbytes==0.41.3 accelerate==0.25.0
    pip install -q git+https://github.com/openai/whisper.git
    pip install -q gradio
    pip install -q gTTS
    ```

3. Make sure you have **FFmpeg** installed for audio processing (required by `gTTS`):
    ```bash
    sudo apt-get install ffmpeg
    ```

## Features

- **Speech-to-Text**: Converts audio input into text using OpenAI's Whisper model.
- **Image Description**: Describes an image based on text input using the LLaVA 1.5 model.
- **Text-to-Speech**: Converts the generated text back into speech using gTTS.
- **Gradio Interface**: An interactive, web-based interface that allows users to upload an image and audio, and receive a response both in text and audio formats.

## How it Works

1. **Upload Image**:
   - First, the user uploads an image into the app.

2. **Voice Query**:
   - After uploading the image, the user can ask questions or request explanations about the image by providing voice input. The **Whisper model** transcribes the voice input into text.

3. **Image-to-Text Generation**:
   - Before generating the final response, the app first uses **LLaVA** to generate a description of the image (image-to-text).

4. **Contextual Image Explanation**:
   - Based on the speech input (now converted to text), the app explains the image according to the user’s query.

5. **Text-to-Speech**:
   - The generated explanation is then converted back into speech using the **gTTS** library, and provided as an audio response to the user.

6. **Gradio Interface**:
   - The entire interaction happens through a user-friendly web interface powered by **Gradio**, where users can upload an image, record voice input, and receive both text and audio responses.
  

---

