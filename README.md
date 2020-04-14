# SledgeDistillery
# BIS Dev team application. Development Dudes. 
# Title: Sledge Distillery Verification Application
# Developed by: Devlopment Dudes (Tim O'Reily, Loren Earl, Zaed Yousuf, Patrick Reigel)

# Purpose: To fulfill the need for Sledge Distillery to better document customer history in order to better comply with Texas State regulations. 

# Description: The applicaiton will verify/deny customer's request to purchase based on cross referencing a database containing their purchase history. 

from tkinter import *
from tkinter import ttk


class SledgeGui:
    def __init__(self,master):
        self.master = master
        master.title = "Title"

        self.label = Label(master, text="Sledge Distillery",width=40, font=("Times New Roman",20)).grid()

        self.label = Label(master, text=" ").grid(row=2)

        self.label = Label(master, text="ID Type:",font=("Times New Roman",15)).grid(row=3)

        idType = ttk.Combobox(master, value=['Driver License','State ID']).grid(row=4)
        
        

root = Tk()
my_Gui = SledgeGui(root)
root.mainloop()
 
