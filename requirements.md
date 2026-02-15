# SmashVision AI: Design & Architecture

## 1. High-Level Architecture
The system follows a **Hybrid Edge-Cloud** approach to balance performance with the low-bandwidth constraints of rural India.

### **1.1 The 3-Zone Workflow**
1.  **Zone 1: The Athlete Loop (Edge AI)**
    * **Input:** User records a 30s drill on a smartphone.
    * **Privacy & Efficiency:** On-device TensorFlow Lite model performs a quality check and blurs faces (for privacy) before upload to save data costs.
2.  **Zone 2: The Intelligence Bridge (AWS Cloud)**
    * **Processing:** Video is uploaded to **Amazon S3**, triggering an **AWS Lambda** pipeline.
    * **Vision Engine:** **MediaPipe** extracts 33 skeletal keypoints; **OpenCV** maps court position.
    * **GenAI Coach:** **AWS Bedrock** interprets the biomechanical data into coaching text, which is then translated by **AWS Translate**.
3.  **Zone 3: National Scouting (Aggregated Data)**
    * **Dashboard:** Anonymized performance metrics feed into a "Talent Heatmap," allowing scouts to identify high-performing districts.

## 2. Technology Stack
* **Frontend:** Flutter (Dart) - for cross-platform support (Android/iOS).
* **Backend:** AWS Lambda (Serverless Python functions).
* **Storage:** Amazon S3 (Video storage), Amazon DynamoDB (User stats).
* **AI/ML:**
    * **Vision:** MediaPipe (Pose Estimation), OpenCV.
    * **LLM:** AWS Bedrock (Claude 3 / Titan) for coaching logic.
    * **Translation:** AWS Translate.
    * **Edge:** TensorFlow Lite.

## 3. User Interface (UI) Strategy
* **Visual-First:** Uses color-coded skeletons (Green=Good, Red=Bad) to explain errors visually, overcoming literacy barriers.
* **Voice-Enabled:** The AI Coach speaks the advice in the local language, ensuring accessibility.
* **Gamification:** Users earn "Skill Badges" (e.g., "Smash King") to maintain motivation.

## 4. Competitive Differentiation
| Feature | Competitors (e.g., SwingVision) | SmashVision AI (Ours) |
| :--- | :--- | :--- |
| **Hardware** | High-end Phones / Sensors | **Any Smartphone (Low-End Compatible)** |
| **Language** | English Only | **8+ Indian Languages** |
| **Cost** | Subscription ($$$) | **Freemium (Ad-supported / Govt partnered)** |
| **Metric Focus** | Match Scores / Line Calls | **Biomechanics & Skill Improvement** |
