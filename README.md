# TamilHRNet: A Novel Approach for Tamil Handwritten Document Recognition

Handwriting recognition is pivotal in preserving and digitizing cultural heritage, especially for languages like Tamil, one of the oldest languages still in use. Tamil holds immense cultural and historical significance, and its script is known for its diverse shapes, curves, and complex stroke patterns, which represent a unique challenge for handwritten document digitization. 

The cursive nature of Tamil script and the wide variability in handwriting styles further complicate recognition efforts. Current Optical Character Recognition (OCR) systems often struggle with these complexities, resulting in limited accuracy.

## Proposed Approach
To address these challenges, we propose **TamilHRNet**, a novel approach for handwritten Tamil document recognition. Our method introduces a **Tri-Phase Segmentation Framework**, which systematically segments documents into:

1. **Sentences**
2. **Words**
3. **Individual Characters**

This framework applies specialized segmentation models at each phase to extract detailed patterns, significantly enhancing character isolation and recognition. The network’s three stages work in tandem, progressively refining the input data for optimal recognition. Once the characters are segmented, is then passed onto the Attention-Backed Neural Network Model which is then used to predict the characters and group them together in the same-way as they appear in the document.

## Key Features
- **Attention Mechanisms**: TamilHRNet incorporates attention mechanisms to effectively handle the nuances of Tamil script.
- **High Accuracy**: Achieved a recognition accuracy of **96.18%**.
- **Datasets Used**: Trained and tested using the **uTHCD** and **HP Labs Offline Tamil Datasets**.

## Performance Comparison

1. With Other Existing state-of-the-art Models

| Methods                          | Accuracy (%) | Precision (%) | Sensitivity (%) | Specificity (%) | F1-Score (%) |
|----------------------------------|--------------|---------------|------------------|-----------------|--------------|
| **Proposed TamilHRNet Model**       | **96.18**        | **95.70**         | **95.50**           | **99.80**          | **95.53**        |
| DNN- VGG Model [9]              | 92.93        | 93.76         | 93.29           | 92.97          | 93.88        |
| DNN- Inception Model            | 94.99        | 92.42         | 91.32           | 91.08          | 92.00        |
| DNN- DenseNet Model [9]         | 91.04        | 92.76         | 94.48           | 92.76          | 90.75        |
| Clustering-Group-Wise Method [11] | 89.66       | 90.21         | 91.40           | 91.59          | 90.73        |
| SVM Algorithm [11]              | 82.04        | 81.17         | 79.90           | 81.22          | 80.96        |
| Elephant Herd Opt. Algorithm [12]| 76.84        | 76.06         | 75.65           | 76.63          | 77.38        |
| SALA Algorithm [12]             | 86.39        | 85.11         | 87.03           | 86.69          | 86.92        |


2. Abelation Studies
   
| MODEL                          | TEST ACCURACY | PRECISION | SENSITIVITY | SPECIFICITY | F1-SCORE |
|--------------------------------|---------------|-----------|-------------|-------------|----------|
| **CNN+CBAM+SA+DCA (Chosen Model)** | **0.9618**         | **0.957**     | **0.955**       | **0.999**       | **0.955**    |
| CNN+CBAM+SA                   | 0.957         | 0.952     | 0.951       | 0.997       | 0.951    |
| CNN+CBAM                      | 0.901         | 0.900     | 0.894       | 0.994       | 0.895    |
| CNN+SA+DCA                    | 0.875         | 0.877     | 0.868       | 0.993       | 0.869    |
| CNN+SA                        | 0.928         | 0.926     | 0.922       | 0.995       | 0.922    |
| CNN+DCA                       | 0.916         | 0.915     | 0.915       | 0.998       | 0.911    |


# The Tri-Stage Segmentation Process
First, the document is segmented into lines by using a larger blur kernel to merge closely spaced words into continuous lines. Dilation along the x-axis fills gaps between words, ensuring proper line segmentation. In the second stage, the lines are split into words using a smaller blur kernel, and vertical dilation ensures that diacritical marks are grouped with their respective words. The words are then sorted based on their positions along the x-axis.

Finally, words are divided into individual characters. At this stage, fine details must be preserved, so a smaller blur kernel is used, and dilation is skipped to avoid merging adjacent characters. The merge_boxes function handles special cases, such as combining diacritical marks with their base characters. Contours are simplified with a low epsilon value to maintain accuracy, and bounding boxes are sorted horizontally to preserve character order.

The end result is a hierarchical 3D array representing the document's segmentation: lines, words, and characters. This structured segmentation facilitates efficient processing by a deep learning model and enables accurate document reconstruction. The array is then passed on to the TamilHRNet Model and the digitization of character is done!

![Picture16](https://github.com/user-attachments/assets/67a6870d-9d58-483c-9ef7-936d5b10f715)

# Attention-Backed Neural Network (TamilHRNet)

![image](https://github.com/user-attachments/assets/318e9ab9-4603-4ebe-ad97-34bce5902193)


## The attention mechanisms used in TamilHRNet include:

- **Convolutional Block Attention Module (CBAM)**:  
  CBAM is a lightweight, yet effective attention module that sequentially applies channel and spatial attention mechanisms. The **channel attention** focuses on the most critical feature maps by assigning higher weights to the channels that contribute most to the task, while the **spatial attention** highlights important regions within the feature maps. By combining these mechanisms, CBAM helps TamilHRNet identify and emphasize key patterns in handwritten Tamil characters, improving recognition accuracy.

- **Dense Channel Attention (DCA)**:  
  DCA extends the concept of channel attention by incorporating dense connections to enhance feature reuse and gradient flow. It assigns importance scores to channels dynamically and encourages the model to focus on subtle variations in character strokes and curves. This mechanism ensures that TamilHRNet can better capture the fine-grained details in complex handwriting styles, which are essential for distinguishing similar-looking Tamil characters.

- **Self-Attention (SA)**:  
  SA is a mechanism that computes attention weights based on the relationships between all elements in a feature map. It enables TamilHRNet to capture long-range dependencies and global context, which is crucial for understanding intricate script patterns and the spatial arrangement of strokes. By leveraging SA, the network can effectively model the relationships between different parts of a handwritten character, improving its ability to recognize challenging and cursive handwriting styles.

These attention mechanisms work together to address the complexities of Tamil handwriting, significantly enhancing the robustness and precision of TamilHRNet.

# Output

![Picture18](https://github.com/user-attachments/assets/15649d93-1524-459c-bf57-fff099e51445)




