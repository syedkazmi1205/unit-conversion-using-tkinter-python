import tkinter as tk
from tkinter import messagebox

def say_hello():
    messagebox.showinfo("hello", "hello frm devs!")

def show_help():
    messagebox.showinfo(
        "Help",
        "To use the unit converter:\n"
        "1. Enter a numeric value.\n"
        "2. Select the 'From' unit.\n"
        "3. Select the 'To' unit.\n"
        "4. Click Convert or press Enter."
    )

def convert():
    try:
        value = float(entry.get())
        from_u = from_unit.get()
        to_u = to_unit.get()

        # Conversion factors to meters
        to_meter = {
            "Centimeter": 0.01,
            "Inch": 0.0254,
            "Meter": 1.0,
            "Foot": 0.3048,
            "Kilometer": 1000.0,
            "Mile": 1609.34,
            "Yard": 0.9144
        }

        meters = value * to_meter[from_u]
        result = meters / to_meter[to_u]

        # Format the result nicely
        if abs(result) < 0.01:
            result_str = f"{result:.6f}"
        elif abs(result) < 1:
            result_str = f"{result:.4f}"
        else:
            result_str = f"{result:.2f}"

        result_label.config(text=f"{value} {from_u} = {result_str} {to_u}")

    except ValueError:
        messagebox.showerror("Invalid Input", "Please enter a valid number")
    except KeyError:
        messagebox.showerror("Conversion Error", "Selected units are not available")

# --- Main application setup ---

root = tk.Tk()
root.title("Unit Converter")
root.geometry("600x550")

# Menu bar
menubar = tk.Menu(root)
root.config(menu=menubar)

file_menu = tk.Menu(menubar, tearoff=0)
menubar.add_cascade(label="File", menu=file_menu)
file_menu.add_command(label="New", command=say_hello)
file_menu.add_separator()
file_menu.add_command(label="Exit", command=root.quit)

help_menu = tk.Menu(menubar, tearoff=0)
menubar.add_cascade(label="Help", menu=help_menu)
help_menu.add_command(label="About", command=lambda: messagebox.showinfo("About", "Simple menu design"))

# Main frame (uses grid)
main_frame = tk.Frame(root, bg="light green", relief="raised")
main_frame.pack(padx=10, pady=10, fill="both", expand=True)

# Button frame (uses pack)
button_frame = tk.Frame(main_frame, bg="light green", relief="sunken")
button_frame.pack(padx=5, pady=5, fill="x")

tk.Button(button_frame, text="help?", command=show_help).pack(side="left", padx=5)
tk.Button(button_frame, text="start").pack(side="left", padx=5)

# Label frame (uses pack)
label_frame = tk.Frame(main_frame, bg="light yellow", relief="sunken")
label_frame.pack(padx=5, pady=5, fill="x")

tk.Label(label_frame, text="label inside frame", bg="light green").pack()

# Title
title_label = tk.Label(main_frame, text="Unit Converter", font=("Arial", 20, "bold"), bg=main_frame['bg'])
title_label.grid(row=0, column=0, columnspan=4, pady=(0, 20))

units = ["Centimeter", "Inch", "Meter", "Foot", "Kilometer", "Mile", "Yard"]

# Entry and labels using grid inside main_frame
tk.Label(main_frame, text="Enter value:", font=("Arial", 12), bg=main_frame['bg']).grid(row=1, column=0, padx=5, pady=5, sticky=tk.E)

entry = tk.Entry(main_frame, width=15, font=("Arial", 12), bd=2, relief=tk.GROOVE)
entry.grid(row=1, column=1, padx=5, pady=5)
entry.focus_set()

tk.Label(main_frame, text="From:", font=("Arial", 12), bg=main_frame['bg']).grid(row=1, column=2, padx=5, pady=5)

from_unit = tk.StringVar(value=units[0])
from_menu = tk.OptionMenu(main_frame, from_unit, *units)
from_menu.config(width=12, font=("Arial", 10), bd=2, relief=tk.GROOVE)
from_menu.grid(row=1, column=3, padx=5, pady=5)

tk.Label(main_frame, text="To:", font=("Arial", 12), bg=main_frame['bg']).grid(row=2, column=2, padx=5, pady=5)

to_unit = tk.StringVar(value=units[1])
to_menu = tk.OptionMenu(main_frame, to_unit, *units)
to_menu.config(width=12, font=("Arial", 10), bd=2, relief=tk.GROOVE)
to_menu.grid(row=2, column=3, padx=5, pady=5)

# Convert button
convert_button = tk.Button(
    main_frame,
    text="Convert (Enter)",
    command=convert,
    font=("Arial", 12, "bold"),
    bg="#4CAF50",
    fg="white",
    activebackground="#45a049",
    width=15
)
convert_button.grid(row=3, column=1, columnspan=2, pady=15)

# Result label
result_label = tk.Label(main_frame, text="Result will appear here", font=("Arial", 12, "bold"), fg="#1e88e5", bg=main_frame['bg'])
result_label.grid(row=4, column=0, columnspan=4, pady=10)

# Keyboard binding for Enter key
entry.bind('<Return>', lambda event: convert_button.invoke())

# Footer
footer = tk.Label(root, text="© 2023 Unit Converter Pro", font=("Arial", 8), fg="#666666", pady=5)
footer.pack(side=tk.BOTTOM, fill=tk.X)

if __name__ == "__main__":
    root.mainloop()
