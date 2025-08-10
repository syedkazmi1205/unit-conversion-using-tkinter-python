
# Unit Converter

A simple and user-friendly desktop unit converter application built using Python's Tkinter library.

---

## Features

- Convert between various length units: Centimeter, Inch, Meter, Foot, Kilometer, Mile, Yard.
- Easy-to-use graphical interface with dropdowns for selecting "From" and "To" units.
- Supports conversion via button click or pressing the Enter key.
- Clear display of conversion results with appropriate formatting.
- Built-in help and about dialogs accessible from the GUI.
- Includes basic menu options like New and Exit.

---

## Screenshots

*(Add screenshots here, if you want to display the UI)*

---

## How to Use

1. Enter a numeric value in the input field.
2. Select the unit you want to convert **from**.
3. Select the unit you want to convert **to**.
4. Click the **Convert (Enter)** button or press the **Enter** key.
5. See the converted result displayed below.

To get help on usage, click the **help?** button.

---

## Installation

Make sure you have Python installed (version 3.x is recommended).

This application uses the built-in `tkinter` module, so no extra installation is required.

---

## Running the Application

Simply run the Python script:

python unit_converter.py

text

*(Replace `unit_converter.py` with the filename you saved the code as)*

---

## Code Structure

- `say_hello()`: Shows a simple greeting message.
- `show_help()`: Displays instructions on how to use the converter.
- `convert()`: Handles the conversion logic, error checking, and displays the result.
- Tkinter GUI setup with menu bar, main frame with entry, dropdowns, buttons, and labels.
- Keyboard binding for convenience (Enter key triggers conversion).
- Footer label with copyright.

---

## Supported Units and Conversion Factors

| Unit       | To Meter Factor |
|------------|-----------------|
| Centimeter | 0.01            |
| Inch       | 0.0254          |
| Meter      | 1.0             |
| Foot       | 0.3048          |
| Kilometer  | 1000.0          |
| Mile       | 1609.34         |
| Yard       | 0.9144          |

---

## License

*(Add license info here if applicable)*

---

## Author

Made by devs (you can modify as needed).

---

Feel free to fork, modify, and improve this unit converter!
