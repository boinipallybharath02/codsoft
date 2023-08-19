import tkinter as tk

def button_click(number):
    current = entry.get()
    entry.delete(0, tk.END)
    entry.insert(0, current + str(number))

def button_clear():
    entry.delete(0, tk.END)

def button_backspace():
    current = entry.get()
    entry.delete(0, tk.END)
    entry.insert(0, current[:-1])

def button_equal():
    try:
        result = eval(entry.get())
        entry.delete(0, tk.END)
        entry.insert(0, str(result))
    except:
        entry.delete(0, tk.END)
        entry.insert(0, "Error")

# Create a GUI window
root = tk.Tk()
root.title("Calculator")

# Create an entry widget to display the input and results
entry = tk.Entry(root, width=20, borderwidth=5)
entry.grid(row=0, column=0, columnspan=4)

# Define buttons
buttons = [
    ("7", 1, 0), ("8", 1, 1), ("9", 1, 2), ("/", 1, 3),
    ("4", 2, 0), ("5", 2, 1), ("6", 2, 2), ("*", 2, 3),
    ("1", 3, 0), ("2", 3, 1), ("3", 3, 2), ("-", 3, 3),
    ("0", 4, 0), (".", 4, 1), ("=", 4, 2), ("+", 4, 3),
]

# Create and place buttons on the grid
for label, row, col in buttons:
    button = tk.Button(root, text=label, padx=20, pady=20, command=lambda label=label: button_click(label))
    button.grid(row=row, column=col)

# Clear button
clear_button = tk.Button(root, text="C", padx=20, pady=20, command=button_clear)
clear_button.grid(row=5, column=0, columnspan=2)

# Backspace button
backspace_button = tk.Button(root, text="←", padx=20, pady=20, command=button_backspace)
backspace_button.grid(row=5, column=2)

# Equal button
equal_button = tk.Button(root, text="=", padx=20, pady=20, command=button_equal)
equal_button.grid(row=5, column=3)

# Start the GUI event loop
root.mainloop()
