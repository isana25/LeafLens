import gradio as gr
import numpy as np
from tensorflow.keras.preprocessing import image
from tensorflow.keras.models import load_model
from PIL import Image

# Load model
model = load_model("plant_disease_model.h5")  # You must include this file in your repo
IMG_SIZE = (224, 224)
class_names = ['Apple___Black_rot', 'Tomato___Early_blight', 'Potato___Late_blight']  # Update this to match your model

# Prediction function
def predict_plant_disease(img):
    img = img.resize(IMG_SIZE)
    img_array = image.img_to_array(img) / 255.0
    img_array = np.expand_dims(img_array, axis=0)

    predictions = model.predict(img_array)
    index = np.argmax(predictions)
    confidence = float(predictions[0][index])

    disease_name = class_names[index]
    confidence_text = f"{confidence:.2%}"
    confidence_value = round(confidence, 2)

    return disease_name, confidence_value, confidence_text

# Gradio UI
with gr.Blocks(css=".green-btn button {background-color: #2e7d32 !important; color: white;}") as demo:
    gr.Markdown("<h1 style='text-align:center;'>🌿 Smart Plant Disease Detector</h1>")

    with gr.Row():
        with gr.Column(scale=1):
            image_input = gr.Image(type="pil", label="📷 Upload Leaf Image")
            predict_btn = gr.Button("🔍 Detect Disease", elem_classes="green-btn")

        with gr.Column(scale=1):
            disease_output = gr.Textbox(label="🪴 Detected Disease")
            confidence_bar = gr.Slider(label="📊 Confidence Level", minimum=0, maximum=1, step=0.01, interactive=False)
            confidence_text = gr.Textbox(label="🔢 Confidence (Text)")

    predict_btn.click(fn=predict_plant_disease, 
                      inputs=image_input, 
                      outputs=[disease_output, confidence_bar, confidence_text])

demo.launch()
