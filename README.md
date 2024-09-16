# Extracting Numeric Values from Images using EasyOCR for Entity Recognition 🖼️🔢

## Introduction 🚀

This project focuses on extracting **numerical values** and their corresponding **units** from a set of images, each associated with specific entities such as **weight, height, or voltage**. The goal is to develop a machine learning pipeline that accurately predicts these values and units from the images, overcoming challenges like variable image quality, different text fonts, and OCR (Optical Character Recognition) errors. 🧐

## Approach 🛠️

Our approach involves several key steps:

1. **Image Text Extraction using OCR** 📄:
   - We use **EasyOCR** with **GPU acceleration** to extract text from images efficiently.
   
2. **Text Pre-processing** 🧹:
   - Clean and normalize the extracted text to reduce noise and correct common OCR misrecognitions.
   
3. **Value and Unit Extraction** 🎯:
   - Using **regular expressions** tailored to each entity, we extract numerical values and units from the pre-processed text.
   
4. **Model Evaluation** 📊:
   - Compare the extracted values and units with the ground truth to evaluate accuracy.

5. **Prediction on Test Data** 🧠:
   - Apply the pipeline to the test dataset and generate predictions.

## Models Used 🧩

- **EasyOCR**: An open-source OCR tool optimized for **GPU** usage. It supports multiple languages and efficiently extracts text from images, which is crucial for our task.

## Experiments and Iterations 🔄

### Initial OCR Extraction ⚙️
- **EasyOCR** was implemented to extract text from images.
- Observed that raw OCR results often contained noise and misrecognized characters.

### Text Pre-processing Enhancements 🧽
- **Lowercasing**: Converted all text to lowercase for uniformity.
- **Character Replacement**: Fixed common misrecognized characters (e.g., "O" → "0", "l" → "1").
- **Removing Unwanted Characters**: Kept only alphanumeric characters, percentages, periods, and spaces.
- **Whitespace Normalization**: Streamlined text by removing extra spaces.

### Value and Unit Extraction Improvements 🔍
- Used an **entity-specific unit map** to associate entities with their allowed units.
- Created **regex patterns** to match numerical values followed by units.
- Implemented **fallback mechanisms** to handle cases where initial extraction fails by assigning default units based on the entity.

### Handling OCR Errors ⚠️
- Introduced a `clean_up_text` function to handle OCR misrecognitions.
- Adjusted regex patterns to account for values and units without spaces (e.g., "74m").

### Model Evaluation 📐
- Calculated training accuracy by comparing extracted values and units with ground truth.
- Observed accuracy improvements with each iteration of text pre-processing and extraction enhancements.

## Conclusion 🎉

Through systematic refinement of our OCR extraction and text pre-processing methods, we've significantly improved the accuracy of numerical value and unit extraction. The final pipeline adeptly handles common OCR errors and variations in text formats, providing a robust solution for entity recognition tasks. ✨
