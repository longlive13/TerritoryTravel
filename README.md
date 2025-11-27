# TerritoryTravel 🌍  
*A gamified travel exploration platform where users conquer regions, receive personalized travel recommendations, share their daily moments, decorate their own territory map, and climb the ranking leaderboard by earning points from conquests and social interactions*

## ✨ Key Features

- **Territory Conquest**
  - Users can conquer regions they have visited and visualize them on an interactive map.

- **Personalized Travel Recommendation**
  - Recommends tourist spots and one-day courses based on user profile, preferences, and current season.

- **Ranking System**
  - Global / regional leaderboard based on the number of conquered regions.

- **Point System**
  - Users earn points by:
    - Conquering new regions
    - Receiving likes on their feed posts
  - Points are stored and updated in a dedicated point log and total point table.

- **Decoration Shop**
  - In-app shop where users can spend their points to buy items used to decorate their conquered territory map.
    
- **Social Feed**
  - Users can create posts with photos and text, similar to an Instagram-style feed, allowing them to share their travel moments and interact with others through likes.


## 🧑‍💻 My Contributions

I was responsible for both the **backend core logic** and several **frontend (Vue) features**, with a major focus on the recommendation, ranking, and point systems.

- **Recommendation Engine (Backend + GPT Integration + Frontend UI)**
  - Designed the DTOs and service layer for personalized travel recommendations.
  - Built a **rule-based scoring system** that evaluates ~850 officially designated tourism spots
    (tourism regions and districts defined by Metropolitan Mayors; excluding special tourism zones).
  - Preprocessed and labeled raw tourism data in Google Colab:
    - Normalized spot categories into **Culture / Nature / Experience / History**
    - Assigned **recommended seasons** using keyword-based mapping  
    - Converted the final dataset to a structured JSON file for fast lookup in the backend
  - Implemented a scoring model assigning points based on:
    - **Preferred category match (+30)**  
    - **Preferred season & *Current season match (+20)**  
    - **Age match (+15)**  
    - Additional heuristic weights for region relevance and diversity
  - Selected the top 3 scored spots and generated a **natural-language one-day itinerary** by calling the **GPT API**, including:
    - Smooth narrative explanation  
    - Visit order suggestion  
    - Contextual notes and **safety/caution points**
  - Integrated the recommendation API into the frontend, enabling users to view their suggested itinerary in a **popup on the home screen**.

- **Ranking System (Backend + Frontend)**
  - Built the ranking logic based on conquered regions and accumulated user points.
  - Developed APIs and implemented the leaderboard UI in Vue.

- **Point System (Backend  + Frontend)**
  - Designed and implemented a multi-rule point mechanism, including:
    - **+5 points** for conquering a new region (동 단위)
    - **+10 bonus points** when conquering a region with fewer than 100 conquerors in the current month
    - **+5 points** when receiving a like on a feed post
  - Implemented point deduction logic for in-app shop purchases.
  - Built APIs for retrieving a detailed point transaction history (earnings, deductions, event types).
  - Managed point logs and maintained users’ total accumulated points for ranking and shop usage.

- **Frontend Development (Vue)**
  - Developed UI components for:
    - Recommendation popup  
    - Ranking leaderboard  
    - Territory conquest visualization  
    - Point display and shop interaction  
  - Ensured smooth communication between backend APIs and frontend components.


Tech Stack (BE/FE/AI/Infra)

Project Architecture (선택)

Screenshots / Demo (선택)

Folder Structure (선택)

How to Run (로컬 실행 방법)

API Overview (선택)

Data & Recommendation Engine (너 프로젝트 핵심✨)
