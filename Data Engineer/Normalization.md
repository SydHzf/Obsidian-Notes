___
Database normalization is a systematic approach of organizing data in a database to reduce [[redundancy]] and improve [[data integrity]]. The process involves dividing a database into two or more tables and defining relationships between the tables. The goal is to ensure that the database structure is efficient and that the data is stored logically.

### Key Concepts of Normalization

1. **Redundancy**: Duplication of data. Normalization aims to eliminate redundant data to save storage and ensure consistency.
2. **Data Integrity**: Ensuring accuracy and consistency of data. Normalized databases help maintain data integrity by enforcing rules that prevent anomalies.

**Normalization** is the process of organizing data in a database to minimize redundancy and dependency by dividing large tables into smaller, related tables. It ensures data integrity and improves database efficiency. Here’s a detailed explanation of the forms of normalization with examples:

---

### **1. First Normal Form (1NF): Eliminate Repeating Groups**

- **Objective:** Ensure that each column contains atomic (indivisible) values, and each row is unique.
- **Rules:**
    1. Each column should have a single value (no arrays or sets).
    2. Each row should have a unique identifier (primary key).

#### Example (Unnormalized Table):

|StudentID|Name|Courses|
|---|---|---|
|1|Alice|Math, Science|
|2|Bob|History|

#### Converted to 1NF:

|StudentID|Name|Course|
|---|---|---|
|1|Alice|Math|
|1|Alice|Science|
|2|Bob|History|

---

### **2. Second Normal Form (2NF): Eliminate Partial Dependency**

- **Objective:** Remove partial dependencies (when a non-key (non-unique) attribute is dependent only on part of a composite primary key).
- **Rules:**
    1. Must be in 1NF.
    2. All non-key attributes must depend on the entire primary key.

#### Example (1NF Table):

| StudentID | Course  | Instructor |
| --------- | ------- | ---------- |
| 1         | Math    | Dr. Smith  |
| 1         | Science | Dr. Brown  |
| 2         | History | Dr. White  |

**Issue:** `Instructor` depends only on `Course`, not the full key (`StudentID, Course`).

#### Converted to 2NF:


| StudentID | Course  |     |
| --------- | ------- | --- |
| 1         | Math    |     |
| 1         | Science |     |
| 2         | History |     |
    
| Course | Instructor |     |
| ------ | ---------- | --- |
| Math   | Dr. Smith  |     |
| Science | Dr. Brown |  
| History | Dr. White |
    

---

### **3. Third Normal Form (3NF): Eliminate Transitive Dependency**

- **Objective:** Remove transitive dependencies (when a non-key(non-unique) attribute depends on another non-key attribute which depend on a key attribute a -> b -> c).
- **Rules:**
    1. Must be in 2NF.
    2. No non-key attribute should depend on another non-key attribute.

#### Example (2NF Table):

|StudentID|Course|Instructor|Dept|
|---|---|---|---|
|1|Math|Dr. Smith|Math|
|1|Science|Dr. Brown|Science|
|2|History|Dr. White|History|

**Issue:** `Dept` depends on `Instructor`, not directly on the primary key (`StudentID, Course`).

#### Converted to 3NF:


| StudentID | Course  |     |
| --------- | ------- | --- |
| 1         | Math    |     |
| 1         | Science |     |
| 2         | History |     |


| Course  | Instructor | Dept    |     |
| ------- | ---------- | ------- | --- |
| Math    | Dr. Smith  | Math    |     |
| Science | Dr. Brown  | Science |     |
| History | Dr. White  | History |     |


---

### **4. Boyce-Codd Normal Form (BCNF): Handle Anomalies Beyond 3NF**

- **Objective:** Ensure every determinant is a candidate key (resolve any remaining dependencies).
- **Rules:**
    1. Must be in 3NF.
    2. If a non-trivial functional dependency exists (`X → Y`), then `X` must be a superkey.

#### Example (3NF Table):

|StudentID|Course|Instructor|
|---|---|---|
|1|Math|Dr. Smith|
|2|Science|Dr. Smith|

**Issue:** `Instructor → Course` exists, but `Instructor` is not a candidate key.

#### Converted to BCNF:

| StudentID | Course  |     |
| --------- | ------- | --- |
| 1         | Math    |     |
| 2         | Science |     |

| Instructor | Course |  
|------------|----------|  
| Dr. Smith | Math |  
| Dr. Smith | Science |


---

### **5. Fourth Normal Form (4NF): Handle Multi-Valued Dependencies**

- **Objective:** Eliminate multi-valued dependencies (when one attribute depends on another, and both are independent of the primary key).
- **Rules:**
    1. Must be in BCNF.
    2. A table should not have more than one independent multi-valued dependency.

#### Example (BCNF Table):

|StudentID|Hobby|Language|
|---|---|---|
|1|Reading|English|
|1|Swimming|French|
|2|Painting|Spanish|

**Issue:** `Hobby` and `Language` are independent multi-valued attributes.

#### Converted to 4NF:

- **Student-Hobby Table:** | StudentID | Hobby |  
    |-----------|--------------|  
    | 1 | Reading |  
    | 1 | Swimming |  
    | 2 | Painting |
    
- **Student-Language Table:** | StudentID | Language |  
    |-----------|--------------|  
    | 1 | English |  
    | 1 | French |  
    | 2 | Spanish |
    

---

### **6. Fifth Normal Form (5NF): Handle Join Dependencies**

- **Objective:** Ensure that data cannot be decomposed further without loss of information.
- **Rules:** Must be in 4NF and resolve all join dependencies.

---

### Summary Table:

|Normal Form|Key Objective|
|---|---|
|1NF|Eliminate repeating groups (atomic values).|
|2NF|Remove partial dependencies.|
|3NF|Remove transitive dependencies.|
|BCNF|Ensure all determinants are candidate keys.|
|4NF|Remove multi-valued dependencies.|
|5NF|Eliminate join dependencies.|

Would you like more examples or clarification on a specific normal form?