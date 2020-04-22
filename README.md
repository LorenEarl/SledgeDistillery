# SledgeDistillery
# BIS Dev team application. Development Dudes. 
# Title: Sledge Distillery Verification Application
# Developed by: Devlopment Dudes (Tim O'Reily, Loren Earl, Zaed Yousuf, Patrick Reigel)

# Purpose: To fulfill the need for Sledge Distillery to better document customer history in order to better comply with Texas State regulations. 

# Description: The applicaiton will verify/deny customer's request to purchase based on cross referencing a database containing their purchase history. 
#Begin

from tkinter import *
from tkinter import ttk


#ALl possible state ID Abbreviations, loaded into the FirstWindow Combobox 1 values
States = ['AL','AK','AZ','AR','CA','CO','CT','DE','FL','GA','HI','ID','IL','IN','IA','KS','KY','LA','ME','MD','MA','MI','MN','MS','MO','MT','NE','NV','NH','NJ','NM','NY','NC','ND','OH','OK','OR','PA','RI','SC','SD','TN','TX','UT','VT','VA','WA','WV','WI','WY']

#purchase options, loaded into the FirstWindow Combobox 2 values
Options = ['One [1] small bottle (750ml)','Two [2] small bottles (1500ml)','One [1] large bottle (1500ml)']

#Initialize variable used to store user entered ID number
IDNUmber = ""
SelectedState = ""
SelectedVolume = ""

#Fairly obvious, this creates the opening window for user input
class FirstWindow:
    def __init__(self,master):
        
        self.master = master
        
        master.configure(bg='orange')

        l1 = Label(master, text="Sledge Distillery Verification",width=40, font=("Times New Roman",20),bg='orange').grid(row=1)

        space1 = Label(master, text=" ",bg='orange').grid(row=2)

        l2 = Label(master, text="ID State:",bg='orange').grid(row=3)

        #This is the combobox where user will select the associated ID State
        global combo1
        combo1 = ttk.Combobox(master, value=States)
        combo1.grid(row=4)

        space2 = Label(master, text=" ",bg='orange').grid(row=5)
         
        l3 = Label(master, text="Enter ID Number:",bg='orange').grid(row=6)

        #Entry Variable where users will enter ID number
        global IDEntry
        IDEntry = Entry(master)
        IDEntry.grid(row=7)

        space3 = Label(master, text=" ",bg='orange').grid(row=8)

        l4 = Label(master, text="Select Purchase Volume: ",bg='orange').grid(row=9)

        #This is the combobox where users will select their purchase volume
        global combo2
        combo2 = ttk.Combobox(master, value=Options, width = 25)
        combo2.grid(row=10)

        l5 = Label(master, text="*According to Texas State Law, Sledge Distillery can only sell (1500ml) of liquour to each customer in any 30-day period. Receive your verification here for your purchase*",wraplength=500, font=("Helvetica",8,'bold'),bg='orange').grid(row=11)

        space4 = Label(master, text=" ",bg='orange').grid(row=12)

        verifyButton = Button(master, text="Verify",command=Verify).grid(row=13,sticky=NE)
       
        

def Verify():
    #Run the verification, if the ID passes, set the text values (like result Title) to the values that would create the appropriate window. If it fails, vice versa.
    #All logic and connection should take place in this function, it is the command of the verify button. 
    
    #These variables get the inpur the user entered in the first screen, use these when verifying 
    IDNUmber = IDEntry.get()
    SelectedState = combo1.get()
    SelectedVolume = combo2.get()
    s = SelectedVolume.split('(')
    s2 = s[1].split('m')
    #this is the int number that tells how much volume was selected
    volumeNumber = int(s2[0])

    global outcome
    global messageText

    #Set these variables if the ID is approved
    outcome = 'Approved!'
    messageText = 'Take the printed receipt below and present at the time of purchase.'


    #Set these variables if the ID is NOT approved
    #outcome = 'We apologize.'
    #messageText = 'Test message'

    #Runs the pop up function
    PopUp()
    
    #prints selected inputs
    print('ID State is: ' + SelectedState)
    print('ID Number is: ' + IDNUmber)
    print('Volume is:', volumeNumber)
    print("Verification Complete...")



# This function created the second popup, all logic and connection should take place in the above Verify() function
def PopUp():
    

    Second = Tk()

    Second.configure(bg='orange')

    Second.label = Label(Second, text="Verification Result" ,width=30, font=("Times New Roman",15),bg='orange').grid(row=1)

    Second.label = Label(Second, text = " ",bg='orange').grid(row=2)

    Second.label = Label(Second, text = outcome, font = 10, bg = 'Orange').grid(row=3)

    Second.label = Label(Second, text = ' ', bg = 'orange').grid(row=4)

    Second.label = Label(Second, text = messageText, font = 8, wraplength = 400, bg = 'Orange').grid(row=5)

    Second.label = Label(Second, text = ' ', bg = 'orange').grid(row=6)

    Second.button = Button(Second, text = 'Finish', command = Second.destroy ).grid(row=7,sticky = E)


   




#Runs Guis

root = Tk()
my_Gui = FirstWindow(root)
root.mainloop()
 

#End
