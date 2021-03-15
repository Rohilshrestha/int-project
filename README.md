# int-project
from random import shuffle
from string import printable
import tkinter as tk
import random

chars=["क","ख","ग","घ","ङ","च","छ","ज","झ","ण","त","थ","द","ध","न","प","फ","ब","भ",
"म","य","र","ल","व","स","श","ष","ह","ञ","ै","ौ","ृ","ु","ू","ि","ी","ो","ा","े",'0',
'1', '2', '3', '4', '5', '6', '7', '8', '9', 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h',
'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y',
'z',  'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P',
'Q', 'R', 'S',  'T', 'U', 'V', 'W', 'X', 'Y', 'Z','!', '"', '#', '$', '%', '&',
'(', ')', '*', '+', ',',   '-', '.', '/', ':', ';', '<', '=', '>', '?', '@', '[', ']',
'^', '_', '`', '{', '|', '}', '~']

keys=list(chars)
shuffled_keys=list(chars)
shuffle(shuffled_keys)
maps=dict(zip(keys,shuffled_keys))
reversed_maps=dict(zip(shuffled_keys,keys))

def encrypt(text):
    mono=[]    
    for m in text:
          if m in chars:
            mono.append(maps[m])
          else:
            mono.append(m)
    return"".join(mono)

def decrypt(mono):
    normal_text = []
    for m in mono:
        if m in chars:
            normal_text.append(reversed_maps[m])
        else:
            normal_text.append(m)
    return''.join(normal_text)

root = tk.Tk()
root.title("Text Encryption")
root.geometry('400x600')
root.configure(background = "#141e30")

def Take_input():
   inputs =  e1.get()
   e2.insert(10, encrypt(inputs))

def Decrypt_input():
    inputs =  e1.get()
    e3.insert(10, decrypt(encrypt(inputs)))

def Clear_input():    
    e1.delete(0, tk.END)
    e2.delete(0, tk.END)
    e3.delete(0,tk.END)

tk.Label(root,text="Normal Text",bg="white").place(x = 20,y = 10)
tk.Label(root,text="Encrypted Text",bg="white").place(x = 20,y = 200)
tk.Label(root,text="Decrypted Text",bg="white").place(x = 20,y = 400)

e1 = tk.Entry(root)
e2 = tk.Entry(root)
e3 = tk.Entry(root)
e1.place(x = 20,y = 34,width=200,height=100)
e2.place(x = 20,y = 224,width=200,height=100)
e3.place(x = 20,y = 424,width=200,height=100)

btn1 = tk.Button(root,text='Clear', bg="#9f96f5", command=Clear_input)
btn1.place(x = 20,y = 550)
btn2 = tk.Button(root,text='Encrypt',  bg="#9f96f5", command=Take_input)
btn2.place(x = 30,y = 150)
btn3 = tk.Button(root,text='Decrypt', bg="#9f96f5", command=Decrypt_input)
btn3.place(x = 20,y = 350)

tk.mainloop()
