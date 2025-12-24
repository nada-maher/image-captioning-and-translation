# Image Captioning & Translation using BLIP + mBART

This project implements an AI-powered image captioning system that generates descriptive captions from images and optionally translates them into Arabic. It uses a hybrid pipeline combining BLIP for image caption generation and mBART-50 for multilingual translation.

The goal of the project is to explore vision–language models and understand how image understanding can be integrated with neural machine translation to produce coherent captions in multiple languages.

## Project Overview

- Built an image-to-text captioning system using BLIP (Bootstrapping Language-Image Pre-training)
- Integrated mBART-50 for English → Arabic translation
- Trained and fine-tuned mBART on a bilingual English–Arabic dataset
- Designed a simple Gradio-based web interface
- Supports caption generation in English or Arabic
- Enables real-time image upload and caption prediction

## Key Concepts

- Computer Vision
- Natural Language Processing (NLP)
- Image Captioning
- Transformer Models
- Vision–Language Models
- Neural Machine Translation (NMT)
- Text Tokenization and Sequence Generation
- Model Fine-Tuning

## Model Architecture

### 1. BLIP — Image Encoder & Caption Generator
- Extracts visual features from the input image
- Generates an initial English description
- Provides high-quality captions with vision–text attention

### 2. mBART-50 — Machine Translation
- Receives the English caption from BLIP
- Translates it into Arabic using a fine-tuned many-to-many model
- Handles tokenization, sequence generation, and decoding

### 3. Combined Pipeline

Image → BLIP → English Caption → mBART (optional) → Arabic Caption


## Dataset (for Translation Fine-Tuning)

The mBART model was fine-tuned on a parallel English–Arabic dataset.

Preprocessing steps included:
- Lowercasing
- Removing special characters
- Text normalization
- Tokenization
- Padding and truncation
- Building DataLoader for batches

## Results

- Generates accurate and coherent English captions from images
- Produces high-quality Arabic translations of the generated captions
- Demonstrates the strength of combining vision–language and NMT models
- Fully deployable through a Gradio GUI

## GUI Access

A simple and interactive GUI was built using Gradio:
- Upload an image
- Choose the output language (English or Arabic)
- Receive a generated caption instantly

## Team Members

- Nada Maher Mohamed El-hady
- Hanaa Mahmoud Ahmed
- Hager Khaled Ibrahim
- Menna Allah Elsaeed

## Future Improvements

- Add support for more output languages
- Improve translation accuracy with larger bilingual datasets
- Fine-tune BLIP for custom-domain captioning
- Add temperature, top-k, and top-p sampling controls

## License

This project is created for educational and research purposes.
