- Python GUI
````python
from tkinter import *

root = Tk()

root.title("Helwan")
root.geometry("500x500")


# # greeting = Label(text="hello")

# # label = Label(
# #     text='Hello Python',
# #     fg='white',
# #     bg='black',
# #     width=10,
# #     height=10
# # )

# # btn = Button(
# #     text="Click Me",
# #     width=25,
# #     height=5,
# #     bg="blue",
# #     fg="yellow"
# # )

# # input = Entry(
# #         bg="red",
# #     fg="yellow",
# #         width=25,
# # )

# # textbox = Text(width=30,height=10)

# # # label.pack()
# # # greeting.pack()
# # # btn.pack()
# # textbox.pack()
# # input.pack()



# photo = PhotoImage(file="x.png")

# l1 = Label(image=photo, text="Ssss")
# l1.pack()


# r1 = Radiobutton(
#     text="Male",
#     value=1
# )

# r2 = Radiobutton(
#     text="Female",
#     value=2
# )
# r1.pack()
# r2.pack()


# c1 = Checkbutton(
#     text="Python"
# )

# c2 = Checkbutton(
#     text="Java"
# )
# c1.pack()
# c2.pack()


# f1 = Frame(background="blue")
# f2 = Frame()

# lab1 = Label(master=f1,text="in frame 1")
# lab2 = Label(master=f2,text="in frame 2")


# lab1.pack()
# lab2.pack()

# f1.pack()
# f2.pack()

output_label = Label(root)
output_label.pack()
def java():
    output_label.config(text = "sdasd")

b1 = Button(text="java",command=java)

b1.pack()

root.mainloop()
````
