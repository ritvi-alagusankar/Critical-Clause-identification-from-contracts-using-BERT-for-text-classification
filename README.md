# Critical Clause Extraction from contracts using BERT for text classification

Critical clauses are sections of a contract that are of great significance. These clauses if ignored may cause financial/legal damages to the party. Extracting these clauses in an agreement will protect your business from miscommunication and lawsuits, providing legal safeguards that your business may not otherwise receive.

We are going to be reading a contract and extracting the critical clauses from the contract thereby safeguarding the party from potential financial/legal ruin. This can be achieved as follows :
![image](https://user-images.githubusercontent.com/114499776/209507161-3266d6ce-047a-4d14-acf9-8c260bb6bedc.png)

# OCR engine (Pytesseract)
Pytesseract or Python-tesseract is an OCR tool for python that also serves as a wrapper for the Tesseract-OCR Engine. It can read and recognize text embedded in images.

We use Pytesseract as our OCR engine to read the contents of the PDF file.

The PDF files are taken from the repository and passed through the OCR engine. The OCR engine first converts the given PDF files into images using the convert_from_path() function of Pytesseract.

``images = convert_from_path(path, 500, poppler_path= r'C:\\Program Files\\poppler-0.68.0\\bin')``

These images of each page of the PDF file are then converted to text using the image_to_string() function.

```
def convert_img_to_text(file):
text = image_to_string(file)
return text
```
    
The text is then stored in a string that contains the entire text of the PDF file. The text from the PDF file is then split into sentences using the split() function. We obtain a list of all the sentences in the file.

``sentence = re.split("\\. |\\.\n|\\.\n\n|\\:\n|\\: \n|\\:\n\n",text_from_pytesseract)``

These sentences are filtered removing the unnecessary parts of the PDF file. The sentences are then finally written into a CSV file. We get a CSV file containing all the clauses of the contract.

# Data Labelling/Annotation

The CSV files from all the contracts are then combined into one CSV file. This file consists of sentences(clauses) from all the contracts. This file is further filtered and we then proceed to the classification process. The various clauses are manually classified as critical or non-critical depending on their contents. Since the number of critical clauses is much less compared to the number of non-critical clauses in contracts, naturally there is an imbalance in the dataset. This problem is solved by adding several critical clauses from various legal contracts available on Kaggle.

![image](https://user-images.githubusercontent.com/114499776/209507325-07ff0991-4190-426b-afa9-fdc2f82c1d50.png)

Total number of clauses in dataset: 1216

Critical Clauses: 644

Non-critical Clauses: 572

The CSV file is then read and stored as a data frame using pandas. All the critical clauses are mapped as 1 and the non-critical clauses are mapped as 0.
