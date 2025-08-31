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


