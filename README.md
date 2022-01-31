# OurCalculator
Calculator created do basic calculations

import tkinter as tk
from tkinter import filedialog, Text
import os
import tkinter.font as font
from tkinter.constants import BOTH, END, LEFT, RIGHT, TOP, Y
import math


#Defs
def add(x,y):
    print("Made it to the add")
    #print(str(x+y))
    global result
    result = int(x)+int(y)
def subtract(x,y):
    global result
    result = int(x)-int(y)
    print("Made it to the subtract")
def multiply(x,y):
    global result
    result = int(x)*int(y)
    print("Made it to multiply")
def divide(x,y):
     if int(x) >= int(y):
        global result
        result = (int(x)/int(y))
     else:
         print("Cannot Divide")
def square(x):
    global result
    result = int(x) * int(x)
def squareroot(x):
    if int(x) > 0:
        global result
        result = math.sqrt(int(x))
    else:
       result = "Cannot Square Root A Negative Number"
def modulo(x, y):
    global result
    result = int(x) % int(y)
def oppositeSign(x):
    global result
    result = int(x) * -1
                            # Numbers
def ZeroButtonClick(event):
    t3.insert(END, "0")
    #print("this works0")
def OneButtonClick(event):
    t3.insert(END, "1")
    #print("this works1")
def TwoButtonClick(event):
    t3.insert(END, "2")
    #print("this works2")
def ThreeButtonClick(event):
    t3.insert(END, "3")
    #print("this works1")
def FourButtonClick(event):
    t3.insert(END, "4")
    #print("this works4")
def FiveButtonClick(event):
    t3.insert(END, "5")
    #print("this works5")
def SixButtonClick(event):
    t3.insert(END, "6")
    #print("this works6")
def SevenButtonClick(event):
    t3.insert(END, "7")
   # print("this works7")
def EightButtonClick(event):
    t3.insert(END, "8")
    #print("this works8")
def NineButtonClick(event):
    t3.insert(END, "9")
    #print("this works9")
    #Functionality
def clearDisplayClick(event):
    t3.delete(0, 'end')
    t3.insert(END, "")
    global currentX
    global currentY
    global result
    currentY = 0
    currentX = 0
    result = 0
    #print("this worksClear")
def addButtonClick(event):
    global currentX                # Calls Current X as a Global Variable
    currentX = t3.get() #3         # Saves First Input to Current X
    print(currentX)                # Prints The Value To Output Just For Us To See
    t3.delete(0, 'end')            # Delete and Clears For The User
    t3.insert(END, "")
    print("this worksClearAdd")    # Prints A Checkpoint For Us, we Know it Works to this point
    global option                  # Calls Option as a Global Variable
    option = 1                     # Sets Option to 1
def subButtonClick(event):
    global currentX
    currentX = t3.get() #3
    print(currentX)
    t3.delete(0, 'end')
    t3.insert(END, "")
    print("this worksClearSub")
    global option
    option = 2
def multButtonClick(event):
    global currentX
    currentX = t3.get() #3
    print(currentX)
    t3.delete(0, 'end')
    t3.insert(END, "")
    print("this worksClearMult")
    global option
    option = 3
def divButtonClick(event):
    global currentX
    currentX = t3.get() #3
    print(currentX)
    t3.delete(0, 'end')
    t3.insert(END, "")
    print("this worksClearDiv")
    global option
    option = 4
def squButtonClick(event):
    global currentX
    currentX = t3.get() #3
    print(currentX)
    t3.delete(0, 'end')
    t3.insert(END, "")
    print("this worksClearSqu")
    global option
    option = 5
    optionPicker(option)
    returnResult()
def rootButtonClick(event):
    global currentX
    currentX = t3.get() #3
    print(currentX)
    t3.delete(0, 'end')
    t3.insert(END, "")
    print("this worksClearSquRoot")
    global option
    option = 6
    optionPicker(option)
    returnResult()
def modButtonClick(event):
    global currentX
    currentX = t3.get() #3
    print(currentX)
    t3.delete(0, 'end')
    t3.insert(END, "")
    print("this worksClearRoot")
    global option
    option = 7
