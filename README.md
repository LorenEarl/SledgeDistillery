# SledgeDistillery
# BIS Dev team application. Development Dudes. 
# Title: Sledge Distillery Verification Application
# Developed by: Devlopment Dudes (Tim O'Reily, Loren Earl, Zaed Yousuf, Patrick Reigel)

# Purpose: To fulfill the need for Sledge Distillery to better document customer history in order to better comply with Texas State regulations. 

# Description: The applicaiton will verify/deny customer's request to purchase based on cross referencing a database containing their purchase history. 
#Begin

from tkinter import *
from tkinter import ttk


#ALl possible state ID Abbreviations 
States = ['AL','AK','AZ','AR','CA','CO','CT','DE','FL','GA','HI','ID','IL','IN','IA','KS','KY','LA','ME','MD','MA','MI','MN','MS','MO','MT','NE','NV','NH','NJ','NM','NY','NC','ND','OH','OK','OR','PA','RI','SC','SD','TN','TX','UT','VT','VA','WA','WV','WI','WY']
#purchase options
Options = ['One [1] small bottle (750ml)','Two [2] small bottles (1500ml)','One [1] large bottle (1500ml)']
#Initialize variable used to store user entered ID number
IDNUmber = ""
SelectedState = ""

#Fairly obvious, this creates the opening window for user input
class FirstWindow:
    def __init__(self,master):
        
        self.master = master
        
        master.configure(bg='orange')

        self.label = Label(master, text="Sledge Distillery Verification",width=40, font=("Times New Roman",20),bg='orange').grid(row=1)

        self.label = Label(master, text=" ",bg='orange').grid(row=2)

        self.label = Label(master, text="ID State:",bg='orange').grid(row=3)

        self.combo = ttk.Combobox(master, value=States).grid(row=4)
        SelectedState = self.combo

        self.label = Label(master, text=" ",bg='orange').grid(row=5)
         
        self.label = Label(master, text="Enter ID Number:",bg='orange').grid(row=6)

        self.entry = Entry(master, textvariable = IDNUmber).grid(row=7)

        self.label = Label(master, text=" ",bg='orange').grid(row=8)

        self.label = Label(master, text="Select Purchase Volume: ",bg='orange').grid(row=9)

        self.combo = ttk.Combobox(master, value=Options, width = 25).grid(row=10)

        self.label = Label(master, text="*According to Texas State Law, Sledge Distillery can only sell (1500ml) of liquour to each customer in any 30-day period. Receive your verification here for your purchase*",wraplength=500, font=("Helvetica",8,'bold'),bg='orange').grid(row=11)

        self.label = Label(master, text=" ",bg='orange').grid(row=12)

        self.button = Button(master, text="Verify",command=Verify).grid(row=13,sticky=NE)


def Verify():
    #Run the verification, if the ID passes, set the text values (like result Title) to the values that would create the appropriate window. If it fails, vice versa.
    #All logic and connection should take place in this function, it is the command of the verify button. 
    global resultTitle 

    PopUp()



# This function created the second popup, all logic and connection should take place in Verify() function
def PopUp():
    resultTitle = "test"

    Second = Tk()

    Second.configure(bg='orange')

    Second.label = Label(Second, text=resultTitle ,width=30, font=("Times New Roman",15),bg='orange').grid(row=1)

    Second.label = Label(Second, text = " ",bg='orange').grid(row=2)

    Second.label = Label(Second, text = "Approved!", font = 15, bg = 'Orange').grid(row=3)


    print("Verification Complete...")

#Runs Guis

root = Tk()
my_Gui = FirstWindow(root)
root.mainloop()
 

#End
