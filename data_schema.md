# Dataset Schema - Student Placement Analytics

## Overview
This schema defines a synthetic dataset of **500 student records** for placement analytics and predictive modeling. The dataset captures academic performance, skills, experience, demographics, and placement outcomes.

---

## Column Specifications

### 1. Student Identification

| Column Name | Data Type | Value Range | Business Meaning |
|------------|-----------|-------------|------------------|
| `Student_ID` | String | STU001 - STU500 | Unique identifier for each student (format: STU + 3-digit number) |

---

### 2. Demographic Features

| Column Name | Data Type | Value Range | Business Meaning |
|------------|-----------|-------------|------------------|
| `Gender` | Categorical | Male, Female | Gender of the student |
| `Age` | Integer | 20 - 25 | Student age at the time of placement season |
| `Location` | Categorical | Tier1, Tier2, Tier3 | Home location tier (Tier1: Metropolitan, Tier2: Cities, Tier3: Towns/Rural) |

---

### 3. Academic Background

| Column Name | Data Type | Value Range | Business Meaning |
|------------|-----------|-------------|------------------|
| `SSC_Percentage` | Float | 55.0 - 98.0 | Secondary School Certificate (10th grade) percentage |
| `HSC_Percentage` | Float | 50.0 - 97.0 | Higher Secondary Certificate (12th grade) percentage |
| `HSC_Stream` | Categorical | Science, Commerce, Arts | Stream chosen in higher secondary education |
| `Degree_Type` | Categorical | B.Tech, B.E., BCA, B.Sc | Type of undergraduate degree program |
| `Specialization` | Categorical | Computer Science, IT, Electronics, Mechanical, Civil, Data Science | Academic specialization/branch |
| `CGPA` | Float | 5.5 - 10.0 | **Mandatory**: Cumulative Grade Point Average (on 10-point scale) |
| `Backlogs` | Integer | 0 - 5 | **Mandatory**: Number of backlogs/arrears during the degree program |

---

### 4. Attendance & Discipline

| Column Name | Data Type | Value Range | Business Meaning |
|------------|-----------|-------------|------------------|
| `Attendance_Percentage` | Float | 60.0 - 100.0 | **Mandatory**: Overall attendance percentage throughout the degree |

---

### 5. Skills & Competencies

| Column Name | Data Type | Value Range | Business Meaning |
|------------|-----------|-------------|------------------|
| `Technical_Skill_Score` | Integer | 30 - 100 | **Mandatory**: Technical proficiency score (based on assessments, certifications, coding tests) |
| `Communication_Skill_Score` | Integer | 40 - 100 | **Mandatory**: Communication skills rating (based on interviews, presentations, language tests) |
| `Problem_Solving_Score` | Integer | 35 - 100 | Aptitude and problem-solving ability score (based on logical reasoning tests) |
| `Leadership_Score` | Integer | 0 - 100 | Leadership and teamwork capability score (based on extracurricular activities) |

---

### 6. Experience & Practical Exposure

| Column Name | Data Type | Value Range | Business Meaning |
|------------|-----------|-------------|------------------|
| `Internship_Count` | Integer | 0 - 4 | **Mandatory**: Number of internships completed during the degree program |
| `Internship_Duration_Months` | Integer | 0 - 12 | Total duration of all internships combined (in months) |
| `Project_Count` | Integer | 0 - 8 | **Mandatory**: Number of academic and personal projects completed |
| `Research_Papers` | Integer | 0 - 3 | Number of research papers published or presented |
| `Certifications` | Integer | 0 - 6 | Number of professional certifications earned (e.g., AWS, Google, Coursera) |

---

### 7. Extracurricular & Soft Skills

| Column Name | Data Type | Value Range | Business Meaning |
|------------|-----------|-------------|------------------|
| `Extracurricular_Activities` | Categorical | None, Low, Medium, High | Level of participation in sports, clubs, events (None=0, Low=1-2, Medium=3-4, High=5+) |
| `Hackathon_Participation` | Integer | 0 - 5 | Number of hackathons participated in or won |
| `Competitive_Programming_Rating` | Integer | 0 - 2500 | Rating on competitive programming platforms (0 = not active, 2500 = expert level) |

---

### 8. Training & Preparation

