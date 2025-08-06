
import tkinter as tk
from tkinter import messagebox
#main window:
root = tk.Tk()
root .title("GUI")
root.geometry("600x550")
#main frame:

main_frame = tk.Frame(root, bg = "light blue", relief = "raised")
main_frame.pack(padx=10, pady=10, fill="both", expand=True, bg = "light green")

#inner frame for btns:
button_frame = tk.Frame(main_frame, bg="light green", relief = "sunken")
button_frame.pack(padx=5, pady=5, fill="x")

#inner frame fior za btns:
label_frame = tk.Frame(main_frame, bg="light yellow", relief="sunken")
label_frame.pack(padx=5, pady=5, fill="x")

#buttonssss:
tk.Button(button_frame, text="help?").pack(side="left", padx=5)
tk.Button(button_frame, text="start").pack(side="left", padx=5)
tk.Label(label_frame, text="label inside frame", bg="light green")

#hello nonsense ts:
def say_hello():
  messagebox.showinfo("hello", "hello frm devs!")  





#menu:
menubar = tk.Menu(root)
root.config(menu=menubar)

#file meenuuuu:
file_menu = tk.Menu(menubar)
menubar.add_cascade(label="file", menu=file_menu)
file_menu.add_command(label="New", command=say_hello)
file_menu.add_separator()
file_menu.add_command(label="exit", )
#HHHEEEEELLLLLLLLLPPPPPP:
help_menu = tk.Menu(menubar, tearoff=0)
menubar.add_cascade(label="HELP!", menu=help_menu)
help_menu.add_command(label="About", command=lambda:messagebox.showinfo("About", "simple menu design"))

    # Add title
title_label = tk.Label(main_frame, text="Unit Converter", 
                         font=("Arial", 20, "bold"), bg='#f0f2f5')
title_label.grid(row=0, column=0, columnspan=4, pady=(0, 20))

    # Units to convert between
units = ["Centimeter", "Inch", "Meter", "Foot", "Kilometer", "Mile", "Yard"]

    # Value entry
entry_label = tk.Label(main_frame, text="Enter value:", 
                         font=("Arial", 12), bg='#f0f2f5')
entry_label.grid(row=1, column=0, padx=5, pady=5, sticky=tk.E)

entry = tk.Entry(main_frame, width=15, font=("Arial", 12), bd=2, relief=tk.GROOVE)
entry.grid(row=1, column=1, padx=5, pady=5)
entry.focus_set()

    # From unit dropdown
from_label = tk.Label(main_frame, text="From:", 
                        font=("Arial", 12), bg='#f0f2f5')
from_label.grid(row=1, column=2, padx=5, pady=5)

from_unit = tk.StringVar(value=units[0])
from_menu = tk.OptionMenu(main_frame, from_unit, *units)
from_menu.config(width=12, font=("Arial", 10), bd=2, relief=tk.GROOVE)
from_menu.grid(row=1, column=3, padx=5, pady=5)

    # To unit dropdown
to_label = tk.Label(main_frame, text="To:", 
                      font=("Arial", 12), bg='#f0f2f5')
to_label.grid(row=2, column=2, padx=5, pady=5)

to_unit = tk.StringVar(value=units[1])
to_menu = tk.OptionMenu(main_frame, to_unit, *units)
to_menu.config(width=12, font=("Arial", 10), bd=2, relief=tk.GROOVE)
to_menu.grid(row=2, column=3, padx=5, pady=5)

    # Conversion function
def convert():
        try:
            value = float(entry.get())
            from_u = from_unit.get()
            to_u = to_unit.get()
            
            # Define conversion factors to meters (base unit)
            to_meter = {
                "Centimeter": 0.01,
                "Inch": 0.0254,
                "Meter": 1.0,
                "Foot": 0.3048,
                "Kilometer": 1000.0,
                "Mile": 1609.34,
                "Yard": 0.9144
            }
            
            # Convert to meters first, then to target unit
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

    # Convert button
convert_button = tk.Button(main_frame, text="Convert (Enter)", 
                             command=convert,
                             font=("Arial", 12, "bold"), bg="#4CAF50", fg="white",
                             activebackground="#45a049", width=15)
convert_button.grid(row=3, column=1, columnspan=2, pady=15)

    # Result label
result_label = tk.Label(main_frame, text="Result will appear here", 
                          font=("Arial", 12, "bold"), fg="#1e88e5", bg='#f0f2f5')
result_label.grid(row=4, column=0, columnspan=4, pady=10)

    # Add keyboard binding
entry.bind('<Return>', lambda event: convert())

    # Add footer
footer = tk.Label(root, text="© 2023 Unit Converter Pro", 
                     font=("Arial", 8), fg="#666666", pady=5)
footer.pack(side=tk.BOTTOM, fill=tk.X)

    # Start the application


if __name__ == "__main__":

    root.mainloop()
