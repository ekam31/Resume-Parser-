Custom NER with spaCy & Transformers

This project builds a custom Named Entity Recognition (NER) model using spaCy and Hugging Face Transformers to extract entities (Name, Email, Skills, etc.) from resumes.

🔧 Requirements:

pip install -U spacy
pip install spacy_transformers
pip install torch torchvision torchaudio
pip install pymupdf tqdm scikit-learn
🗂️ Data Format:

[("Sample text", {"entities": [(start, end, "LABEL")]})]
⚙️ Steps:

Convert JSON annotations to .spacy format using DocBin.
Split into train/test sets using train_test_split.
Create config:
python -m spacy init fill-config base_config.cfg config.cfg
Train the model:
python -m spacy train config.cfg --output ./output --paths.train train_data.spacy --paths.dev test_data.spacy
🔍 Inference:

nlp = spacy.load("model_for_ner")
doc = nlp(text)
for ent in doc.ents:
    print(ent.text, ent.label_)
📊 Visualization:
displacy.serve(doc, style="ent")

That’s it! You now have a trained NER pipeline ready to extract structured information from resumes.
