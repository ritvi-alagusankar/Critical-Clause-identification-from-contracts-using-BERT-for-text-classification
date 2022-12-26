# Critical Clause Extraction from contracts using BERT for text classification

Critical clauses are sections of a contract that are of great significance. These clauses if ignored may cause financial/legal damages to the party. Extracting these clauses in an agreement will protect your business from miscommunication and lawsuits, providing legal safeguards that your business may not otherwise receive.

# OCR engine (Pytesseract)
Pytesseract or Python-tesseract is an OCR tool for python that also serves as a wrapper for the Tesseract-OCR Engine. It can read and recognize text embedded in images.

We use Pytesseract as our OCR engine to read the contents of the PDF file.

The PDF files are taken from the repository and passed through the OCR engine. The OCR engine first converts the given PDF files into images using the convert_from_path() function of Pytesseract.
