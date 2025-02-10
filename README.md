#Video Dowloader Beta 0.1 Python Script

import pytube
import os
from urllib.parse import urlparse

def download_video(url, title):
    yt = pytube.YouTube(url)
    stream = yt.streams.first()
    filename = f"{title}.mp4"
    print(f"Downloading {filename}...")
    stream.download(filename=filename)

def main():
    url = input("Enter the YouTube video URL: ")
    title = input("Enter a new title for the downloaded video (optional, default is the original title): ")

    if not title:
        yt = pytube.YouTube(url)
        title = yt.title

    download_video(url, title)

if __name__ == "__main__":
    main()
