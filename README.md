# Google Cloud speech-to-text video transcribe subtitle generator

This script converts a video file to an audio file, transcribe the audio file with Google Cloud Platform speech-to-text API, and generates the result into .SRT, .JSON, .TXT file formats.


## Requirements

- Git, Python 3.7 and ffmpeg installed on your system.

- A Google Cloud project with billing enabled.

- A service account with the right to use Speech-to-Text API.

-  Download the service account credentials as `credentials.json`.

-  Install the requirements:

    ```
    pip3 install -r requirements.txt
    ```

- Confugure the `.env` file.


## Usage

```
python3 main.py example.wav en-US
```


## TODO

- Handle non-English languages results


## Reference

- [Generate SRT File (Subtitles) using Google Cloud’s Speech-to-Text API](https://github.com/darshan-majithiya/Generate-SRT-File-using-Google-Cloud-s-Speech-to-Text-API)

- [GoogleCloudPlatform/community](https://github.com/GoogleCloudPlatform/community/blob/master/tutorials/speech2srt/speech2srt.py)