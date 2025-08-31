# University Rankings Data Analysis Report

This project analyzes global university rankings to explore data design, visual analytics, and structured queries. We built a relational database using SQL and created interactive visualizations in Tableau to turn complex data into actionable knowledge for students, families, and employers.

## Database Schema
The database was designed with three core tables: `Location`, `University`, and `RankingScores` to structure the data logically.

```sql
-- Stores geographical location for each university
CREATE TABLE Location (
    LocationID INT AUTO_INCREMENT PRIMARY KEY, -- Unique identifier for each location
    Country VARCHAR(100), -- Name of the country
    Region VARCHAR(100) -- Broad regions (e.g., Asia, Europe, Oceania)
);

-- Contains general information about universities
CREATE TABLE University (
    UniversityID INT AUTO_INCREMENT PRIMARY KEY, -- Unique identifier for each university
    UniversityName VARCHAR(255), -- Name of the institution
    LocationID INT, -- Foreign key referencing the university's location
    PublicOrPrivate VARCHAR(50), -- Indicates if the institution is public or private
    FOREIGN KEY (LocationID) REFERENCES Location(LocationID)
);

-- Stores annual ranking and performance scores for each university
CREATE TABLE RankingScores (
    ScoreID INT AUTO_INCREMENT PRIMARY KEY, -- Unique identifier for each score
    UniversityID INT, -- Foreign key referencing the university
    Ranking INT, -- Global 2026 ranking of the university
    OverallScore FLOAT, -- Overall score based on various metrics
    -- ...and so on for the other columns
    FOREIGN KEY (UniversityID) REFERENCES University(UniversityID)
);
```
## Data Dictionary
The database is comprised of three tables: Location, University, and RankingScore.

### Location Table
| Column Name | Description | Data Type | Key? |
|---|---|---|---|
| LocationID | Unique number identifying each location | INT | PK |
| Country | The country that the university is located in | VARCHAR(100) | |
| Region | The region that the university is located in | VARCHAR(100) | |

### University Table
| Column Name | Description | Data Type | Key? |
|---|---|---|---|
| UniversityID | Unique number assigned to each university | INT | PK |
| UniversityName | University’s name | VARCHAR(255) | |
| LocationID | Unique number identifying each location | INT | FK |
| PublicOrPrivate | The status of the university (public, private) | VARCHAR(50) | |
| Size | The size of the university based on student population | VARCHAR(50) | |

### RankingScore Table
| Column Name | Description | Data Type | Key? |
|---|---|---|---|
| ScoreID | Unique number for each score set | INT | PK |
| UniversityID | Unique number assigned to each university | INT | FK (references University) |
| Ranking | The predicted ranking of each university in 2026 | INT | |
| OverallScore | Composite Score used to determine the university’s rank| FLOAT | |
| AcademicReputationScore| Academic reputation score | FLOAT | |
| EmployerReputationScore| Employer reputation | FLOAT | |
| FacultyStudentScore | Evaluates Teaching Commitment for Students Per Professor| FLOAT | |
| InternationalStudentsScore| Percentage of international students | FLOAT | |
| CitationsPerFacultyScore| Citations per Faculty score | FLOAT | |

## Data Visualizations

### Top 100 Universities by Country

<img width="624" height="317" alt="Screenshot 2025-08-31 at 2 22 50 PM" src="https://github.com/user-attachments/assets/b7220d8a-3fd0-4cf6-b714-fc2d14cd96fa" />

This visualization identifies which countries contained the most top-100 ranked universities. The United States of America contains the most highly ranked universities with 25, followed by the United Kingdom with 15. This data can help students interested in studying abroad narrow down which nations align with their goals.

### Most Improved U.S Universities

<img width="626" height="211" alt="Screenshot 2025-08-31 at 2 23 05 PM" src="https://github.com/user-attachments/assets/91717d66-4a87-4377-bda6-8f6b60ccc830" />

This chart shows the top 10 U.S. universities with the greatest increase in rank from 2025-2026. The rank change was calculated by finding the difference between the 2025 and 2026 ranks; a negative number indicates the university improved its position (moved closer to rank 1). This data is useful for parents and students as it shows which universities are continuously improving.

### Universities with Highest Employment Outcomes

<img width="626" height="423" alt="Screenshot 2025-08-31 at 2 23 16 PM" src="https://github.com/user-attachments/assets/6a6af026-5bff-4a47-a1b0-630761602eec" />

This world map shows the number of top-50 universities with the highest Employment Outcomes score per country. This metric reflects how well graduates perform in the job market, highlighting institutions that best prepare students for successful careers. The United States leads with 15 universities, followed by the United Kingdom and Canada with 3 each.

### Academic vs. Employer Reputation

<img width="623" height="625" alt="Screenshot 2025-08-31 at 2 23 26 PM" src="https://github.com/user-attachments/assets/71a94991-5843-4489-b8a3-969e1817f250" />

This scatterplot represents the relationship between each university’s Academic Reputation Score and Employer Reputation Score. It reveals a strong positive correlation, indicating that institutions known for academic excellence are also well-respected by employers.  This can help students make more informed decisions and help employers target universities for recruitment.

### Sustainability vs. International Research Collaboration

<img width="646" height="399" alt="Screenshot 2025-08-31 at 2 23 37 PM" src="https://github.com/user-attachments/assets/ab0f20b9-7cca-4e84-a208-e842ab97266c" />

This visualization shows the relationship between a university's sustainability score and its international research collaboration score, broken down by global region.

***

## Conclusion

This project showed our team with valuable insight on how global university rankings can be explored through data design, visual analytics, and structured queries. By building a SQL database with defined relationships like Location, University, and RankingScores tables, we gained practical experience in data modeling, foreign key constraints, and schema development. These skills helped us create a data structure for a real-world dataset. In Tableau, we converted complex data into visualizations that highlight regional strengths, academic performance, and employment readiness across thousands of universities. Each visualization showed us patterns and helped us think critically about how students, employers, or families can use data for informed decision-making. We learned how data tools like Tableau can turn university rankings into applicable knowledge, whether it was identifying top-performing countries or highlighting quickly improving institutions. Overall, this project deepened our understanding of how SQL and Tableau work well together in analyzing real-world scenarios and emphasized the importance of data in education, policy, and career planning.
