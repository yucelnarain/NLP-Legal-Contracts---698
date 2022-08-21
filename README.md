# NLP-Legal-Contracts---698
Project Overview

This project creates an NLP pipeline that takes a transformer model trained on CUAD legal contracts and applies it to analyze and review existing procurement contracts by the State of Michigan’s Procurement Office. The project also explores techniques for fine-tuning an existing model to specific business uses via transfer learning, with the broader aim of facilitating the usage of complex tools for real-life applications within public institutions.

Data Sources

DTMB Procurement Contract List

The Michigan Dataset contains over 1000 rows of contracts over the last 10 years, making up the entire DTMB contract portfolio. This list is updated every week. The two relevant features used include the contract number, and a link to the actual contract embedded as a hyperlink. The current dataset used for this project is from the week of July 14th, 2022. For convenience of extraction we’ve downloaded 5 contracts from the database for usage with the models.

CUAD Dataset

The Contract Understanding Atticus Dataset (CUAD) is a dataset of over 500 contracts with over 13,000 expert made annotations for 41 different labels, provided by legal professionals from the Atticus Project.


Pipeline and Model

Requirements

Package requirements for all notebooks can be found in the following requirements.txt file. These can be installed by running the following line in your terminal:

pip install -r requirements.txt

Once requirements are installed, the following combined notebook will run all the actions which form our pipeline, and can be run to 1) extract the contracts, 2) convert them into text format, 3) run them through the transformer model to obtain results.

pdf_download_script.py: Extracts the urls from the DTMB excel sheet, and downloads pdf forms of the legal contracts.
To run this script:

Extracting Contract PDFs: 
download DTMB_PRO-Contract-List.xls
Insert the following into your terminal (Bold indicates custom input):
python pdf_download_script.py **Number of files you want to download** 'DTMB_PRO-Contract-List.xls' **File path for converted excel** 'Updated 07-14-2022' ‘ **File path to store pdf downloads’**
Example run on my computer: python pdf_download_script.py 5 'DTMB_PRO-Contract-List.xls' '/Users/narainyucel/Google Drive/MADS/capstone/697' 'Updated 07-14-2022' '/Users/narainyucel/Google Drive/MADS/capstone/697’
In case the extraction does not work due to permissions and package idiosyncrasies due to xlrd, we have provided 20 pdf contracts generated using this script for direct download.

Convert PDF to text files
PDF conversion notebook: Turns the pdfs into text data which can be input into the model. To run this action - open the notebook, then run all cells. Once all cells have run, run the final main() function to convert the pdfs into text.
PDF_to_txt.ipynb
User needs to specify custom ‘path’ and ‘output_path’ in the notebook to retrieve and to store documents
Run all the cells in PDF_to_txt.ipynb

Train model:
Run all the cells in Train.ipynb
Run all the cells in Predict.ipynb



Our Results


5 questions were asked on 3 different legal contracts from the DTMB. A domain expert compared predictions between the two models (0) and (1) and either scored it as 0, 1, or N/A if neither model produced relevant results. 

Based on our qualitative evaluation done by a procurement domain expert, we noticed a significant improvement in relevant prediction based on the retrained model. Out of 15 total questions, the retrained model predicted 11 correct answers (73%), which is much higher than the pre-trained model which only predicted 1 correct answer (7%). 



Result Example: 


For Detailed Results Please See the Following Blog Post. 