def oppositeSignClick(event):
    global currentX
    currentX = t3.get() #3
    print(currentX)
    t3.delete(0, 'end')
    t3.insert(END, "")
    print("this worksClearOppositeSign")
    global option
    option = 8
    optionPicker(option)
    returnResult()
def equalButtonClick(event):               # Upon Equal Botton Being Clicked
    global currentY                        # Calls Current Y as a Global Variable
    currentY = t3.get()                    # Saves The Second Input to Current Y
    optionPicker(option)                   # Takes Us To The If Statement Below
    returnResult()
def optionPicker(argument):
    #print(option)
    global result
    if argument == 1:                      # Earlier We Made Global Option = 1
        add(currentX, currentY)            # Which Triggers The Add Function In Beginning w/ Parameters Earlier Set
    elif argument == 2:
        subtract(currentX, currentY)
    elif argument == 3:
        multiply(currentX, currentY)
    elif argument == 4:
        if int(currentY) == 0:
            result = "Error! Cannot divide by 0"
            returnResult()
        elif currentX >= currentY:
            divide(currentX, currentY)
        else:
            result = "Result less than 1 or not possible"
    elif argument == 5:
        square(currentX)
    elif argument == 6:
        squareroot(currentX)
    elif argument == 7:
        modulo(currentX, currentY)
    elif argument == 8:
        oppositeSign(currentX)
    else:
        print("That option is not available")
        result = "That option is not availabe"
        returnResult()
    print("I'm here")
    print(argument)
def returnResult():
   t3.delete(0, 'end')
   t3.insert(END, str(result))            # Returns Result to Display
# Memory
result = 0
currentX = 0
currentY = 0
option = 0
root = tk.Tk()
root.title("Calculator")
# Body/Frame of Calculator
canvas = tk.Canvas(root, height= 800, width= 500, bg= "#263D42")
canvas.pack()
frame = tk.Frame(root, bg= "#3E646E")
frame.place(relwidth=0.8, relheight=0.8, rely= 0.1, relx = 0.1)
bottomframe = tk.Frame(root)
bottomframe.pack( side = tk.BOTTOM )
# Titles
root.title("Calculator")
label = tk.Label(root, text = "Our Calculator", bg = "white", bd = 20, fg = "black", font = "Castellar")
label.place(relx = 0.5, rely = 0.2, anchor = 'center')
# Various Buttons
        # Numbers first
buttonFont1 = font.Font(family='Castellar', size= 25)  #only used for clear, clear ALl
buttonFont2 = font.Font(family='Castellar', size= 20)  #only used for clear, clear ALl
onebutton = tk.Button(frame, text="1", height = 3,
          width = 3, fg="red", font = "Castellar")
onebutton.place(relx = 0.2, rely = 0.4, anchor = 'center')
twobutton = tk.Button(frame, text="2", height = 3,
          width = 3, fg="brown", font = "Castellar")
twobutton.place(relx = 0.3, rely = 0.4, anchor = 'center')
threebutton = tk.Button(frame, text="3", height = 3,
          width = 3, fg="blue", font = "Castellar")
threebutton.place(relx = 0.4, rely = 0.4, anchor = 'center')
fourbutton = tk.Button(frame, text="4", height = 3,
          width = 3, fg="red", font = "Castellar")
fourbutton.place(relx = 0.2, rely = 0.5, anchor = 'center')
fivebutton = tk.Button(frame, text="5", height = 3,
          width = 3, fg="brown", font = "Castellar")
fivebutton.place(relx = 0.3, rely = 0.5, anchor = 'center')
sixbutton = tk.Button(frame, text="6", height = 3,
          width = 3, fg="blue", font = "Castellar")
sixbutton.place(relx = 0.4, rely = 0.5, anchor = 'center')
sevenbutton = tk.Button(frame, text="7", height = 3,
          width = 3, fg="red", font = "Castellar")
sevenbutton.place(relx = 0.2, rely = 0.6, anchor = 'center')
eightbutton = tk.Button(frame, text="8", height = 3,
          width = 3, fg="brown", font = "Castellar")
eightbutton.place(relx = 0.3, rely = 0.6, anchor = 'center')
ninebutton = tk.Button(frame, text="9", height = 3,
          width = 3, fg="blue", font = "Castellar")
