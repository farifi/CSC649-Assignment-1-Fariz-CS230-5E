# Technology Brief: AI-Based Tree Risk Assessment Using CNN

**Technology:** Computer vision: Convolutional Neural Network (ResNet-50 with transfer learning).

## Reason for this technology
Tree risk assessment in Malaysia relies mainly on physical observation of decay, cracks, canopy imbalance, leaning and soil conditions (Bernama, 2026a). Fatima et al. (2026) note that visual tree assessment is labour intensive and time consuming, it's can lead to human error depending on the arborist skills, and tools such as resistographs are costly. A CNN can learn to recognise visible defects from photos, giving a faster and more consistent first screening that helps arborists decide where to look first, but they're not replacing the arborist, it will be just a tool for arborist to be able to work with more ease and faster.

## Core idea
A user uploads a photo of an tree. The CNN then will classifies visible defects and give a risk level with confidence score. The part of the tree defects will be highlight by the system. Suspicious trees will be flagged as high risk for inspection by arborist. The system supports the arborist's decision and does not replace it.

## Basic flow
1. Upload a photo of the trunk, base and canopy.
2. Check photo quality.
3. Preprocess: resize to the network input size and normalise.
4. ResNet-50 classifies defects and risk level and returns a confidence score.
5. Create a highlight of the influential image region.
6. Show the result, for high risk and suspicious trees, will suggest for inspection.
7. An arborist reviews and confirms or changes the result.

## Examples of tree defects
Defects reported in Malaysian sources include trunk cracks, decay, disease, weird leaning angle and asymmetric canopy shape (Bernama, 2026a), and rotting roots, trunk base cavity and soil compaction (Bernama, 2026b). Some are visible warning signs of hidden problems, for example the cavity at trunk base, leaning or dead branches, CNN can use these to learn to recognise. However, internal decay and root damage are difficult to detect from images from the outside.

This project focuses on Angsana tree as it very common urban tree in Malaysia. Root rot, trunk cavities, soil compaction and limited space at roots have been linked to Angsana failures recently (The Star, 2026a), and if the roots spread sideways near the surface, its makes it very vulnerable for construction works around it (The Star, 2026b).

## Methods, models and tools
| Item | What it is used for |
| --- | --- |
| ResNet-50 | Main CNN model that learns defect features and classifies risk level |
| Transfer learning | Start from pretrained weights and fine-tune on a small Angsana photo set, so less data is needed |
| Data augmentation (rotation, flipping, brightness change) | Increases photo variety and reduces overfitting; used by Fatima et al. (2026) with a small dataset |
| Precision, recall, F1-score and confusion matrix | Measure model performance; recall on the high-risk class matters most |
| Grad-CAM (proposed) | Highlights the image region that influenced a prediction |
| PyTorch or TensorFlow, OpenCV, scikit-learn | Build and train the model, handle images and calculate metrics |

## 7. Fit to the problem
**Benefits:** faster, more consistent first screening; lower cost than specialised equipment; results can be reviewed by arborists; the photo can be taken with a phone.

**Risks and limitations:**
- **Small, single-species data:** Fatima et al. (2026) used 453 ash tree images and acknowledge that generalisation to other species is untested. This project limits scope to Angsana, but it will still need its own labelled Angsana photos, and no ready public Angsana defect dataset has been identified.
- **Hidden causes:** Angsana failures are often linked to root rot (The Star, 2026a), which cannot be measured from photos outside of the tree. The system can only detect visible warning signs, so a "low risk" result does not rule out hidden decay.
- **Image quality:** occlusion, lighting, camera distance and angle reduced accuracy in Fatima et al. (2026).
- **Proxy risk:** a CNN output estimates relative risk, it does not give the probability that a tree will fail.
- **Human review needed:** a wrong "low risk" result has safety consequences.

**Alternative approach:** sensor-based monitoring. Putrajaya uses 100 IoT tilt sensors on high-risk trees (Perbadanan Putrajaya, 2026), and DBKL plans at least 200 sensors (Malay Mail, 2026). Sensors give continuous real-time data but need hardware, networks and funding, and cover only selected trees. A CNN is cheaper to start but gives a snapshot and cannot see hidden defects. **Choice:** a CNN for low-cost screening, with arborists confirming high-risk cases and sensors where budget allows.

References are listed in [References.md](Documents/References.md).