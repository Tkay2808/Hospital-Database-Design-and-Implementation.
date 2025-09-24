# Hospital-Database-Design-and-Implementation.
 

## Project Overview  
This repository contains the **Database Design and Implementation Project** for **Toronto General Infirmary Patient and Medical Management System**, completed and designed by **X**quisite Analytics** in **September 2025**.  

The system is designed to efficiently manage hospital operations, including patient information, doctor details, medical records, appointments, and departmental data. Its primary goal is to ensure **data integrity, scalability, and quick access to essential medical information** for both staffs and administrators.  

---

## Table of Contents  
- [Introduction](#introduction)  
- [Database Design Process](#database-design-process)  
  - [Requirements Gathering](#requirements-gathering)  
  - [Conceptual Design](#conceptual-design) 
  - [ER Diagram](#ER-Diagram)
  - [Logical Design](#logical-design)  
  - [Physical Design](#physical-design)  
- [Database Schema and Implementation](#database-schema-and-implementation)  
  - [Patients Table](#patients-table)  
  - [Departments Table](#departments-table)  
  - [Doctors Table](#doctors-table)  
  - [Appointments Table](#appointments-table)  
  - [Medical Records Table](#medical-records-table)  
- [Normalization](#normalization)  
- [Triggers and Business Logic](#triggers-and-business-logic)  
- [Justification of Design Choices](#justification-of-design-choices)  
- [Conclusion](#conclusion)  

---

## Introduction  
The **Toronto General Infirmary** required a scalable and efficient solution to manage its healthcare operations, including **patient registration, appointment scheduling, and medical records management**.  

This database system was developed to:  
- Enhance **operational efficiency**  
- Ensure **data integrity and accuracy**  
- Provide **fast, reliable access** to patient and medical data  
- Support **scalable growth** of the hospital  

---

## Database Design Process  

### Requirements Gathering  
Through collaboration with stakeholders, the following requirements were identified:  
- Maintain comprehensive records of **patients, doctors, and departments**  
- Manage **medical records** (diagnoses, prescriptions, treatment history)  
- Support **real-time appointment scheduling and tracking**  

### Conceptual Design  
The **Entity-Relationship (ER) model** identified the following entities:  
- **Patients**: Personal and contact details  
- **Doctors**: Names, specialties, availability  
- **Departments**: Medical divisions and organizational structure  
- **Appointments**: Scheduling and status  
- **Medical Records**: Historical data of diagnoses and treatments  
--- 

### ER Diagram 


---

### Logical Design  
The ER model was mapped into **relational tables**, with **primary keys** and **foreign keys** enforcing relationships and referential integrity.  

### Physical Design  
The database was implemented in **SQL Server (T-SQL)** with:  
- **Triggers** for appointment status handling  
- **Constraints** for data accuracy  
- **Indexes and optimized queries** for performance  

---

## Database Schema and Implementation  

### Patients Table  
```sql
-- CREATE PATIENTS TABLE: THIS INCLUDES PATIENTS BASIC INFORMATION
CREATE TABLE PATIENTS(    
    PATIENTS_ID INT PRIMARY KEY IDENTITY,    
    FULL_NAME VARCHAR(50) NOT NULL,    
    DATE_OF_BIRTH DATE NOT NULL,    
    INSURANCE VARCHAR(100) NOT NULL,    
    PATIENTS_ADDRESS VARCHAR(200),    
    PHONE_NO VARCHAR(20),    
    EMAIL VARCHAR(200),    
    PATIENTS_USERNAME VARCHAR(30) NOT NULL,    
    PATIENTS_PASSWORD CHAR(20) NOT NULL,    
    REG_DATE DATE NOT NULL,    
    ADMITTED_DATE DATE NOT NULL,    
    DISCHARGED_DATE DATE NOT NULL    
);    

SELECT * FROM PATIENTS;
---
### Departments Table

-- CREATE DEPARTMENT TABLE
CREATE TABLE DEPARTMENT(    
    DEPARTMENT_ID INT PRIMARY KEY IDENTITY,    
    DEPARTMENT_NAME VARCHAR(30)    
);    

SELECT * FROM DEPARTMENT;
---

### Doctors Table

-- CREATE DOCTORS TABLE: INVOLVES DOCTORS INFORMATION AND THE DEPARTMENTS THEY BELONG

CREATE TABLE DOCTORS (    
    DOCTORS_ID INT PRIMARY KEY IDENTITY,    
    FULL_NAME VARCHAR(50) NOT NULL,    
    PHONE_NO VARCHAR(20),    
    DEPARTMENT_ID INT REFERENCES DEPARTMENT(DEPARTMENT_ID)    
);    

SELECT * FROM DOCTORS;
---
### Appointments Table 

-- CREATE APPOINTMENTS TABLE
CREATE TABLE APPOINTMENTS (    
    APPOINTMENTS_ID INT PRIMARY KEY IDENTITY,     
    APPOINTMENT_DATE DATETIME,    
    STATUS VARCHAR(30),    
    PATIENTS_ID INT REFERENCES PATIENTS(PATIENTS_ID),    
    DOCTORS_ID INT REFERENCES DOCTORS(DOCTORS_ID)    
);    

SELECT * FROM APPOINTMENTS;
---

###  Medical Records Table

-- CREATE MEDICAL RECORDS TABLE: THIS STORES THE PATIENTS MEDICAL HISTORY AND CONNECTS TO THE DOCTOR
CREATE TABLE MEDICAL_RECORDS (    
    MEDICAL_RECORD_ID INT PRIMARY KEY IDENTITY,     
    DIAGNOSIS VARCHAR(100),    
    TREATMENT_DATE DATE,     
    PRESCRIPTIONS VARCHAR(100),    
    RECORD_DATE DATETIME,     
    PATIENTS_ID INT REFERENCES PATIENTS(PATIENTS_ID),    
    DOCTORS_ID INT REFERENCES DOCTORS(DOCTORS_ID)    
);    

SELECT * FROM MEDICAL_RECORDS (...);
---



## Normalization  

- **First Normal Form (1NF):**  
  Ensures atomicity of values (no repeating groups or multi-valued attributes).  

- **Second Normal Form (2NF):**  
  Eliminates **partial dependencies**; all non-key attributes fully depend on the primary key.  

- **Third Normal Form (3NF):**  
  Removes **transitive dependencies**, ensuring non-key attributes depend only on primary keys.  

---

## Triggers and Business Logic  
A trigger was implemented to enforce appointment management rules:  

- If an appointment is marked as **Canceled** without rebooking, the **transaction is rolled back**.  
- Ensures appointments maintain **data integrity and business rules**.  

---

## Justification of Design Choices  
- **Separation of Concerns:** Each table manages one type of data, reducing redundancy.  
- **Data Integrity:** Foreign keys and constraints prevent inconsistent or orphaned records.  
- **Scalability:** Supports future hospital growth with minimal structural changes.  
- **Business Rule Enforcement:** Triggers ensure smooth, rule-compliant operations.  

---

## Conclusion  

The **Toronto General Infirmary Database System** is a **robust, scalable, and reliable solution** for managing healthcare operations. It provides:  
- Efficient **patient and doctor data management**  
- Accurate **medical records and appointment tracking**  
- Strong **data integrity and business rule enforcement**  

This system enhances healthcare service delivery by enabling **fast, structured, and secure access** to critical information.

--- 

## About me
- I transform complex data into clear, actionable insights.
Using analytics, machine learning, and visualization, I help you understand trends, improve efficiency, and plan for the future.

Connect with me @https://www.linkedin.com/in/adetokunbo-olasupo-70aa042a1


--