ninebutton.place(relx = 0.4, rely = 0.6, anchor = 'center')
zerobutton = tk.Button(frame, text="0", height = 3,
          width = 3, fg="red", font = "Castellar")
zerobutton.place(relx = 0.2, rely = 0.7, anchor = 'center')
equalbutton = tk.Button(frame, text="=", height = 2,
          width = 3, fg="red", font = buttonFont2)
equalbutton.place(relx = 0.42, rely = 0.7, anchor = 'center')
negativebutton = tk.Button(frame, text="(-)", height = 3,
          width = 3, fg="red", font = "Castellar")
negativebutton.place(relx = 0.3, rely = 0.7, anchor = 'center')
    # Operatopns
addbutton = tk.Button(frame, text="Add", height = 3,
          width = 4, fg="red", font = "Castellar")
addbutton.place(relx = 0.6, rely = 0.4, anchor = 'center')
subbbutton = tk.Button(frame, text="Sub", height = 3,
          width = 4, fg="red", font = "Castellar")
subbbutton.place(relx = 0.7, rely = 0.4, anchor = 'center')
multbutton = tk.Button(frame, text="Mult", height = 3,
          width = 4, fg="brown", font = "Castellar")
multbutton.place(relx = 0.6, rely = 0.5, anchor = 'center')
divbutton = tk.Button(frame, text="Div", height = 3,
          width = 4, fg="brown", font = "Castellar")
divbutton.place(relx = 0.7, rely = 0.5, anchor = 'center')
squarebutton = tk.Button(frame, text="Squ", height = 3,
          width = 4, fg="blue", font = "Castellar")
squarebutton.place(relx = 0.6, rely = 0.6, anchor = 'center')
squarerootbutton = tk.Button(frame, text="Root", height = 3,
          width = 4, fg="blue", font = "Castellar")
squarerootbutton.place(relx = 0.7, rely = 0.6, anchor = 'center')
modulobutton = tk.Button(frame, text="Mod", height = 3,
          width = 4, fg="blue", font = "Castellar")
modulobutton.place(relx = 0.65, rely = 0.7, anchor = 'center')
#clearbutton = tk.Button(frame, text="Clear", fg="black", font = buttonFont1)
#clearbutton.place(relx = 0.3, rely = 0.9, anchor = 'center')
clearAllbutton = tk.Button(frame, height = 2,
          width = 6, text="Clear All", fg="black", font = buttonFont1)
clearAllbutton.place(relx = 0.5, rely = 0.9, anchor = 'center')
# To Stop Resizing
#Stop the frame from propagating the widget to be shrink or fit
# Button Binding
        #Numbers
zerobutton.bind("<Button-1>", ZeroButtonClick)
onebutton.bind("<Button-1>", OneButtonClick)
twobutton.bind("<Button-1>", TwoButtonClick)
threebutton.bind("<Button-1>", ThreeButtonClick)
fourbutton.bind("<Button-1>", FourButtonClick)
fivebutton.bind("<Button-1>", FiveButtonClick)
sixbutton.bind("<Button-1>", SixButtonClick)
sevenbutton.bind("<Button-1>", SevenButtonClick)
eightbutton.bind("<Button-1>", EightButtonClick)
ninebutton.bind("<Button-1>", NineButtonClick)
        #Functionality
clearAllbutton.bind("<Button-1>", clearDisplayClick)
#clearbutton.bind("<Button-1>", clearDisplayClick)
addbutton.bind("<Button-1>", addButtonClick)
subbbutton.bind("<Button-1>", subButtonClick)
multbutton.bind("<Button-1>", multButtonClick)
divbutton.bind("<Button-1>", divButtonClick)
squarebutton.bind("<Button-1>",squButtonClick )
squarerootbutton.bind("<Button-1>", rootButtonClick)
modulobutton.bind("<Button-1>", modButtonClick)
equalbutton.bind("<Button-1>", equalButtonClick)
negativebutton.bind("<Button-1>", oppositeSignClick)
t3=tk.Entry()
t3.place(relx=0.3, rely=0.3)
t3.insert(END, "Welcome to our calculator!")