| Column Name | Data Type | Value Range | Business Meaning |
|------------|-----------|-------------|------------------|
| `Aptitude_Test_Score` | Float | 40.0 - 100.0 | Score in placement aptitude tests (percentile) |
| `Mock_Interview_Score` | Float | 30.0 - 100.0 | Average performance score in mock interviews |
| `Resume_Quality_Score` | Integer | 40 - 100 | Resume quality rating (assessed by career services) |

---

### 9. Placement Outcomes (Target Variables)

| Column Name | Data Type | Value Range | Business Meaning |
|------------|-----------|-------------|------------------|
| `Placement_Status` | Binary | 0, 1 | **Mandatory**: Whether student got placed (0 = Not Placed, 1 = Placed) |
| `Salary` | Float | 0 (if not placed), 3.0 - 25.0 (if placed) | **Mandatory**: Annual salary package in Lakhs INR (Indian Rupees). 0 for unplaced students |
| `Job_Role` | Categorical | Software Developer, Data Analyst, Business Analyst, Consultant, Support Engineer, System Engineer, NULL | Job role offered (NULL for unplaced students) |
| `Company_Type` | Categorical | Product, Service, Startup, Core, NULL | Type of company that hired the student (NULL for unplaced) |
| `Company_Tier` | Categorical | Tier1, Tier2, Tier3, NULL | Company tier based on reputation and package (Tier1: Top MNCs, Tier2: Mid-level, Tier3: Entry-level, NULL: Not placed) |

---

## Data Generation Guidelines

### Realistic Correlations to Implement:
1. **CGPA** should positively correlate with `Placement_Status` and `Salary`
2. **Backlogs** should negatively correlate with placement success
3. Higher `Technical_Skill_Score` should increase placement probability and salary
4. `Internship_Count` and `Project_Count` should boost placement chances
5. Students with `Specialization` in Computer Science/IT/Data Science typically command higher salaries
6. `Attendance_Percentage` below 75% should significantly reduce placement probability
7. `Communication_Skill_Score` should be critical for higher-paying roles
8. Combination of high CGPA (>8.0), multiple internships (2+), and strong technical skills (>80) should almost guarantee placement

### Realistic Salary Ranges by Company Tier:
- **Tier 1 Companies**: 12.0 - 25.0 LPA (Premium product companies, FAANG-tier)
- **Tier 2 Companies**: 6.0 - 12.0 LPA (Established MNCs and well-funded startups)
- **Tier 3 Companies**: 3.0 - 6.0 LPA (Service companies, mass recruiters)

### Placement Status Distribution:
- Approximately **70-75%** of students should be placed (realistic for decent engineering colleges)
- Remaining **25-30%** should be unplaced (with lower CGPA, high backlogs, or weak skills)

---

## Sample Data Record

```
Student_ID: STU042
Gender: Female
Age: 22
Location: Tier1
SSC_Percentage: 88.5
HSC_Percentage: 85.2
HSC_Stream: Science
Degree_Type: B.Tech
Specialization: Computer Science
CGPA: 8.7
Backlogs: 0
Attendance_Percentage: 92.5
Technical_Skill_Score: 85
Communication_Skill_Score: 78
Problem_Solving_Score: 82
Leadership_Score: 70
Internship_Count: 2
Internship_Duration_Months: 6
Project_Count: 5
Research_Papers: 1
Certifications: 3
Extracurricular_Activities: Medium
Hackathon_Participation: 2
Competitive_Programming_Rating: 1450
Aptitude_Test_Score: 87.5
Mock_Interview_Score: 82.0
Resume_Quality_Score: 85
Placement_Status: 1
Salary: 10.5
Job_Role: Software Developer
Company_Type: Product
Company_Tier: Tier2
```

---

## Dataset Statistics Summary

| Metric | Value |
|--------|-------|
| Total Records | 500 |
| Total Features | 30 |
| Categorical Features | 9 |
| Numerical Features | 21 |
| Target Variable (Classification) | Placement_Status |
| Target Variable (Regression) | Salary |
| Expected Placement Rate | 70-75% |
| Expected Missing Values | 0% (clean synthetic data) |

---

## Next Steps

1. **Generate Dataset**: Use Python (Faker, NumPy, Pandas) to create synthetic data following this schema
2. **Apply Correlations**: Ensure realistic relationships between features and outcomes
3. **Validate Quality**: Check for data consistency, distributions, and outliers
4. **Save Format**: Export as CSV file in `data/raw/student_placement_data.csv`
5. **Document**: Create data dictionary and generation script for reproducibility

---

**✅ Dataset schema designed successfully.**
