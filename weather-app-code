import tkinter as tk
import requests
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from bs4 import BeautifulSoup
import pandas as pd
import glob
import sys
import os
import time
from tkinter import font
import tkinter.messagebox
from tkinter import filedialog

from pygame import mixer

H = 500
W = 600

def browse_file():
    global filename
    filename = filedialog.askopenfilename()
    
def about_us():
    tkinter.messagebox.showinfo('About Weather', 'This is a Weather App build using Python Tkinter by @vindesai')
    

def f1(entry):
    try:
        city_name = entry
        page = requests.get('https://www.google.com/search?source=hp&ei=DFZGX-3wE4SFmgeFtJ6oAQ&q=Weather+'+city_name)
        page_source = page.content
        soup = BeautifulSoup(page_source)
        t1 = soup.find('div', attrs={'class':"BNeawe tAd8D AP7Wnd"})
        t2 = soup.find('div', attrs={'class':"BNeawe iBp4i AP7Wnd"})
        t3 = soup.find('span', attrs={'class':"BNeawe tAd8D AP7Wnd"})
        L = (t1.text).split('\n')
        #print('\033[1m' + 'Place: '+ '\033[0m',t3.text)
        #print('\033[1m' + 'Time: '+ '\033[0m',L[0])
        #print( '\033[1m' + 'Weather Condition: ' + '\033[0m',L[1])
        #print('\033[1m' + 'Temparature: '+ '\033[0m',t2.text)
        f = 'Place: '+  t3.text + '\n' + 'Time: '+ L[0] + '\n' + 'Weather Condition: ' + L[1]+'\n' + 'Temparature: '+ t2.text
        label['text'] = f
    except:
        label['text'] = 'Error Occured. Please Try Again !!'


root = tk.Tk()

root.title("Weather App")
root.iconbitmap("Bokehlicia-Pacifica-Weather.ico")


canvas = tk.Canvas(root, height = H, width = W)
canvas.pack()

bg_image = tk.PhotoImage(file='landscape.png')
bg_label = tk.Label(root,image = bg_image)
bg_label.place(x=0,y=0, relwidth = 1, relheight = 1)

frame = tk.Frame(root, bg='#80c1ff' , bd = 5)
frame.place(relx = 0.5, rely = 0.1, relwidth = 0.75, relheight = 0.1, anchor='n')

entry = tk.Entry(frame, font = ('Courier',12))
entry.place(relwidth = 0.65, relheight = 1)
#entry.insert(1,'Enter Name or PinCode of Place: ')

button = tk.Button(frame, text = 'Get Weather', font = ('Courier',10), bg = 'gray', command = lambda: f1(entry.get()))
button.place(relx = 0.7, relwidth = 0.3, relheight = 0.9)

lower_frame = tk.Frame(root, bg='#80c1ff' , bd = 12)
lower_frame.place(relx = 0.5, rely = 0.25, relwidth = 0.75, relheight = 0.6, anchor='n')

label = tk.Label(lower_frame , font = ('Courier',12), anchor = 'nw', justify = 'left', bd = 4 )
label.place(relwidth = 1, relheight = 1)

root.mainloop()
