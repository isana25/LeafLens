### 🌿 **What’s the Project About?**

The **LeafLens** is an AI-based project that uses **deep learning** to identify **plant leaf diseases** from images.

## 🧠 Model Architecture

This project uses **MobileNetV2** as the core model for plant disease classification.

- ✅ Pre-trained on **ImageNet**
- 🔁 Fine-tuned on the **PlantDoc dataset**
- 💡 Chosen for its lightweight structure and high efficiency on mobile and browser-based applications
- ⚙️ Custom classification layers added on top (Dense + Dropout + Softmax)

> MobileNetV2 was selected due to its excellent trade-off between accuracy and performance, making it ideal for real-time inference in interactive web apps like this one.

### 🔍 **What Does It Do (Functionality)?**

1. **📸 Takes an image of a plant leaf**  
   – You upload or pass a photo of a plant leaf (could be healthy or diseased).

2. **🧠 Detects the type of disease (if any)**  
   – The trained model analyzes the image and predicts which disease the plant might have — or says it's healthy.

3. **🔍 Classifies among multiple diseases**  
   – The model is trained on **many different classes**, like:  
   - Tomato\_\_\_Early\_blight  
   - Apple\_\_\_Black\_rot  
   - Potato\_\_\_Late\_blight  
   - And more...

4. **📊 Shows prediction result and confidence**  
   – After analysis, it returns:  
   - The **name of the disease**  
   - The **confidence/probability** (e.g., 94% Tomato\_\_\_Early\_blight)

### 💡 Real-World Use

This kind of project can help:

- **Farmers** detect plant issues early using mobile apps  
- **Agricultural experts** monitor crop health at scale  
- **Researchers** build smart farming solutions
