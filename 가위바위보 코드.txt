from tkinter import *
import random
import tkinter as tk
from PIL import Image, ImageTk


def push(a):
    computer = random.randint(1, 3)
    canvas1.delete("all")
    canvas2.delete("all")

    if computer == 1:  # 가위
        canvas2.create_image(200, 200, image=tk_s1)
    elif computer == 2:  # 바위
        canvas2.create_image(200, 200, image=tk_r1)
    elif computer == 3:  # 보
        canvas2.create_image(200, 200, image=tk_p1)

    if a == "가위":
        canvas1.create_image(200, 200, image=tk_s1)

        if computer == 1:
            l1 = Label(window, text='======', font=("휴먼고딕", 30))
            l1.grid(row=0, column=1)
            l2 = Label(window, width=10, text='무승부!', fg="black", font=("휴먼고딕", 30))
            l2.grid(row=1, column=1)
        elif computer == 2:
            l1 = Label(window, text='<<<<<', font=("휴먼고딕", 30))
            l1.grid(row=0, column=1)
            l2 = Label(window, text='컴퓨터 승!', fg="black", font=("휴먼고딕", 30))
            l2.grid(row=1, column=1)
        elif computer == 3:
            l1 = Label(window, text='>>>>>', font=("휴먼고딕", 30))
            l1.grid(row=0, column=1)
            l2 = Label(window, text='사용자 승!', fg="black", font=("휴먼고딕", 30))
            l2.grid(row=1, column=1)

    elif a == "바위":
        canvas1.create_image(200, 200, image=tk_r1)
        if computer == 1:
            l1 = Label(window, text='>>>>>', font=("휴먼고딕", 30))
            l1.grid(row=0, column=1)
            l2 = Label(window, text='사용자 승!', fg="black", font=("휴먼고딕", 30))
            l2.grid(row=1, column=1)
        elif computer == 2:
            l1 = Label(window, text='=====', font=("휴먼고딕", 30))
            l1.grid(row=0, column=1)
            l2 = Label(window, width=10, text='무승부!', fg="black", font=("휴먼고딕", 30))
            l2.grid(row=1, column=1)
        elif computer == 3:
            l1 = Label(window, text='<<<<<', font=("휴먼고딕", 30))
            l1.grid(row=0, column=1)
            l2 = Label(window, text='컴퓨터 승!', fg="black", font=("휴먼고딕", 30))
            l2.grid(row=1, column=1)

    elif a == "보":
        canvas1.create_image(200, 200, image=tk_p1)
        if computer == 1:
            l1 = Label(window, text='<<<<<', font=("휴먼고딕", 30))
            l1.grid(row=0, column=1)
            l2 = Label(window, text='컴퓨터 승!', fg="black", font=("휴먼고딕", 30))
            l2.grid(row=1, column=1)
        elif computer == 2:
            l1 = Label(window, text='>>>>>', font=("휴먼고딕", 30))
            l1.grid(row=0, column=1)
            l2 = Label(window, text='사용자 승!', fg="black", font=("휴먼고딕", 30))
            l2.grid(row=1, column=1)
        elif computer == 3:
            l1 = Label(window, text='=====', font=("휴먼고딕", 30))
            l1.grid(row=0, column=1)
            l2 = Label(window, width=10, text='무승부!', fg="black", font=("휴먼고딕", 30))
            l2.grid(row=1, column=1)


window = Tk()
window.title("가위바위보!")

canvas1 = tk.Canvas(window, width=400, height=400)
canvas1.grid(row=0, column=0)
canvas2 = tk.Canvas(window, width=400, height=400)
canvas2.grid(row=0, column=2)

s1 = Image.open("가위바위보 가위.png").resize((300, 300))
r1 = Image.open("가위바위보 바위.png").resize((300, 300))
p1 = Image.open("가위바위보 보.png").resize((300, 300))
tk_s1 = ImageTk.PhotoImage(s1)
tk_r1 = ImageTk.PhotoImage(r1)
tk_p1 = ImageTk.PhotoImage(p1)

num = 0
rsp = ["바위", "보", "가위"]
for loop in rsp:
    def clickRSP(j=loop):
        push(j)

    button = Button(window, text=loop, font=("휴먼고딕", 12), width=25, command=clickRSP)
    button.grid(row=2, column=num)
    num = num + 1

window.mainloop()