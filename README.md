# Alarmclock_project2
import tkinter as tk
from tkinter import *
from tkinter import messagebox
import os, time, winsound

def createWidgets():

    label1 = Label(root,text="Enter the time in hh:mm - ")
    label1.grid(row=0, column=0, padx=5, pady=5)
    
    global entry1
    entry1 = Entry(root, width=15)
    entry1.grid(row=0,column=1)

    label2 = Label(root,text="Enter the meesage of alarm: ")
    label2.grid(row=0, column=0, padx=5, pady=5)

    global entry2
    entry2 = Entry(root, width=15)
    entry2.grid(row=1, column=1)

    but = Button(root, text="Submit", width=10, command=submit)
    but.grid(row=2, column=1)

    global label3 
    label3 = Label(root, text="")
    label3.grid(row=3, column=0)

def message1():

    global entry1, label3
    Alarmtimelabel = entry1.get()
    label3.config(text="The Alarm is counting....")
    messagebox.showinfo("Alarm clock", f"The Alarm time is:{Alarmtimelabel}")

def submit():

    global entry1, entry2, label3
    Alarmtime = entry1.get()
    message1()
    currenttime = time.strftime("%H:%M")
    alarmmessage = entry2.get()
    print(f"The Alarm time is: {Alarmtime}")
    while Alarmtime != currenttime:
        currenttime = time.strftime("%H:%M")
        time.sleep(1)
    if Alarmtime == currenttime:
        print("Playing Alarm Sound....")
        winsound.PlaySound("*", winsound.SND_ASYNC)
        label3.config(text="Alarm Sound Playing>>>>")
        messagebox.showinfo("Alarm Message", f"The Message is: {alarmmessage}")



root = tk.Tk()
root.title("Alarm clock")
root.geometry("400x150")

createWidgets()

root.mainloop()

