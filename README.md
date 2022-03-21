# Google Cloud speech-to-text video transcribe subtitle generator

This script converts a video file to an audio file, transcribe the audio file with Google Cloud Platform speech-to-text API, and generates the result into .SRT, .JSON, .TXT file formats.

## Requirements

- Git, Python 3.7 and ffmpeg installed on your system.

- A Google Cloud project with billing enabled.

- A service account with the right to use Speech-to-Text API.

- Download the service account credentials as `credentials.json`. Example:

    ```
    {
    "type": "service_account",
    "project_id": "EXAMPLE",
    "private_key_id": "EXAMPLE",
    "private_key": "EXAMPLE",
    "client_email": "EXAMPLE",
    "client_id": "EXAMPLE",
    "auth_uri": "https://accounts.google.com/o/oauth2/auth",
    "token_uri": "https://oauth2.googleapis.com/token",
    "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
    "client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/EXAMPLE"
    }
    ```

-  Install the requirements:

    ```
    pip3 install -r requirements.txt
    ```

- Confugure the `.env` file. Example:

    ```
    # Google storage bucket name
    BUCKET_NAME = "bucket_name"

    # Maximum characters in each single line in the SRT subtitle file
    MAX_CHARS = 60

    # Location where your ffmpeg binary file is put
    FFMPEG_LOCATION = "C:\\\Apps\\ffmpeg\\bin\\ffmpeg.exe"
    FFPROBE_LOCATION = "C:\\\Apps\\ffmpeg\\bin\\ffprobe.exe"
    ```


## Usage

```
python3 main.py example.mp4 en-US
```

## Explanation of functions

`upload_blob()` - Uploads the media file to the Google Storaege bucket.

`video_info()` - Returns number of channels, bit rate, and sample rate of the video, extracted by running `ffmpeg`. These parameters are required by Google's API.

`video_to_audio()` - Converts video into audio, and upload the audio to the Google Storaege bucket.

`long_running_recognize()` - Transcribes the audio by calling Google Cloud API.

`break_sentences()` - Breaks sentences by punctuations and maximum sentence length. This ensures that in the video subtitle, the sentence won't be too long.


## TODO

- Handle non-English languages results


## Reference

- [Generate SRT File (Subtitles) using Google Cloud’s Speech-to-Text API](https://github.com/darshan-majithiya/Generate-SRT-File-using-Google-Cloud-s-Speech-to-Text-API)

- [GoogleCloudPlatform/community](https://github.com/GoogleCloudPlatform/community/blob/master/tutorials/speech2srt/speech2srt.py)