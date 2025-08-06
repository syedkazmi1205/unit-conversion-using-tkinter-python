
GUI Unit Converter
A Tkinter-based GUI application that includes:

A main menu with File and Help options.

A simple frame and button layout.

A unit conversion tool supporting common length units.

✨ Features
Interactive GUI

Frames for buttons and labels

Custom colors and layouts

Menu Bar

File menu: Create new action, exit option

Help menu: About section

Unit Converter

Convert between:

Centimeter

Inch

Meter

Foot

Kilometer

Mile

Yard

Supports keyboard shortcut: press Enter to convert

Displays results with appropriate decimal precision

Popup Messages

Informational dialogs using messagebox

🖼 Preview Layout
less
Copy
Edit
+----------------------------------------------------+
|                   Menu Bar                         |
+----------------------------------------------------+
|  Main Frame                                        |
|  ┌──────────────┐  ┌──────────────┐                |
|  | Buttons      |  | Labels       |                |
|  └──────────────┘  └──────────────┘                |
|                                                    |
|  [Unit Converter Title]                            |
|  Enter Value: [____]   From: [Dropdown]            |
|                 To:   [Dropdown]                   |
|  [Convert Button]                                   |
|  Result will appear here                           |
+----------------------------------------------------+
|          © 2023 Unit Converter Pro                 |
+----------------------------------------------------+
🛠 Installation & Usage
Clone this repository:

bash
Copy
Edit
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
Run the program:

bash
Copy
Edit
python main.py
📂 File Structure
bash
Copy
Edit
.
├── main.py        # Main Tkinter application
└── README.md      # Documentation
📸 Example Conversion
If you input:

makefile
Copy
Edit
Value: 100
From: Centimeter
To: Meter
The program will output:

Copy
Edit
100 Centimeter = 1.00 Meter
📜 License
This project is licensed under the MIT License
