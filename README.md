## 📌 SQL Project 1: Mental Health Analysis of International Students  

### **Objective**
This project explores whether studying abroad impacts students’ mental health.  
The analysis is based on survey data collected in 2018 from students at a Japanese international university.  

The study investigates the relationship between:  
- **Depression levels (PHQ-9 test scores)**  
- **Social connectedness (SCS test scores)**  
- **Acculturative stress (ASISS test scores)**  
- **Length of stay in the host country**  

---

### **Dataset Description**
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

⚠️ *Dataset provided by DataCamp. Not included in this repository due to license restrictions.*  

---

### **Task 1**: Impact of Stay Duration on Mental Health
Analyze the impact of length of stay on international students’ average mental health diagnostic scores.

Requirements:
- Return a table with columns: stay, count_int, average_phq, average_scs, average_as
- Round averages to 2 decimals
- Sort by stay (descending)
- Limit results to 9 rows

**Solution**:

SELECT stay, COUNT(inter_dom) AS count_int, ROUND(AVG(todep), 2) AS average_phq, 
       
ROUND(AVG(tosc), 2) AS average_scs, ROUND(AVG(toas), 2) AS average_as

FROM students

WHERE inter_dom = 'Inter'

GROUP BY stay

ORDER BY stay DESC

LIMIT 9;

---

### **Task 2**: Depression Levels by Academic Level
Explore whether undergraduate vs graduate students show differences in depression levels.

Requirements:
- Return a table with columns: academic, avg_depression
- avg_depression = average PHQ-9 depression score, rounded to 2 decimals
- Sort results by average depression in descending order

**Solution**:

SELECT academic, ROUND(AVG(todep), 2) AS avg_depression

FROM students

GROUP BY academic

ORDER BY avg_depression DESC;

---

### **Task 3**: Relationship Between Language Proficiency and Social Connectedness
Analyze if English language proficiency impacts social connectedness among students.

Requirements:
- Return a table with columns: english_cate, avg_social_connectedness
- avg_social_connectedness = average of SCS test scores, rounded to 2 decimals
- Sort by highest social connectedness

**Solution**:

SELECT english_cate, ROUND(AVG(tosc), 2) AS avg_social_connectedness

FROM students

GROUP BY english_cate

ORDER BY avg_social_connectedness DESC;
