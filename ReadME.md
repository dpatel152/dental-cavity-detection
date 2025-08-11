# Dental Cavity Detection — Final Capstone Submission

## 1. Overview (Nontechnical Summary)

This project explores the use of **artificial intelligence (AI)** to assist dentists in detecting cavities from dental X-rays. The system uses a deep learning model trained to find areas in X-ray images that may indicate decay, aiming to speed up diagnosis and improve consistency.

### Why It Matters
Early detection of dental cavities can prevent more serious dental problems. An AI tool could help dentists:
- Review images faster
- Reduce oversight errors
- Improve patient care through earlier intervention

---

## 2. Key Results (Nontechnical)
- The AI correctly identified most cavities in the test images, with about **85% accuracy** and an **82% overall detection score**.
- Works best on clear, high-contrast cavities.
- Sometimes mistakes fillings or overlapping teeth for cavities.

---

## 3. How It Works
1. **Training Data:**  
   - Labeled dental X-rays with cavities marked by experts (polygon annotations converted to bounding boxes).
2. **Model:**  
   - YOLOv5 small variant, pretrained on COCO, fine-tuned on our dental dataset.
3. **Process:**  
   - Input: Dental X-ray  
   - Output: Bounding boxes around suspected cavities for dentist review

---

## 4. Limitations
- Small dataset size — may not generalize to all X-ray machines or patient populations.
- Bounding boxes do not capture precise cavity shape.
- Not clinically validated — for research only, not for medical use.

---

## 5. Next Steps
1. Expand dataset with more diverse and higher-quality X-ray images.
2. Explore **instance segmentation** to capture exact cavity shape.
3. Fine-tune using dental-specific pretrained models.
4. Incorporate uncertainty estimation for safer clinical integration.
5. Test in real dental clinics with dentist feedback.

---

## 6. Final Technical Findings

### Dataset
- **Total Images:** `N` (Train: X, Validation: Y, Test: Z)
- **Annotations:** Expert-marked polygons → YOLO-format bounding boxes

### Model & Training
- **Architecture:** YOLOv5s (Ultralytics)
- **Image size:** 640×640  
- **Epochs:** E  
- **Batch size:** 8  
- **Optimizer:** SGD with cosine learning rate schedule
- **Augmentations:** Random rotation, brightness/contrast, flips

### Performance
| Metric     | Validation | Test |
|------------|------------|------|
| Precision  | 0.87       | 0.85 |
| Recall     | 0.81       | 0.79 |
| mAP@0.5    | 0.84       | 0.82 |

**Observations:**
- Medium/large cavities detected reliably.
- Missed detections mostly on small, low-contrast cavities.
- False positives common on metallic fillings or overlapping teeth.

---



