AdPulse: Automated Insight Engine

**Tagline:** An automated reporting pipeline that converts raw ad campaign logs into executive-ready PDF briefings with AI-generated narratives in under 30 seconds.

---

### 1. The Problem (Real World Scenario)

**Context:** In the AdTech industry, reporting is a massive bottleneck. Account Managers currently spend 4-6 hours every week downloading CSVs from different DSPs, manually aggregating data in Excel, and taking screenshots to paste into PowerPoint decks.

**The Pain Point:**

1. **Latency:** Data is often days old by the time the client sees it.
2. **Error Rate:** Manual copy-pasting leads to human error in critical metrics like Spend and CPA.
3. **Wasted Talent:** Highly paid strategists are doing low-value data entry work instead of optimizing campaigns.

**My Solution:**
I built **AdPulse**, a streamlined insight engine. The user uploads a raw data file, and the system instantly standardizes the data, calculates the math deterministically, and uses Generative AI to write a strategic summary. The output is a finalized PDF ready to be emailed to a CMO.

---

### 2. Expected End Result

**For the User:**

* **Input:** Upload a raw CSV file (Campaign Performance Report).
* **Action:** Click "Generate Executive Report".
* **Output:** A downloadable, professional PDF containing:
  * Hard KPIs (Total Spend, Conversions, CPA) calculated with 100% precision.
  * An AI-written executive summary explaining *why* a specific campaign is winning or losing.

---

### 3. Technical Approach

I designed this system to prioritize **accuracy** and **speed**, moving away from "chatbots" to a functional business tool.

**System Architecture:**

1. **Ingestion Layer (Streamlit):**
    * Acts as the frontend interface for secure file handling.
    * Provides immediate visual feedback and data preview.

2. **Data Engine (Pandas):**
    * **Decision:** I chose Pandas over pure AI processing for the calculations.
    * **Reasoning:** LLMs are probabilistic and often fail at basic arithmetic (hallucinations). I strictly used Pandas for all aggregations (Sum, Avg, CPA calculation) to ensure financial accuracy.

3. **Intelligence Layer (Google Gemini):**
    * We pass the *aggregated metadata* (not the raw rows) to Google Gemini.
    * **Prompt Engineering:** Used a "Role-Playing" prompt to force the model to act as a Senior Analyst, focusing on actionable insights rather than generic observations.

4. **Reporting Engine (FPDF):**
    * Programmatically renders the final PDF. This ensures a consistent corporate layout that is difficult to achieve with simple HTML-to-PDF converters.

---

### 4. Tech Stack

* **Language:** Python 3.10+
* **Frontend:** Streamlit
* **Data Processing:** Pandas (NumPy backend)
* **AI Model:** Google Gemini API (via LangChain)
* **Document Generation:** FPDF
* **Environment Management:** Python Dotenv

---

### 5. How to Run

1. **Clone Repository**

    ```bash
    git clone https://github.com/manojkp08/GroundTruthAIHackathon2025_Manoj.git
    ```

2. **Install Dependencies**

    ```bash
    pip install -r requirements.txt
    ```

3. **Configure API Key**
    Create a `.env` file in the root directory:

    ```bash
    GEMINI_API_KEY="your_google_api_key_here"
    ```

4. **Run the Application**

    ```bash
    streamlit run app.py
    ```

5. **Test with Sample Data**
    * Use the `custom_csv/campaign_data.csv` provided in the repo to test the pipeline.
