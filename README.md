# Akademi – Smart Campus Operations Hub

**Akademi – Smart Campus Operations Hub** is a full-stack web application built to streamline university resource and facility management. It replaces manual, error-prone campus operations with a centralized digital platform.

Built with **Spring Boot** (backend), **React** (frontend), and **MySQL** (database), following a microservices architecture with role-based access control via **OAuth 2.0**.

---

##  Key Modules

| Module | Description |
|---|---|
| Resource Management | Manage campus facilities (lecture halls, labs, equipment) |
| Booking Management | Request, approve/reject, and track facility bookings |
| Incident & Ticket Management | Report maintenance issues with image attachments and SLA tracking |
| Comment Service | Threaded comments on incident tickets |
| Notification Service | Real-time alerts for booking and ticket updates |
| User & Auth Service | OAuth 2.0 login, role management (USER / ADMIN / TECHNICIAN) |

---

## 🔧 Tech Stack

- **Backend:** Spring Boot, Maven, Apache Tomcat
- **Frontend:** React
- **Database:** MySQL
- **Auth:** OAuth 2.0 (Google)
- **Testing:** Postman
- **Version Control:** Git

---

## 👤 My Contribution – Incident & Ticket Service + Comment Service

I was responsible for **Module C: Incident & Ticket Management** and the **Comment Service**.

### 🔧 Backend

- Full CRUD for incident tickets with enums (priority, category, status)
- Image attachment upload (up to 3 files; JPG, PNG, WEBP, GIF; 5MB each)
- Technician assignment and status lifecycle management
- Auto-escalation via a scheduled **SLA Timer** — tickets flagged and escalated based on priority deadlines (CRITICAL: 4h, HIGH: 24h, MEDIUM: 72h, LOW: 168h)
- Role-based delete restrictions (students: OPEN/REJECTED only; admins: CLOSED/REJECTED only)
- Circular JPA serialization fix via `UserSummaryDto`
- Spring Security rule ordering fixes
- Full Comment Service (add, view, edit, delete)

---

### 🖥️ Frontend Pages

#### Incidents – User View (`/incidents`)
Students see all their reported incidents as cards, each showing status, priority, category, location, description, image thumbnail, and date. Users can delete their own OPEN tickets and access comments per ticket via a Comments button.

#### Incident Detail (`/incidents/:id`)
A full detail view showing ticket description, attachments, location, reporter, assigned technician, and SLA status with time remaining. A live comments sidebar allows admins, technicians, and users to post, edit, and delete comments in real time.

#### Technician Dashboard (`/technician`)
A dedicated workspace for technicians with summary cards for Total Assigned, Open, In Progress, and Resolved counts. Tickets are grouped by status — technicians can start work, add notes, or mark tickets resolved directly from the dashboard.

#### SLA Monitor (`/admin/sla`) — Admin only
Real-time monitoring of incident response and resolution times. Shows total incidents, open/in-progress count, and SLA breach count. Table lists all incidents with SLA health (On Track / Response Breached / Resolve Breached), time remaining, and a quick-assign dropdown to assign technicians inline. Filterable by All / Open / Breached / Escalated.

<img width="975" height="491" alt="image" src="https://github.com/user-attachments/assets/0fecaa64-0506-4f3c-a893-ac07c384bae6" />
<img width="975" height="523" alt="image" src="https://github.com/user-attachments/assets/fa0df10f-586a-4bfe-9d8b-b3677fe55111" />
<img width="975" height="516" alt="image" src="https://github.com/user-attachments/assets/c56b3159-e613-4be0-b142-1bbd441bb0a3" />
<img width="975" height="518" alt="image" src="https://github.com/user-attachments/assets/efdb3f8c-2420-45ef-abe6-3044b5862daf" />
<img width="975" height="519" alt="image" src="https://github.com/user-attachments/assets/2d0b50f7-2549-4bba-88f3-1f5bbd93f7b9" />
<img width="975" height="515" alt="image" src="https://github.com/user-attachments/assets/820e8320-270f-44d4-9209-025bf4f95b82" />

