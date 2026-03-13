# 🛍️ AI-FitStyler: Your Personal Multi-Agent Fashion Advisor

## Project Overview

AI-FitStyler is an innovative, web-based fashion recommendation system designed to provide **hyper-personalized outfit suggestions**. It leverages a **multi-agent architecture** to combine **Computer Vision (CV)** analysis of the user's physique (body type and skin tone) with a highly efficient **Retrieval-Augmented Generation (RAG)** engine for finding optimal, trend-aware, and budget-friendly outfits from a product catalog.

The system addresses major gaps in traditional online shopping by offering **speed, personalization, and actionable style advice**.

---

## 🚀 Key Features

- **Precision Body Analysis**  
  Uses **MediaPipe Pose** to detect body landmarks and determine the user's body type (slim, curvy, athletic) based on the hip-to-shoulder ratio.

- **Skin Tone & Color Palette Detection**  
  Uses **MediaPipe Face Mesh** and **LAB Color Space** analysis to identify skin tone (fair, wheatish, dark) and suggest a complementary color palette.

- **Rapid RAG Engine**  
  Utilizes **FAISS Vector Store** and **HuggingFace Embeddings** for ultra-fast and semantically relevant outfit retrieval from `catalog.csv`.

- **Trend Critique**  
  Provides a **Trend Score (7/10 to 10/10)** with a short fashion commentary for each suggestion.

- **User Interface**  
  Built using **Streamlit** for a clean, fast, and interactive user experience.

---

## ⚙️ System Architecture

AI-FitStyler follows a **Multi-Agent Architecture**, orchestrated using custom Python logic and LangChain modules.

### Workflow:

1. **Input**  
   - User uploads a photo  
   - Selects Gender, Occasion, and Budget  

2. **Analysis Agents (Computer Vision)**  
   - `body_analyzer.py`  
   - `skin_color_analyzer.py`

3. **Data & Retrieval Layer**  
   - `rag_system.py`  
   - Indexes the product catalog into a **FAISS Vector Store**

4. **Generation Agents (RAG)**  
   - `outfit_generator.py` – Performs semantic search  
   - `trend_critic.py` – Adds trend scoring and comments

5. **Output**  
   - Results displayed via `app.py` using Streamlit

---

## 🛠️ Installation and Setup

### Prerequisites

- Python 3.8 or higher  
- pip (Python package installer)

---

### Step 1: Clone the Repository

