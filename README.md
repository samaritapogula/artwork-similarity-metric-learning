# 🎨 Artwork Similarity using Metric Learning

An image retrieval system for artworks that learns visual similarity using deep learning.  
This project uses **Triplet Loss** to train embeddings and compares performance with **CLIP**.

---

## 🚀 Overview

Understanding similarity between artworks is challenging due to variations in style, composition, and artistic intent.

Instead of traditional classification, this project uses **metric learning** to learn an embedding space where:
- Similar artworks are close together  
- Dissimilar artworks are far apart

This project demonstrates how domain-specific metric learning compares against large pretrained models (CLIP) for fine-grained artwork similarity.

---

## 🧠 Approach

### 🔹 Model
- Backbone: ResNet18 (pretrained)
- Output: 256-dimensional embeddings
- Normalization: L2-normalized embeddings

### 🔹 Training
- Loss: Triplet Margin Loss
- Strategy:
  - Anchor → Image
  - Positive → Same artist
  - Negative → Different artist

---

## 📊 Dataset

- Source: Artwork metadata + IIIF images
- Filtered:
  - Only paintings
  - Valid artist attribution
- Final dataset size: **~4000 images**

---

## 🔍 Image Retrieval

- Similarity metric: **Cosine similarity**
- Given a query image → retrieve top-K similar artworks

---

## 📈 Results

### 🔹 Quantitative Metrics

| Metric | Score |
|--------|------|
| Top-1 Accuracy | 5.5% |
| Top-3 Accuracy | 10.3% |
| Top-5 Accuracy | 12.5% |
| Precision@5 (Our Model) | 0.154 |
| Precision@5 (CLIP) | 0.236 |

---

### 🔹 Observations

- The model captures **visual similarity** (pose, lighting, composition)
- It struggles with **exact artist identification**
- CLIP performs better due to **large-scale pretraining**

---

## 🤖 Model Comparison

| Aspect | Our Model | CLIP |
|-------|----------|------|
| Training | Triplet Loss | Large-scale pretraining |
| Strength | Style-specific similarity | Semantic understanding |
| Weakness | Low artist accuracy | Less domain-specific |

---

## 🎯 Key Insight

> The embedding space clusters paintings based on visual similarity rather than strictly separating artists.

---

## ✅ Conclusion

This project demonstrates that metric learning can effectively capture visual similarity in artworks, while large pretrained models like CLIP provide stronger generalization. The comparison highlights trade-offs between domain-specific learning and large-scale pretraining.

---

## ⚠️ Limitations

- Limited training data (~4000 images)
- No hard negative mining
- Focuses on low-level features (color, texture)

---

## 🔮 Future Work

- Use **contrastive learning (SimCLR / CLIP fine-tuning)**
- Add **hard negative mining**
- Increase dataset size
- Incorporate **multimodal features**

---

## 🛠️ Tech Stack

- Python
- PyTorch
- torchvision
- scikit-learn
- matplotlib

---

## 📌 How to Run

```bash
# Clone repo
git clone https://github.com/your-username/artwork-similarity-metric-learning.git

# Install dependencies
pip install -r requirements.txt

# Run notebook
jupyter notebook
