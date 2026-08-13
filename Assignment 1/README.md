# User Authentication using Biometric Features
## Advanced Biometric Systems and Security (AI461) - Assignment 1

**Name:** Jaival Chauhan (U23AI035)

### Objective
This repository contains the implementation for Assignment 1, focusing on the performance evaluation of a biometric authentication system. The goal is to compute, visualize, and compare the performance of Euclidean distance and Cosine similarity in matching biometric feature vectors.

### Dataset Overview
*   **Total Users:** 100
*   **Samples per User:** 10 images (5 for enrollment, 5 for testing)
*   **Feature Vector Dimensions:** 144 features per sample
*   **Total Samples:** 1000

### Implementation Details
The evaluation follows the standard biometric pipeline established in the assignment parameters:

1.  **Data Processing:** 
    *   The `biomet_data.csv` file is loaded and transposed to appropriately map the 1000 samples against their 144 extracted features.
2.  **Dataset Split:**
    *   **Enrollment Set:** The first 5 image samples (indices 1-5) for each user are grouped for training.
    *   **Test Set:** The remaining 5 image samples (indices 6-10) captured 6 months later are held out for testing.
3.  **Template Generation:**
    *   A single robust template is created for each of the 100 users by calculating the arithmetic mean of their 5 enrollment feature vectors.
4.  **Evaluation Protocol:**
    *   Each of the 500 test samples is matched against all 100 generated templates, yielding a 500 x 100 distance matrix.
    *   **Genuine Comparisons:** 500 (matching a user's test sample against their own template).
    *   **Impostor Comparisons:** 49,500 (matching a test sample against all other users' templates).
5.  **Metrics Computed:**
    *   Genuine and Impostor Score Distributions
    *   False Acceptance Rate (FAR) and False Rejection Rate (FRR)
    *   Receiver Operating Characteristics (ROC) Curve
    *   Equal Error Rate (EER) and Decidability Index ($d^\prime$)

### Results & Conclusion

| Metric | Euclidean Distance | Cosine Similarity |
| :--- | :--- | :--- |
| **Equal Error Rate (EER)** | 11.56% | **8.46%** |
| **Decidability Index ($d^\prime$)** | 1.7622 | **1.9259** |

**Conclusion:** Cosine similarity outperforms Euclidean distance for this specific biometric feature set. It demonstrates better inter-class and intra-class separability (indicated by the higher Decidability Index of ~1.93) and provides a substantially lower Equal Error Rate (~8.46%), making it the superior distance metric for minimizing both false acceptances and false rejections in this system.

### Repository Files
*   `biomet_data.csv` - The original feature vector dataset.
*   `README.md` - Implementation explanations and results overview.
*   `biometrics_evaluation.png` - Visualizations encompassing A-E assignment requirements (Distributions, FAR/FRR, ROC).

