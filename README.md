# image-captioning-and-translation
This project combines image captioning using the BLIP model and English → Arabic translation using a fine-tuned mBART-50 model.
The system runs through a simple Gradio web interface, allowing you to upload an image and receive the caption in English or Arabic.

🚀 Features

📷 Upload an image and automatically generate a caption

🧠 Uses a fine-tuned BLIP model for English captions

🌍 Uses a fine-tuned mBART model for English → Arabic translation

🖥️ Clean Gradio UI

🗂️ Organized project structure

🔧 Easy to run locally or on cloud platforms


📂 Project Directory Structure
.
├── app.py                        # Main Gradio application
│
├── mbart_en_ar_model/            # Fine-tuned mBART model
│   ├── config.json
│   ├── tokenizer.json
│   ├── pytorch_model.bin
│   └── ...
│
├── blip/                         # Fine-tuned BLIP model
│   ├── config.json
│   ├── processor_config.json
│   ├── tokenizer.json
│   ├── pytorch_model.bin
│   └── ...
│
├── samples/                      # Optional sample images
│
├── README.md
└── requirements.txt

🧠 Models Used

🔹 1. BLIP — Image Captioning

Pretrained model: Salesforce/blip-image-captioning-base

Generates high-quality English captions from raw images.

🔹 2. mBART-50 — English → Arabic Translation

Base model: facebook/mbart-large-50-many-to-many-mmt

You fine-tuned it on your parallel EN→AR dataset.

Loaded locally from:

mbart_en_ar_model/

🛠 Installation
1️⃣ Clone the repository
git clone <your-repo-url>
cd <your-project-folder>

2️⃣ Install dependencies
pip install -r requirements.txt


If requirements.txt is missing, use this one:

torch
transformers
gradio


For GPU installation:

pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu121

🚀 Running the Application

Run Gradio:

python app.py


Then open the URL that appears:

http://127.0.0.1:7860

🖼 Application Workflow

1️⃣ Upload Image

User uploads an image via Gradio.

2️⃣ BLIP Generates English Caption
inputs = blip_processor(images=image, return_tensors="pt").to(device)
output_ids = blip_model.generate(**inputs)
english_caption = blip_processor.decode(output_ids[0], skip_special_tokens=True)

3️⃣ mBART Translates to Arabic (optional)
tokens = mbart_tokenizer(english_caption, return_tensors="pt").to(device)
arabic_ids = mbart_model.generate(**tokens)
arabic_caption = mbart_tokenizer.decode(arabic_ids[0], skip_special_tokens=True)

🎮 Gradio Interface (UI)

You can switch between:

English caption

Arabic translation

The UI allows real-time captioning and translation.

🧪 Example Output
Input Image

English Caption

"A brown dog running across a grassy field."

Arabic Translation

"كلب بني يجري عبر حقل عشبي."

🧵 Training Summary for mBART-50

You trained the model using a dataset containing:

en → English sentence

ar → Arabic translation

Core preprocessing logic:

labels = input_ids.clone()
labels[labels == tokenizer.pad_token_id] = -100


Why -100?
Because PyTorch’s CrossEntropyLoss ignores -100, so padding tokens don’t affect training.

🛣 Future Improvements

 Add Arabic → English translation

 Fine-tune BLIP for Arabic

 Add attention heatmap visualization

 Deploy app to HuggingFace Spaces

 Add multiple language options

📜 License

This project is licensed under the MIT License.

🙌 Acknowledgements

Salesforce Research for BLIP

Meta AI for mBART-50

HuggingFace for model hub + transformers

Gradio for UI framework
