1. Pliki `part` wypakuj do jednego folderu. Ścieżkę w kodzie ustawiamy pytesseract.pytesseract.tesseract_cmd=PATH
2. Plik poppler wypakuj do innego folderu. Ścieżkę ustawiamy w kodzie w funkcji convert_from_path.

import pytesseract
from PIL import Image
from pdf2image import convert_from_path

pytesseract.pytesseract.tesseract_cmd = r'C:\Users\s1623573\Pictures\ggg\tesseract'

images = convert_from_path(path_to_file, 550,poppler_path=r'C:\Users\s1623573\poppler-24.02.0\Library\bin')
text=''

for i, image in enumerate(images):
    fname = 'image'+str(i)+'.png'
    image.save(fname, "PNG")
    text+=pytesseract.image_to_string(Image.open(fname),lang='pol')
