#  Clinic Management System – ER Diagram Design

## Problem Statement
A modern clinic wants to organize its operations digitally. They want to manage doctors, patients, appointments, consultations, diagnostic tests, reports, and payments. Patients should be able to visit doctors, book appointments, undergo tests if prescribed, and receive reports later.

The clinic may have multiple doctors across different departments or specialties. A patient may visit the clinic multiple times. During a visit, the doctor may prescribe one or more diagnostic tests. The diagnostic reports may be generated later and linked back to the patient and doctor visit.

Your task is to design the ER diagram for this clinic system.

This assignment is not about making a hospital-level giant system. Keep it focused on a clinic that handles appointments, consultations, diagnostics, and reporting in a clean and scalable way.

---

##  Objectives

The design supports the following real-world scenarios:

- Manage doctors and their specialties  
- Allow patients to book appointments  
- Track appointment status (scheduled, completed, cancelled, etc.)  
- Record actual consultations (visits)  
- Prescribe diagnostic tests during consultations  
- Generate and store diagnostic reports  
- Handle payments for consultations  

---

## Key Design Decisions

### 1. Appointment vs Consultation
- Appointment represents a booking  
- Consultation represents the actual doctor visit  

Not all appointments result in consultations (e.g., cancellations, no-shows)

---

### 2. User Abstraction
A separate `User` entity is introduced for authentication:

- One user → one patient or doctor profile  
- Supports role-based access (patient, doctor, admin in future)

---

### 3. Diagnostic Flow
- Tests are prescribed during consultations  
- Reports are generated after tests  
- Multiple tests can be linked to one consultation  

---

### 4. Doctor Specialties
- A doctor can have multiple specialties  
- Implemented using a junction table (`DOCTOR_SPECIALTY`)  

---

## Entities Description

###  User
Stores authentication-related information:
- Email, password, role, account status  

---

### Patient
Stores patient-specific details:
- Name, date of birth, gender, contact info, blood group  

---

### Doctor
Stores doctor information:
- Qualification, experience, consultation fees  

---

###  Specialty
Defines medical specialties (e.g., Cardiology, Dermatology)

---

### Doctor_Specialty
Maps doctors to one or more specialties  

---

###  Appointment
Represents booking between patient and doctor:
- Includes date, status, and reason  

---

###  Consultation
Represents actual visit:
- Linked to appointment (0 or 1 consultation per appointment)  
- Contains diagnosis and notes  

---

###  Test_Master
Stores available diagnostic tests:
- Name, description, price  

---

###  Prescribed_Test
Tracks tests prescribed during consultation:
- Status of test (prescribed, completed, etc.)  

---

### Report
Stores diagnostic results generated after tests  

---

###  Payment
Tracks payments made for consultations  

---

##  Relationships Summary

- One User → One Patient/Doctor  
- One Patient → Many Appointments  
- One Doctor → Many Appointments  
- One Appointment → Zero or One Consultation  
- One Consultation → Many Prescribed Tests  
- One Test → Many Prescriptions  
- One Prescribed Test → One Report  
- One Consultation → one Payments 
---
## ER Diagram :
![ER Diagram](/image.png)
##  ER Diagram Features

- Normalized structure (avoids redundancy)  
- Clear separation of booking and actual visits  
- Supports real-world clinic workflows  
- Scalable for future enhancements  