# Access Form — Use Case Hierarchy 📄

## Table of Contents
- [1. Admin (Green)](#1-admin-green)  
- [2. Form Creator (Blue)](#2-form-creator-blue)  
- [3. Respondent / Shared & System (Orange / Purple / Gray)](#3-respondent--shared--system-orange--purple--gray)  
- [Drawing Tips](#drawing-tips)  

---

## 1. Admin (Green)

| Main Use Case | Sub-Use Cases (Included / Extended) |
|--------------|-------------------------------------|
| **Manage Users [Green]** | Add User, Edit User, Delete User |
| **Manage Forms [Green]** | View Forms, Edit Forms, Delete Forms |
| **Monitor Accessibility Compliance [Green]** | `<<include>>` Ensure Accessibility Standards |
| **View Analytics / Reports [Green]** | Filter Reports; Export (CSV / Excel / PDF) |

---

## 2. Form Creator (Blue)

| Main Use Case | Sub-Use Cases (Included / Extended) |
|--------------|-------------------------------------|
| **Create Form [Blue]** | Add Questions (MCQ, Text, Rating, File Upload); Reorder/Delete Questions; Preview Form |
| | `<<include>>` **Enable Accessibility Features [Light Blue]**  
| | • Keyboard Navigation  
| | • Screen Reader (ARIA)  
| | • High-Contrast / Dyslexia-Friendly Themes  
| | • Alt Text for Images  
| | • Captions / Sign-Language Video |
| **Share Form [Blue]** | Via Web, Email, SMS |
| **View Responses / Analytics [Blue]** | Filter Responses; Export Data (CSV / Excel / PDF) |

---

## 3. Respondent / Shared & System (Orange / Purple / Gray)

| Role / Type | Use Case | Sub-Use Cases (Included / Extended) |
|-------------|----------|-------------------------------------|
| **Respondent [Orange]** | Fill Form | `<<extend>>` Voice Input / Speech-to-Text; Keyboard Navigation |
| | Submit Form | – |
| | Use Accessibility Features [Orange] | Screen Reader; High-Contrast / Dyslexia-Friendly Themes; Captions / Sign-Language Video |
| **All Actors [Purple]** | Authenticate User | Login / Logout |
| **System Processes [Gray]** | Store Responses | – |
| | Export Data | CSV, Excel, PDF |

---

## Drawing Tips

- Use actor-colors (Green, Blue, Orange, Purple) outside the system boundary.  
- Main use cases → ellipses with same color as actor.  
- Sub-use cases → lighter shade of same color (or nested ellipses).  
- Use **`<<include>>`** for mandatory included features; **`<<extend>>`** for optional/alternative features.  
- System / shared processes (Gray) should be inside boundary but visually distinct from actor-related use cases.  
- Layout suggestion:  
  - Left side: Admin, Form Creator  
  - Right side: Respondent, Shared/System  

---

## Use case Diagram 

![Untitled_pages-to-jpg-0001](https://github.com/user-attachments/assets/61b862ec-8dfb-4d86-a36f-5f24e9387fc4)



