#YouTube Video Downloader
A streamlined desktop application built with Python, Tkinter, and Pytube, designed to download YouTube videos in the highest available resolution.
The tool provides a clean and intuitive interface, making video downloads accessible to both technical and non-technical users.

🚀Features
Modern Tkinter-based GUI

High-resolution video download using Pytube

Directory selection for flexible file storage

Real-time success confirmation via modal prompts

Lightweight and easy to run on any system with Python installed

📸Screenshots
Application Interface

<img width="1024" height="1536" alt="INTERFACE" src="https://github.com/user-attachments/assets/31e9cff5-50a5-43f9-a4d5-12a546744c6f" />

Download Confirmatio
<img width="1024" height="1536" alt="COMPLETE" src="https://github.com/user-attachments/assets/babe8d5a-f324-4e14-ad24-dd748427089a" />
n

🛠️Tech Stack
Python 3.x
Tkinter for the graphical user interface
Pytube for handling YouTube video streams

📂Project Structure
.
├── youtube_downloader.py
├── assets/
│   ├── home_screen.png
│   └── success_message.png
└── README.md
▶️Running the Project:-
1. Install Dependencies
pip install pytube
2. Start the Application
python youtube_downloader.py
🧩Source Code

import tkinter as tk
from tkinter import *
from pytube import YouTube
from tkinter import messagebox, filedialog
 
def Widgets():
    head_label = Label(root, text="YouTube Video Downloader Using Tkinter",
                       padx=15, pady=15, font="SegoeUI 14",
                       bg="greenyellow", fg="purple")
    head_label.grid(row=1, column=1, pady=10, padx=5, columnspan=3)

    link_label = Label(root, text="YouTube link :", bg="salmon",
                       pady=5, padx=5)
    link_label.grid(row=2, column=0, pady=5, padx=5)

    root.linkText = Entry(root, width=35, textvariable=video_Link,
                          font="Arial 14")
    root.linkText.grid(row=2, column=1, pady=5, padx=5, columnspan=2)

    destination_label = Label(root, text="Destination :", bg="salmon",
                              pady=5, padx=9)
    destination_label.grid(row=3, column=0, pady=5, padx=5)

    root.destinationText = Entry(root, width=27, textvariable=download_Path,
                                 font="Arial 14")
    root.destinationText.grid(row=3, column=1, pady=5, padx=5)

    browse_B = Button(root, text="Browse", command=Browse,
                      width=10, bg="firebrick2", relief=GROOVE)
    browse_B.grid(row=3, column=2, pady=1, padx=1)

    Download_B = Button(root, text="Download Video", command=Download,
                        width=20, bg="orange", pady=10, padx=15,
                        relief=GROOVE, font="Georgia, 13")
    Download_B.grid(row=4, column=1, pady=20, padx=20)
 
def Browse():
    download_Directory = filedialog.askdirectory(
        initialdir="YOUR DIRECTORY PATH", title="Save Video")
    download_Path.set(download_Directory)
 
def Download():
    Youtube_link = video_Link.get()
    download_Folder = download_Path.get()
    getVideo = YouTube(Youtube_link)
    videoStream = getVideo.streams.get_highest_resolution()
    videoStream.download(download_Folder)
    messagebox.showinfo("SUCCESSFULLY",
                        "DOWNLOADED AND SAVED IN\n" + download_Folder)
 
root = tk.Tk()
root.geometry("520x520")
root.resizable(False, False)
root.title("YouTube Video Downloader")
root.config(background="darkorchid1")
 
video_Link = StringVar()
download_Path = StringVar()

Widgets()
root.mainloop()