```bash
git clone <Your_Repo_URL>
cd AI-FitStyler
Step 2: Install Dependencies
All required libraries (MediaPipe, OpenCV, Streamlit, LangChain, FAISS, HuggingFace) are listed in requirements.txt.

bash
Copy code
pip install -r requirements.txt
Step 3: Build the RAG Index (Mandatory)
The system must process data/catalog.csv and build the FAISS vector index.

bash
Copy code
python core/rag_system.py
Expected Output:

rust
Copy code
RAG built and saved! Ready for queries.
Step 4: Run the Application
Launch the Streamlit interface:

bash
Copy code
streamlit run app.py
The application will open automatically in your browser at:
http://localhost:8501

👨‍💻 Usage
Set Preferences
Use the sidebar to select Gender, Occasion, and Budget.

Upload Photo
Upload a clear, full-body image for accurate body type and skin tone detection.

Analyze
The system displays detected:

Body Type

Skin Tone

Suggested Color Palette

Get Suggestions
Click "Get Outfit Suggestions!" to view personalized outfits with trend scores.

👥 Team Members
Name	Student ID
Maryyam Tanveer	BCSF23M007
Minahil Shahid	BCSF23M012
Hassan Ali Pansota	BCSF23M029
Fatima Mirza	BCSF23M031

🛑 Limitations & Future Scope
Limitation	Mitigation / Future Enhancement
Small Dataset	Expand catalog to 10,000+ entries
Dummy LLM Mode	Integrate real LLM (Ollama / xAI API)
No Persistence	Add database support (SQLite)
Image URLs	Improve error handling or use reliable APIs
No AR Try-On	Implement AR-based outfit overlay

markdown
Copy code

If you want:
- **shorter version for slides**
- **black theme presentation text**
- **report-style formatting**
- **diagram explanation**

Just tell me 👍






You said:
git hub hatao


ChatGPT said:
Theek hai 👍
Yeh GitHub ka reference completely hata kar clean copy-paste Markdown version hai:

markdown
Copy code
# 🛍️ AI-FitStyler: Your Personal Multi-Agent Fashion Advisor

## Project Overview

AI-FitStyler is an innovative, web-based fashion recommendation system designed to provide **hyper-personalized outfit suggestions**. It leverages a **multi-agent architecture** to combine **Computer Vision (CV)** analysis of the user's physique (body type and skin tone) with a highly efficient **Retrieval-Augmented Generation (RAG)** engine for finding optimal, trend-aware, and budget-friendly outfits from a product catalog.

The system addresses gaps in traditional shopping by offering **speed, personalization, and actionable style advice**.

---

## 🚀 Key Features

- **Precision Body Analysis**  
  Uses **MediaPipe Pose** to detect body landmarks and determine the user's body type (slim, curvy, athletic) based on the hip-to-shoulder ratio.

- **Skin Tone & Color Palette Detection**  
  Uses **MediaPipe Face Mesh** and **LAB Color Space** analysis to identify skin tone (fair, wheatish, dark) and suggest a complementary color palette.

- **Rapid RAG Engine**  
  Utilizes **FAISS Vector Store** and **HuggingFace Embeddings** for fast and semantically relevant outfit retrieval from `catalog.csv`.

- **Trend Critique**  
  Provides a **Trend Score (7/10 to 10/10)** with a short fashion commentary for each suggestion.

- **User Interface**  
  Built using **Streamlit** for a clean, fast, and interactive experience.

---

## ⚙️ System Architecture

AI-FitStyler follows a **Multi-Agent Architecture**, orchestrated using custom Python logic.

### Workflow:

1. **Input**  
   - User uploads a photo  
   - Selects Gender, Occasion, and Budget  

2. **Analysis Agents (Computer Vision)**  
   - `body_analyzer.py`  
   - `skin_color_analyzer.py`

3. **Data & Retrieval Layer**  
   - `rag_system.py`  
   - Indexes the product catalog into a **FAISS Vector Store**

4. **Generation Agents (RAG)**  
   - `outfit_generator.py`  
   - `trend_critic.py`

5. **Output**  
   - Personalized outfit suggestions displayed via `app.py`

---

## 🛠️ Installation and Setup

### Prerequisites

- Python 3.8 or higher  
- pip (Python package installer)

---

### Step 1: Install Required Libraries

All required libraries are listed in `requirements.txt`.

```bash
pip install -r requirements.txt
Step 2: Build the RAG Index (Mandatory)
The system processes data/catalog.csv and builds the FAISS vector index.

bash
Copy code
python core/rag_system.py
Expected Output:

rust
Copy code
RAG built and saved! Ready for queries.
Step 3: Run the Application
Launch the Streamlit interface:

bash
Copy code
streamlit run app.py
The application opens automatically at:
http://localhost:8501

👨‍💻 Usage
Set Preferences
Select Gender, Occasion, and Budget from the sidebar.

Upload Photo
Upload a clear, full-body image for accurate detection.

Analyze
The system displays:

Body Type

Skin Tone

Suggested Color Palette

Get Outfit Suggestions
Click "Get Outfit Suggestions!" to view results with trend scores.

👥 Team Members
Name	Student ID
Maryyam Tanveer	BCSF23M007
Minahil Shahid	BCSF23M012
Hassan Ali Pansota	BCSF23M029
Fatima Mirza	BCSF23M031

🛑 Limitations & Future Scope
Limitation	Mitigation / Future Enhancement
Small Dataset	Expand catalog to 10,000+ entries
Dummy LLM Mode	Integrate a real LLM (Ollama / xAI API)
No Persistence	Implement database support (SQLite)
Image URLs	Improve error handling or use reliable APIs
No AR Try-On	Add AR-based virtual try-on feature