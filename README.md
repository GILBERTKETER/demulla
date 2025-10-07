![Demulla Logo](https://demulla.co.ke/wp-content/uploads/2024/11/cropped-Demulla-web-graphics.-hcc254-01-1.png)



# Demulla Employee Check-in & Attendance Management System

## Executive Summary

As **Demulla** continues expanding its loan system and integrating multiple internal tools into one centralized platform, it is crucial to maintain a balance between scalability, reliability, and independence.

While having one unified system may sound efficient, over-integration introduces serious operational risks. If one core module such as the loan system fails, dependent systems like attendance, ticketing, or HR functionalities can also fail. This single point of failure could disrupt the entire organization’s workflow.

This proposal introduces a **modular Employee Check-in and Attendance Management System for Demulla**. It integrates seamlessly with the existing loan system for authentication but remains technically independent. This ensures that employee attendance, HR reports, and internal communications continue functioning even if the loan system experiences downtime.


## Problem Statement

The HR Manager raised concerns about the difficulty of tracking employee attendance across multiple branches.  
Currently, LOCOs and branch managers take photos as proof of presence and send them to HR — a method that is time-consuming, inconsistent, and vulnerable to manipulation.

This manual process makes it hard to:
- Verify attendance consistently.
- Detect late arrivals or early departures.
- Maintain accurate, auditable records for HR and payroll.


## Proposed Solution

The solution is a **dedicated, modular attendance system** designed for Demulla that:
- Uses secure, branch-based QR codes for check-in and check-out.
- Tracks employee **location** during check-in for verification.
- Provides real-time dashboards for branch managers and HR.
- Automates notifications via WhatsApp and email.
- Functions independently from the loan system during downtime.

This ensures reliability, transparency, and scalability without introducing dependency risks.


## Key System Advantages

1. **Independence and Reliability**  
   - Operates even when the loan platform is offline.  
   - Includes a backup sign-in mode with cached credentials or offline QR verification.

2. **Secure Integration**  
   - Uses Demulla’s existing loan system authentication.  
   - Supports role-based permissions (Employee, Manager, HR/Admin).  
   - Optional two-factor authentication (2FA) for sensitive roles.

3. **Modular Architecture**  
   - Core features (attendance, announcements, etc.) function independently.  
   - Easy to expand without disrupting other systems.


## Roles and Permissions

### Employees
- Log in using Demulla’s loan system auth system.  
- Scan a QR code to check in/out.  
- Automatically capture GPS location during check-in.  
- Provide a reason if checked in from outside the office location.  
- View attendance history and receive punctuality badges.  
- Get WhatsApp or email alerts if late or absent.

### Branch Managers
- Display daily branch QR codes.  
- Approve or reject check-ins made from outside the office radius.  
- View real-time attendance dashboards.  
- Manually check in employees (with justification).  
- Receive alerts for missing or late staff.

### HR/Admin
- Access company-wide dashboards and analytics.  
- Manage branches, employees, and work schedules.  
- Define shifts, working hours, and holidays - still reviewing this section.  
- Export data for payroll processing.  
- Review justifications for off-site check-ins.  
- Send internal announcements and review audit logs.


## Core Features

1. **QR Code Check-in System**  
   - Daily, auto-generated branch-specific QR codes.  
   - Prevents duplicate or spoofed check-ins.  

2. **Location Tracking & Validation**  
   - Captures GPS coordinates on each check-in.  
   - Validates location against registered office coordinates.  
   - Flags check-ins from outside the allowed radius.  
   - Employees working remotely or in the field can justify the location.  
   - HR and managers can approve or flag these records.

3. **Real-time Analytics Dashboard**  
   - Displays attendance summaries, lateness, and absences.  
   - Provides branch-level and company-wide trends.

4. **Automated Notifications**  
   - Sends alerts via WhatsApp and email for lateness, absence, or flagged check-ins.  

5. **Manual Check-in (with Justification)**  
   - For employees without smartphones or during technical issues.  
   - All entries logged for audit and transparency.

6. **Payroll Integration**  
   - Exports attendance data to CSV/Excel.  
   - Tracks overtime, absences, and fieldwork.  

7. **Gamification**  
   - Introduces leaderboards and punctuality rewards.  
   - Encourages timely attendance.

8. **Announcements System**  
   - HR can send organization-wide announcements instantly.  
   - Delivered via WhatsApp and email.


## Architecture Overview

| Component | Technology | Description |
|------------|-------------|-------------|
| Frontend | React + TypeScript + Tailwind + Arco Design | Dashboards, QR code display, maps, and analytics |
| Backend | Django (API) / Directus CMS + Node Services | Authentication, logic, QR generation, and GPS validation |
| Database | PostgreSQL / MySQL | Stores users, branches, tokens, logs, and location data |
| Notifications | WhatsApp API + Email | Automated alerts and updates |
| Deployment | Docker | Containerized and scalable |


## Risk and Mitigation

| Risk | Impact | Mitigation |
|------|---------|------------|
| Loan system downtime | Attendance unavailable | Independent modular system ensures continuity |
| Authentication failure | Temporary login issue | Cached tokens and backup authentication |
| Data corruption | Loss of attendance data | Daily encrypted backups and audit trails |
| GPS spoofing | False check-ins | Radius-based validation and manager review |


## Development Plan

| Phase | Duration | Deliverables |
|-------|-----------|--------------|
| Phase 1 | Weeks 1–3 | System setup, authentication, user roles, QR logic, and location-based check-in |
| Phase 2 | Weeks 4–6 | Dashboard development, analytics, WhatsApp/email notifications, and location verification |
| Phase 3 | Weeks 7–8 | Final testing, QA review, documentation, optimization, and Dockerized deployment |

**Estimated Total Duration:** 2 Months  
*(Development will primarily take place during nights and weekends.)*


## Current Progress

- Dashboard structure prepared and active.  
- Prototype accessible at: [https://lumovate.lmn.co.ke/inout/console](https://lumovate.lmn.co.ke/inout/console)


## Recommended Strategy for Demulla

While integration with the loan system offers convenience for authentication, it’s essential that the attendance system remains **modular** to ensure reliability.

If the loan system encounters downtime, ticketing, attendance, and HR functions should continue running seamlessly.  
This proposal emphasizes **connected but independent integration**, ensuring both systems can operate and scale efficiently.


## Optional Add-ons

These optional modules can evolve the platform into a full **Demulla Internal Operations Hub**.

1. **Ticketing and Issue Tracking**  
   - Employees raise HR or IT tickets.  
   - Managers track and close issues.

2. **Internal Chat and Messaging**  
   - Department-based chat with optional AI chatbot integration.  

3. **Training and E-Learning Portal**  
   - Centralized access to internal training materials.  

4. **Performance Insights**  
   - Combine attendance, punctuality, and fieldwork data for KPI-based performance reviews.  

5. **Task Management System**  
   - Employees can log and update their daily tasks.  
   - Managers can assign, monitor, and review employee tasks in real-time.  
   - Tasks can be categorized by **priority**, **urgency**, or **type**.  
   - Automated **notifications** remind employees before task deadlines.  
   - Enables daily productivity tracking and historical task analytics for performance insights.

6. **Digital Suggestion Box**  
   - Allows employees to submit feedback, ideas, or issues **anonymously**.  
   - Eliminates the need for physical suggestion boxes.  
   - Submissions can be automatically categorized (e.g., HR, IT, Welfare).  
   - Admins can review and respond to suggestions within the system dashboard.  
   - Encourages open communication while maintaining employee privacy.

7. **Other Features as Requested**

All add-ons can be implemented as separate microservices for better scalability.


## Expected Outcomes

- Eliminates manual, photo-based attendance tracking.  
- Enables GPS-based verification of check-ins.  
- Provides accurate, auditable data for payroll and HR.  
- Reduces administrative overhead.  
- Encourages punctuality and accountability.  
- Supports Demulla’s digital transformation strategy.  
- Continues operating even if other internal systems fail.

## Conclusion

The **Demulla Employee Check-in & Attendance Management System** is a modern, modular, and scalable solution designed to enhance transparency and accountability.  
It integrates smoothly with Demulla’s existing infrastructure while maintaining independence for maximum reliability.  
This system positions Demulla for sustainable growth, operational efficiency, and a stronger digital foundation.


## 👨‍💻 Developer Information

**Developer:** [Gilbert Keter](https://dev.lmn.co.ke)  
**Email:** [gilbertketer759@gmail.com](mailto:gilbertketer759@gmail.com)  
**Phone:** [+254 759 104 865](tel:+254759104865)  
**Portfolio:** [https://dev.lmn.co.ke](https://dev.lmn.co.ke)  
**GitHub:** [https://github.com/gilbertketer](https://github.com/gilbertketer)  
**LinkedIn:** [https://www.linkedin.com/in/keter-gilbert-2251b0255](https://www.linkedin.com/in/keter-gilbert-2251b0255)

