# CollageOCRproject
Optical Character Reader
//This Project used to read text from images and give its digital output 
//Modules use--

pytesseract- for reading languages 
Pillow- for adding and receiving images from computer
Tkinter- for adding graphics and different buttons




import tkinter as tk
from tkinter import filedialog
import pytesseract
pytesseract.pytesseract.tesseract_cmd='C:\\Program Files\\Tesseract-OCR\\tesseract.exe'
from PIL import Image, ImageTk

# Create the main window
window = tk.Tk()
window.geometry('500x300')

window.title("Python Project For Optical Character Reader")

# Create a function to open a file dialog and select an image file
def select_image():
    # Open a file dialog and get the selected file's path
 file_path = filedialog.askopenfilename()

 # Load the image using the Pillow library
 image = Image.open(file_path)

 # Use PyTesseract to extract the text from the image
 text = pytesseract.image_to_string(image)
 
 # Write the extracted text to a doc file
 with open("output.doc", "w") as f:
  f.write(text)

 # Display the extracted text in a text widget
 text_widget = tk.Text(window)
 text_widget.pack()
 text_widget.insert(tk.END, text)

 
#display image 
 img_widget = tk.Image(window)
 img_widget.geometry('600x400')
 img_widget.pack()
 img_widget.insert(tk.END, image)

# Create a button to trigger the image selection process
button = tk.Button(text="Select Image", command=select_image)
button.pack()

# Run the main loop
window.mainloop()
