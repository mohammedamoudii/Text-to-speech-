# Text-to-Speech Conversion

This project demonstrates how to convert text to speech using Python's `gtts` (Google Text-to-Speech) library and play the audio using `pygame`. The script converts a given text to speech and plays it back through the system's audio output.

## Prerequisites

Before running the script, you need to install the required Python libraries. You can do this using `pip`:

```bash
pip install gtts
pip install pygame
```

## How It Works
- Text-to-Speech Conversion: The gtts library is used to convert text into an audio file.
- In-Memory Audio Handling: The io.BytesIO class is used to handle audio data in-memory without creating temporary files.
- Audio Playback: The pygame library's mixer module is used to load and play the audio data.

## script
```
import os
from gtts import gTTS
import pygame
import io

# The text that you want to convert to audio
mytext = 'This is a text to speech file yay we made it !'

# Language in which you want to convert
language = 'en'

# Convert text to speech
myobj = gTTS(text=mytext, lang=language, slow=False)

# Use BytesIO to handle the audio data in-memory
audio_data = io.BytesIO()
myobj.write_to_fp(audio_data)
audio_data.seek(0)

# Initialize the mixer module
pygame.mixer.init()

# Load the audio data from BytesIO
pygame.mixer.music.load(audio_data, 'mp3')

# Play the loaded audio data
pygame.mixer.music.play()

# Keep the program running long enough to hear the audio
while pygame.mixer.music.get_busy():
    continue
```
