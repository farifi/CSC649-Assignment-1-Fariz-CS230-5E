# User Stories
## US1: Upload a usable photo
As a council officer, I want to upload a photo of an Angsana tree and be told right away if the photo is too dark or blurry, so that I only get a result from a photo the system can actually read. **(FR1, FR2)**

**Acceptance criteria:**
- The user can upload a JPG or PNG photo taken with a phone.
- If the photo is too dark or too blurry, the system rejects it and shows a message asking for another photo.
- A rejected photo is not sent to the CNN, so no risk level is shown for it.

## US2: Get a risk level fast
As a council officer, I want to see a risk level (low, moderate or high) with the defects found in the photo, so that I can decide which trees to inspect first. **(FR3, FR4, NFR1)**

**Acceptance criteria:**
- After a valid upload, the result shows exactly one risk level: low risk, moderate risk or high risk.
- The result lists the visible defects the CNN detected (for example trunk cavity, crack, leaning, dead branches).
- The result appears within 10 seconds of the upload.

## US3: See why the AI said that
As a council officer, I want to see a confidence score and a highlight on the part of the photo that influenced the result, so that I can check whether the AI is looking at a real defect. **(FR5, FR6)**

**Acceptance criteria:**
- The result shows a confidence score as a percentage next to the risk level.
- A highlight (heatmap) is drawn on top of the original photo over the region that influenced the prediction.
- The user can switch the highlight on and off to see the original photo.

## US4: Be told when to call an arborist
As a landscape staff member, I want the system to recommend a detailed arborist inspection for high-risk trees, so that dangerous trees are not left unchecked. **(FR8, FR9)**

**Acceptance criteria:**
- When the risk level is high, the result shows a clear recommendation for a detailed arborist inspection.
- The recommendation is not shown for low risk results.
- Every result states that the system only checks visible signs and that a low-risk result does not rule out hidden decay.

## US5: Arborist has the final say
As an arborist, I want to confirm or change the AI risk level after reviewing the photo, so that the final decision stays with a qualified person. **(FR7, NFR4)**

**Acceptance criteria:**
- Only a logged-in user can confirm or change a risk level. A visitor who is not logged in cannot see the confirm or change option.
- When the arborist changes the level, the new level is saved and the original AI level is still visible.
- The result shows who confirmed or changed it and when.

## US6: Easy for a new officer
As a new council officer, I want to assess a tree in a few simple steps without training, so that I can start using the system right away. **(NFR3)**

**Acceptance criteria:**
- A first-time user can go from opening the system to seeing a risk result in no more than 5 steps.
- Each step has one clear action on the screen (for example Upload photo, then View result).

## US7: Trust the model's accuracy
As a research or technical expert, I want to see how well the model finds high-risk trees on unseen photos, so that I can judge whether it is safe to use as a first screening tool. **(NFR2)**

**Acceptance criteria:**
- The evaluation report shows precision, recall, F1-score and a confusion matrix on the test set.
- Recall on the high-risk class is at least 80% on the test set.
- The test set photos are not used for training.
