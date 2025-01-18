# TamilHRNet: A Novel Approach for Tamil Handwritten Document Recognition

Handwriting recognition is pivotal in preserving and digitizing cultural heritage, especially for languages like Tamil, one of the oldest languages still in use. Tamil holds immense cultural and historical significance, and its script is known for its diverse shapes, curves, and complex stroke patterns, which represent a unique challenge for handwritten document digitization. 

The cursive nature of Tamil script and the wide variability in handwriting styles further complicate recognition efforts. Current Optical Character Recognition (OCR) systems often struggle with these complexities, resulting in limited accuracy.

## Proposed Approach
To address these challenges, we propose **TamilHRNet**, a novel approach for handwritten Tamil document recognition. Our method introduces a **Tri-Phase Segmentation Framework**, which systematically segments documents into:

1. **Sentences**
2. **Words**
3. **Individual Characters**

This framework applies specialized segmentation models at each phase to extract detailed patterns, significantly enhancing character isolation and recognition. The network’s three stages work in tandem, progressively refining the input data for optimal recognition.

## Key Features
- **Attention Mechanisms**: TamilHRNet incorporates attention mechanisms to effectively handle the nuances of Tamil script.
- **High Accuracy**: Achieved a recognition accuracy of **96.18%**.
- **Datasets Used**: Trained and tested using the **uTHCD** and **HP Labs Offline Tamil Datasets**.

## Conclusion
This work offers a promising solution for the digitization of Tamil handwritten documents, ensuring that this rich linguistic and cultural heritage is preserved and accessible for future generations.
