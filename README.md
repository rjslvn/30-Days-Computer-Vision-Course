# 30-Day Plan for Learning Computer Vision
by Rajan Selvan (& gpt4) 
-- 
```import cv2
import numpy as np

# Load YOLO
net = cv2.dnn.readNet("yolov3.weights", "yolov3.cfg")
layer_names = net.getLayerNames()
output_layers = [layer_names[i[0] - 1] for i in net.getUnconnectedOutLayers()]

# Open webcam
cap = cv2.VideoCapture(0)

while(cap.isOpened()):
    ret, frame = cap.read()
    if ret:
        height, width, channels = frame.shape

        # Detecting objects
        blob = cv2.dnn.blobFromImage(frame, 0.00392, (416, 416), (0, 0, 0), True, crop=False)
        net.setInput(blob)
        outs = net.forward(output_layers)

        # Information to show on the screen
        class_ids = []
        confidences = []
        boxes = []
        for out in outs:
            for detection in out:
                scores = detection[5:]
                class_id = np.argmax(scores)
                confidence = scores[class_id]
                if confidence > 0.5:
                    # Object detected
                    center_x = int(detection[0] * width)
                    center_y = int(detection[1] * height)
                    w = int(detection[2] * width)
                    h = int(detection[3] * height)
                    x = int(center_x - w / 2)
                    y = int(center_y - h / 2)
                    boxes.append([x, y, w, h])
                    confidences.append(float(confidence))
                    class_ids.append(class_id)

        indexes = cv2.dnn.NMSBoxes(boxes, confidences, 0.5, 0.4)
        for i in range(len(boxes)):
            if i in indexes:
                label = str(classes[class_ids[i]])
                confidence = confidences[i]
                cv2.rectangle(frame, (x, y), (x + w, y + h), (255,0,0), 2)
                cv2.putText(frame, label, (x, y + 30), font, 2, (255,0,0), 2)

        cv2.imshow('frame',frame)
        if cv2.waitKey(1) & 0xFF == ord('q'):
            break
    else:
        break

cap.release()
cv2.destroyAllWindows()
```

### Suggested Folder Structure

```
30-Day_Plan/
|-- Week_1_Foundation_Assessment/
|   |-- Self_Assessment/
|   |-- Resource_Compilation/
|   |-- Study_Schedule/
|-- Week_2_Deep_Dive_Skill_Acquisition/
|   |-- Targeted_Learning/
|   |-- Practical_Application/
|   |-- Peer_Review_Feedback/
|-- Week_3_Refinement_Networking/
|   |-- Advanced_Materials/
|   |-- Networking/
|   |-- Mock_Interviews_Role_Play/
|-- Week_4_Finalization_Application/
|   |-- Portfolio_Resume_Building/
|   |-- Job_Applications/
|   |-- Continuous_Learning_Followups/
|-- Estimation_Functions/
|-- Tips/
```

## Table of Contents

1. [Week 1: Foundation Assessment](#week-1-foundation-assessment)
2. [Week 2: Deep Dive & Skill Acquisition](#week-2-deep-dive--skill-acquisition)
3. [Week 3: Refinement & Networking](#week-3-refinement--networking)
4. [Week 4: Finalization & Application](#week-4-finalization--application)
5. [Estimation Functions](#estimation-functions)
6. [Tips](#tips)

---

## Week 1: Foundation Assessment

### Self Assessment

- `knowledge_evaluation.md`: Document to evaluate your current understanding of computer vision. Include a pre-assessment quiz.
  
  \[
  \text{Knowledge Score} = \frac{\text{Correct Answers}}{\text{Total Questions}} \times 100
  \]

- `objectives.md`: List of objectives and goals you aim to achieve by the end of the 30-day period.

### Resource Compilation

- `books.txt`: List of essential books for computer vision.
- `courses.txt`: List of online courses and tutorials.
- `webinars.txt`: Schedule and links to relevant webinars.

### Study Schedule

- `daily_schedule.md`: Hourly breakdown of your daily study routine.
- `study_plan.md`: Weekly study plan detailing what to cover.

---

## Week 2: Deep Dive & Skill Acquisition

### Targeted Learning

- `key_areas.md`: Specific areas within computer vision to focus on.
- `learning_techniques.md`: Effective learning methods and techniques.

### Practical Application

- `mini_projects/`: Folder containing small projects to apply what you've learned.
- `exercises/`: Set of exercises to practice skills.

### Peer Review Feedback

- `peer_reviews.md`: Reviews from peers on your projects and exercises.
- `feedback.md`: Your reflections on the feedback received.

---

## Week 3: Refinement & Networking

### Advanced Materials

- `advanced_resources.md`: List of advanced materials for deep diving.
- `research_papers.txt`: Collection of research papers to read.

### Networking

- `contacts.md`: List of industry contacts.
- `meetups.txt`: Information on relevant meetups and events.

### Mock Interviews & Role Play

- `mock_interview_questions.md`: Set of potential interview questions.
- `role_play_scenarios.md`: Scenarios for role-playing interviews.

---

## Week 4: Finalization & Application

### Portfolio & Resume Building

- `portfolio.md`: Guide on building your portfolio.
- `resume.md`: Resume tailored for computer vision roles.

### Job Applications

- `job_applications.md`: List of jobs to apply for.
- `customized_applications.md`: Customized cover letters and applications.

### Continuous Learning & Follow-ups

- `ongoing_learning.md`: Plan for continued learning.
- `follow_ups.md`: Follow-up actions post the 30-day period.

---

## Estimation Functions

- `knowledge_increase_formula.md`: Formula to estimate knowledge increase.

  \[
  \text{Knowledge Increase} = \frac{\text{Post-Assessment Score} - \text{Pre-Assessment Score}}{\text{Pre-Assessment Score}} \times 100
  \]

- `role_offer_ability_formula.md`: Formula to estimate job offer potential.

  \[
  \text{Job Offer Ability} = \text{Knowledge Increase} \times \text{Networking Factor}
  \]

---

## Tips

- `weightage_tips.md`: Tips on allocating time effectively.
- `adaptive_strategies.md`: Strategies for adapting the plan based on progress.
- `reflection_tips.md`: Tips for reflective practices.

---
