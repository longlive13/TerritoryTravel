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
## 🛠 Tech Stack

### 💻 Backend  
![Java](https://img.shields.io/badge/Java-007396.svg?style=for-the-badge&logo=openjdk&logoColor=white) 
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F.svg?style=for-the-badge&logo=springboot&logoColor=white)
![Spring Cloud](https://img.shields.io/badge/Spring_Cloud-6DB33F.svg?style=for-the-badge&logo=spring&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F.svg?style=for-the-badge&logo=springsecurity&logoColor=white)
![JPA](https://img.shields.io/badge/JPA-59666C.svg?style=for-the-badge&logo=hibernate&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000.svg?style=for-the-badge&logo=jsonwebtokens&logoColor=white)
![MyBatis](https://img.shields.io/badge/MyBatis-B7178C.svg?style=for-the-badge)

### 🎨 Frontend  
![HTML5](https://img.shields.io/badge/HTML5-E34F26.svg?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6.svg?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E.svg?style=for-the-badge&logo=javascript&logoColor=black)
![ES6](https://img.shields.io/badge/ES6-F7DF1E.svg?style=for-the-badge&logo=javascript&logoColor=black)
![Vue.js](https://img.shields.io/badge/Vue.js-4FC08D.svg?style=for-the-badge&logo=vuedotjs&logoColor=white)
![Fetch API](https://img.shields.io/badge/Fetch_API-02569B.svg?style=for-the-badge)
![Axios](https://img.shields.io/badge/Axios-5A29E4.svg?style=for-the-badge)
![dayjs](https://img.shields.io/badge/day.js-EC4A3F.svg?style=for-the-badge)

### 🎨 Design  
![Figma](https://img.shields.io/badge/Figma-F24E1E.svg?style=for-the-badge&logo=figma&logoColor=white)

### 🗄️ Database  
![MariaDB](https://img.shields.io/badge/MariaDB-003545.svg?style=for-the-badge&logo=mariadb&logoColor=white)
![MyBatis](https://img.shields.io/badge/MyBatis-B7178C.svg?style=for-the-badge)

### 🔧 Tools  
![Notion](https://img.shields.io/badge/Notion-000000.svg?style=for-the-badge&logo=notion&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google_Sheets-34A853.svg?style=for-the-badge&logo=googlesheets&logoColor=white)
![ERD Cloud](https://img.shields.io/badge/ERD_Cloud-4285F4.svg?style=for-the-badge)
![IntelliJ IDEA](https://img.shields.io/badge/IntelliJ_IDEA-000000.svg?style=for-the-badge&logo=intellijidea&logoColor=white)
![VS Code](https://img.shields.io/badge/VS_Code-007ACC.svg?style=for-the-badge&logo=visualstudiocode&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032.svg?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717.svg?style=for-the-badge&logo=github&logoColor=white)
![Postman](https://img.shields.io/badge/Postman-FF6C37.svg?style=for-the-badge&logo=postman&logoColor=white)

       
Project Architecture (선택)

## 🎬 Demo
<details>
  <summary>Login</summary>

- Google Login<br>
  ![Image](https://github.com/user-attachments/assets/e7f5e196-9fc2-4a84-aaba-e3ce22eca34e)

- Naver Login<br>
  ![Image](https://github.com/user-attachments/assets/88810a05-d6ce-4365-81c3-bf9d27716fce)

- Kakao Login<br>
  ![Image](https://github.com/user-attachments/assets/ff5d2d9e-0763-4720-9d23-7a192bcc4613)

- Admin Login<br>
  ![Image](https://github.com/user-attachments/assets/fc78136b-ccff-46f2-804e-b545005132f1)

</details>

<details>
  <summary>Admin Membership Management</summary>

- Suspension of membership<br>
  ![Image](https://github.com/user-attachments/assets/a6ea0053-7797-4360-9d43-6ae854b40bc7)

- Activation of membership<br>
  ![Image](https://github.com/user-attachments/assets/d817200c-ceda-4bb8-85a6-0452cee3513d)

- Pagination<br>
  ![Image](https://github.com/user-attachments/assets/15c6df88-d63d-44e7-bf19-ea32d56ec23e)

</details>

<details>
  <summary>Home Screen</summary>

- Home<br>
  <img width="700" alt="Image" src="https://github.com/user-attachments/assets/a4690cc2-711d-46d5-827c-4e690a3f9948" />

- Recommenation Pop-Up<br>
  ![진짜추천팝업](https://github.com/user-attachments/assets/c1a5b82f-fb42-48e9-bb58-5a2f87223550)

- View the rankings in full<br>
  ![Image](https://github.com/user-attachments/assets/7bce638d-865f-42c5-9697-aa79b618ac79)

- Notice<br>
  ![Image](https://github.com/user-attachments/assets/832f345c-eba1-4564-9257-f7ad36fda381)

</details>

<details>
  <summary>My-Page</summary>

- Modifying Membership Information<br>
  ![Image](https://github.com/user-attachments/assets/f6fc7db4-8600-419c-9d8f-475d033527a9)

- Point Details Inquiry<br>
  ![Image](https://github.com/user-attachments/assets/61697c32-2141-4d4a-b0bb-00da00d0ff8c)

- Gather My Feed & Click to go to that feed<br>
  ![Image](https://github.com/user-attachments/assets/ccbdd0d2-cfb9-46c6-81a6-a6ddc70a24bc)

</details>

<details>
  <summary>Feed</summary>

- Writing Feed<br>
  ![write-successimg](https://github.com/user-attachments/assets/b23f69fd-3147-4d63-9bbc-be80e45423a9)
 
- View Feed<br>
 ![list-successimg](https://github.com/user-attachments/assets/80494e33-ce71-44c3-8d24-5b1aac7b093a)

- Modify Feed<br>
  ![edit-successimg](https://github.com/user-attachments/assets/65a05779-9255-428d-90a3-f1442fc595a3)

- Delete Feed<br>
  ![delete-successimg](https://github.com/user-attachments/assets/0f7ecc09-c784-4d09-8908-a7600dbef29b)

- Giving Like to Feed<br>
  ![feedlike-successimg](https://github.com/user-attachments/assets/0dbed72a-490d-47be-9772-8fff00eb7728)

</details>

<details>
  <summary>Store</summary>

- Item Registration<br>
![ezgif-1f2d9e2ff2f7290f](https://github.com/user-attachments/assets/fc9db298-dec8-41f0-834f-c810243d8f5a)

- Item Modification<br>
![아이템 수정](https://github.com/user-attachments/assets/f96fe94b-be6f-4d35-84f1-05230058689a)

- Item Deletion<br>
 ![아이템 삭제](https://github.com/user-attachments/assets/b5918312-0255-40e4-abc9-6e3803ede724)
 
- Item View<br>
![아이템 조회](https://github.com/user-attachments/assets/616facdb-00e8-4027-aa9e-90e686a86a7f)


</details>

<details>
  <summary>Report Processing</summary>

  - Report Processing<br>
  ![신고 처리](https://github.com/user-attachments/assets/f8072048-7432-488a-90a5-087ae14b9891)
</details>

<details>
  <summary>Notice</summary>

  - Notice<br>
  ![공지사항](https://github.com/user-attachments/assets/9d811aa8-2ded-4f9a-96c2-c9cb33a38cb1)
</details>

<details>
  <summary>User Alarm</summary>

  - User Alarm <br>
  ![알림](https://github.com/user-attachments/assets/4740e163-f1f8-4cf0-8a73-c3610b872587)
</details>


Folder Structure (선택)

How to Run (로컬 실행 방법)

API Overview (선택)

Data & Recommendation Engine (너 프로젝트 핵심✨)
