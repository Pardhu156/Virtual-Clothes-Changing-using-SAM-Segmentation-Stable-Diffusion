# 👗 Virtual Clothes Changing using SAM Segmentation & Stable Diffusion

This repository implements a **virtual clothes-changing system** using:

- **SAM (Segment Anything Model)** for high-accuracy clothing segmentation  
- **Stable Diffusion (Img2Img)** for generating new clothing styles  
- Image preprocessing & mask refinement  
- End-to-end pipeline to replace the clothing on a person while keeping facial identity intact  

---

## 📌 Project Overview

The goal of this project is to:

- Detect and extract the clothing region (shirt/top/jacket) from an image  
- Generate a mask using **Meta’s SAM model**  
- Replace the segmented region using **Stable Diffusion**  
- Maintain:
  - Original background  
  - Person’s pose  
  - Face structure  
- Produce a realistic output where only the clothes are changed  

This solution can be used for:
- Virtual try-on  
- Fashion editing  
- E-commerce previews  
- Digital content creation  

---

## 🧩 Pipeline Summary

### **1️⃣ Image Input**
User uploads an image of a person.

### **2️⃣ Segmentation using SAM**
- SAM automatically segments the region of interest  
- IOU ~ **0.90–0.95+** for high accuracy  
- Mask is extracted and cleaned  

### **3️⃣ Mask Refinement**
- Convert mask to binary  
- Optionally dilate/erode to avoid leaks  
- Prepare masked area for the diffusion model  

### **4️⃣ Stable Diffusion Editing**
- Use Stable Diffusion Img2Img / Inpainting  
- Prompt example:
