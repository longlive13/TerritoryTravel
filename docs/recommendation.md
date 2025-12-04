## Recommendation

### 1. Data Sources

- **(1) National Tourism Information (Korean Public Data Portal)**
  - Official tourism regions and districts designated by metropolitan mayors  
  - Source: https://www.data.go.kr/data/15021141/standard.do  

- **(2) References for Synthetic User Generation**
  - **Seasonal preference of Koreans by age and gender**  
    - Source: Gallup Korea  
    - https://www.gallup.co.kr/gallupdb/reportContent.asp?seqNo=1478  
  - **Preferred travel categories (Culture / Nature / Experience / History)**  
    - Paper: *A Study on Travel Activity and Shopping Behavior of 20’s–30’s Korean Overseas Travelers*  
    - Journal: Fam. Environ. Res., Vol. 54, No. 5, 2016, pp. 529–539  
    - DOI: http://dx.doi.org/10.6115/fer.2016.041  

Using insights from these studies, I generated **10,000 synthetic users** with realistic distributions over:
- Age groups  
- Gender  
- Preferred seasons  
- Preferred travel categories  

---

### 2. Automatic Labeling of Tourism Data

I automatically labeled each tourism spot with:

- **Category:** `Culture / Nature / Experience / History`
- **Recommended season**

This was done using a rule-based preprocessing pipeline in **Google Colab** (keyword-based mapping on the raw tourism dataset), and the final labeled data was exported as a structured JSON file for use in the backend.

---

### 3. Recommendation System v1 — Content-Based Filtering

The first version of the recommendation engine is a **content-based, score-based model**.

#### 3.1 Backend Logic

- Designed the **DTOs and service layer** for personalized travel recommendations.
- Built a **rule-based scoring system** that evaluates ~850 officially designated tourism spots  
  (tourism regions and districts defined by metropolitan mayors; special tourism zones excluded).
- Preprocessed and labeled raw tourism data in Google Colab:
  - Normalized spot categories into **Culture / Nature / Experience / History**
  - Assigned **recommended seasons** using keyword-based mapping  
  - Converted the final dataset to a structured **JSON file** for fast lookup in the backend

#### 3.2 Scoring Model

Each spot receives a score based on:

- **Preferred category match:** `+30`
- **Preferred season & current season match:** `+20`
- **Age group match:** `+15`
- Additional heuristic weights for:
  - Regional relevance
  - Diversity across recommended regions

The system then selects the **top 3 spots** for each user.

#### 3.3 GPT-Powered Itinerary Generation

For the top 3 spots, the backend calls the **GPT API** to generate a natural-language **one-day itinerary**, including:

- Narrative explanation of the trip
- Recommended visit order
- Contextual notes
- Safety / caution points

#### 3.4 Frontend Integration

- Exposed the recommendation logic via a backend API.
- Integrated the API into the Vue frontend and implemented a **home-screen popup** that displays:
  - The recommended spots
  - The generated one-day itinerary

### 4. Recommendation System v2 — User-Based Collaborative Filtering (In Progress)

This version explores a **User-Based Collaborative Filtering (User-Based CF)** approach using **10,000 synthetic users** generated from demographic and preference statistics.

**Concept:**  
Recommend tourism spots that *similar users are likely to prefer*.  
This is based on the core CF idea that:

> *“Users with similar preferences will like similar items.”*

#### 4.1 Vector-Based Preference Modeling

Each user and tourism spot is represented as a vector:

- **User preference vector:**  
  Encodes the user’s preferred category, season, and age group  
- **Spot feature vector:**  
  Encodes the spot’s category and recommended season

Using these vectors, we compute:

