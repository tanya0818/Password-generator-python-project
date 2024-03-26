# Password-generator-python-project
from tkinter import *
from tkinter.ttk import Combobox
from tkinter import messagebox
import random
import string

root=Tk()
root.geometry('500x300')
root.title("Password Geneerator")
root.config(bg="white")
root.resizable(False,False)

def pass_Generator():
    try:
        len=solidboss.get()
        small=string.ascii_lowercase
        caps=string.ascii_uppercase
        digits=string.digits
        specials=string.punctuation
        all=[]
        all.extend(list(small))
        all.extend(list(caps))
        all.extend(list(digits))
        all.extend(list(specials))
        random.shuffle(all)
        password.set("".join(all[0:len]))
    except:
        messagebox.askokcancel("A problem has been occured","Please try again")
all_no={"0":"0","1":"1","2":"2","3":"3","4":"4","5":"5","6":"6","7":"7","8":"8","9":"9"}
Title=Label(root,text="Password Generator",bg="white",fg="black",font=("futura",15,"bold"))
Title.pack(anchor="center",pady="20px")

length=Label(root,text="Enter Password length:",bg="orange",font=("futura",15,"bold"))
length.place(x="20px",y="70px")

def enter(e):
    btn['bg']="grey"
    btn['fg']="black"
def leave(e):
    btn['bg']="blue"
    btn['fg'] = "black"

solidboss=IntVar()
selector=Combobox(root,textvariable=solidboss,state='readonly')
selector['values']=[l for l in all_no.keys()]
selector.current(7)
selector.place(x='200px',y='72px')

btn=Button(root,text="Generate Password",bg="green",fg="black",font=("ubuntu",15),cursor="hand2",command=pass_Generator)
btn.bind("<Enter>",enter)
btn.bind("<Leave>",leave)
btn.pack(anchor="center",pady="50px")
result=Label(root,text="Generated Password:",bg="orange",fg="green",font=("futura",15,"bold"))
result.place(x="20px",y="160px")
password = StringVar()
password_final=Entry(root,textvariable=password,state="readonly",fg="red",font=("ubuntu",15))
password_final.place(x="200px",y="160px")
root.mainloop()
