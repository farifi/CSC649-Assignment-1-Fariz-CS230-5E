# Requirements (Draft)

## Functional Requirements
- FR1: The system shall let a user upload a photo of an Angsana tree.
- FR2: The system shall reject a photo that is too dark or too blurry and ask for another.
- FR3: The system shall classify visible defects and warning signs in the photo using a CNN.
- FR4: The system shall assign each tree a risk level such as low risk, moderate risk or high risk.
- FR5: The system shall show a confidence score and highlight the part of the photo that influenced the result which is the tree defects.
- FR6: The system shall let an arborist confirm or change the AI risk level.
- FR7: The system shall recommend a detailed arborist inspection when a tree is rated high risk.

## Non-Functional Requirements
- NFR1 (Performance): The system shall return a risk result within 10 seconds of a photo upload.
- NFR2 (Accuracy): The model shall achieve at least 80% recall on the high-risk class on the test set.
- NFR3 (Usability): A new officer shall be able to assess a tree in no more than 5 steps.
- NFR4 (Security): Only authenticated users shall be able to edit or confirm risk levels.