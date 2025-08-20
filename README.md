# DataCamp_Projects
DataCamp SQL projects showcasing data analysis and query-solving skills.

# SQL Project: Mental Health Analysis of International Students

## 📌 Objective
This project explores whether studying abroad impacts students’ mental health.  
The analysis is based on survey data collected in 2018 from students at a Japanese international university.  

The study investigates the relationship between:
- **Depression levels (PHQ-9 test scores)**
- **Social connectedness (SCS test scores)**
- **Acculturative stress (ASISS test scores)**
- **Length of stay in the host country**

Using PostgreSQL, we analyze how the **length of stay** impacts mental health scores for international students.

---

## 📊 Dataset Description
The dataset contains the following columns:

| Field Name    | Description |
|---------------|-------------|
| inter_dom     | Type of student (International or Domestic) |
| japanese_cate | Japanese language proficiency |
| english_cate  | English language proficiency |
| academic      | Current academic level (Undergraduate or Graduate) |
| age           | Age of the student |
| stay          | Length of stay in years |
| todep         | Depression score (PHQ-9 test) |
| tosc          | Social connectedness score (SCS test) |
| toas          | Acculturative stress score (ASISS test) |

---

## ❓ Project Task
- Analyze the **impact of length of stay** on international students’ average mental health diagnostic scores.  
- Return a table with:
  - `stay` → length of stay in years  
  - `count_int` → number of international students per stay length  
  - `average_phq` → average PHQ-9 score (rounded to 2 decimals)  
  - `average_scs` → average SCS score (rounded to 2 decimals)  
  - `average_as` → average ASISS score (rounded to 2 decimals)  
- Sort results by **stay** in descending order.  
- Limit output to **9 rows**.

---

## 📝 SQL Solution
```sql
SELECT stay, 
       COUNT(inter_dom) AS count_int, 
       ROUND(AVG(todep), 2) AS average_phq, 
       ROUND(AVG(tosc), 2) AS average_scs, 
       ROUND(AVG(toas), 2) AS average_as
FROM students
WHERE inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC
LIMIT 9;

