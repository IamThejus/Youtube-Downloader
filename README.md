# Youtube-Downloader
This is an app for downloading youtube videos

Download the zip and extract....
Its a smiple .py to .exe conversion.
Open the folder and open dist,then you can find youtube_downloader.exe.

If you want the source code its given below.

# Source Code

# Import Modules

from pytube import YouTube
from tkinter import*
from tkinter import messagebox


# Functions for widgets

def yt_download(re,path,link,name):
    try:
        yt = YouTube(link)  
        yt.streams.filter(res=re,progressive = True, file_extension = "mp4").first().download(output_path = path, filename =name+".mp4")
        return True
    except:
        return False
    
def download_in_360():
    path=en_location.get()
    link=en_link.get()
    name=en_name.get()
    re='360p'
    yt_download(re,path,link,name)
    if yt_download(re,path,link,name)==True:
        messagebox.showinfo('Task Complete','The file '+name+'\nhas been downloaded')
    else:
        messagebox.showinfo('An Error Occured','Sorry an error occured.\nPlease try again .')

def download_in_720():
    path=en_location.get()
    link=en_link.get()
    name=en_name.get()
    re='720p'
    yt_download(re,path,link,name)
    if yt_download(re,path,link,name)==True:
        messagebox.showinfo('Task Complete','The file '+name+'\nhas been downloaded')
    else:
        messagebox.showinfo('An Error Occured','Sorry an error occured.\nPlease try again .')
    
def info():
    messagebox.showinfo('INFO','The YouTube Downloader is downloader which can download videos in 360p and 720p.Its free and does not contain ads.Its created by Thejus A.\n\nHope you like it :)')

# Creating Window

window=Tk()
window.geometry('360x130')
window.title('YouTube Video Downloader')

# Creating Widgets

lab_link=Label(window,text='Link')
lab_name=Label(window,text='Name')
lab_location=Label(window,text='Location')
en_link=Entry(window,width=30)
en_name=Entry(window,width=30)
en_location=Entry(window,width=30)
download_360=Button(window,text='Download in 360p',command=download_in_360,bg='green')
download_720=Button(window,text='Download in 720p',command=download_in_720,bg='orange')
info=Button(window,text='Info',command=info,bg='light blue',font='raleway')

# Postion For Widgets

lab_link.grid(column=1,row=1)
lab_name.grid(column=1,row=2)
lab_location.grid(column=1,row=3)
en_link.grid(column=2,row=1)
en_name.grid(column=2,row=2)
en_location.grid(column=2,row=3)
download_360.grid(column=1,row=4)
download_720.grid(column=1,row=5)
info.grid(column=2,row=4)


window.mainloop()

# Important Modules To Download

pytube

# For Pytube installing it using cmd

pip3 install pytube
