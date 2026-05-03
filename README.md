# ✈️ Airline Management System — Built on Salesforce CRM

> **Automating end-to-end airline operations — from flight scheduling to passenger booking — on an enterprise-grade CRM platform.**

---

## 📄 Published Research Paper

> This project is backed by a **peer-reviewed research paper** published in an international journal — validating the technical depth and real-world applicability of this system.

| Field | Details |
|---|---|
| 📰 **Journal** | International Journal of Engineering Research & Technology (IJERT) |
| 🔖 **ISSN** | 2278-0181 |
| 📅 **Volume / Issue** | Vol. 15, Issue 04, April 2026 |
| 🏷️ **Registration No** | IJERTV15IS040776 |
| 📆 **Published Date** | 13 April 2026 |
| 🔗 **Publisher** | [www.ijert.org](https://www.ijert.org/) |
| ✅ **Status** | Peer-Reviewed & Certified |
| 📜 **License** | Creative Commons Attribution 4.0 International |

**Author:** Mr. Prathamesh Killol  
**Institution:** Department of Computer Science & Engineering, PRMCEAM, Badnera, Maharashtra – 444701, India

> 🏅 *Certificate of Publication issued by Chief Editor, IJERT — Registration No: IJERTV15IS040776, Date: 13-04-2026*

---

## 📌 Problem Statement

Traditional airline management relies on fragmented, manual workflows:

- Booking data spread across disconnected spreadsheets and legacy tools
- No real-time seat availability tracking, leading to overbooking errors
- Manual confirmation emails causing delays and human error
- Scheduling conflicts arising from siloed flight, aircraft, and staff data
- Zero visibility into operational performance or revenue trends for decision-makers
- Data duplication and inconsistency across booking, passenger, and payment records

These inefficiencies cost time, money, and passenger trust. The need is clear: a **unified, automated, and scalable system** that handles operations end-to-end without manual intervention.

---

## 💡 Solution Overview

This project delivers a fully functional **Airline Management System** built natively on the **Salesforce Platform**, leveraging its CRM backbone, declarative automation, and custom development capabilities.

The system centralises flight data, passenger records, bookings, payments, aircraft, and staff into a single source of truth — with automated workflows, real-time seat maps, and instant confirmation emails replacing every manual touchpoint.

**Core approach:**
- 6-object relational data model designed with Salesforce Schema Builder
- LWC-powered UI for dynamic seat selection and booking management
- Apex Triggers enforce complex business rules at the database layer
- Flow Builder automates post-booking actions (confirmation emails, flight alerts)
- Role-based security controls access across operational roles
- Reports & Dashboards surface live KPIs for decision-makers

---

## 🚀 Key Features

- **Flight Scheduling** — Create and manage flights with source/destination airports, departure/arrival times, aircraft assignment, and live status tracking (On-Time, Delayed, Cancelled)
- **Seat Map Visualisation** — Real-time interactive seat map built in LWC; available seats shown in green, booked in red — updates live on each booking transaction
- **Passenger Management** — Full CRUD for passenger profiles (name, email, phone, passport) linked directly to booking records
- **Booking & Payment Processing** — End-to-end booking lifecycle with seat assignment, status tracking, and payment validation via Apex Triggers
- **Automated Confirmation Emails** — Record-Triggered Flow fires post-booking, sending personalised confirmation emails with seat number — zero manual effort
- **Overbooking Prevention** — Apex Triggers validate every booking against aircraft seating capacity; booking is blocked if no seats are available
- **Aircraft & Staff Management** — Aircraft assigned to flights; crew allocation tracked through Staff object linked to Flight records
- **Role-Based Access Control** — Salesforce profiles and permission sets enforce who can create flights, manage bookings, or view financial reports
- **Reports & Dashboards** — Pre-built dashboards tracking occupancy rates, booking trends, flight status distribution, and payment analytics

---

## 🏗️ System Architecture & Data Flow

The system is built on a **4-layer Salesforce architecture**:

```
┌─────────────────────────────────────────────────────┐
│             PRESENTATION LAYER                      │
│   Lightning Web Components (LWC) + Dashboards       │
│   → Seat Map UI, Booking Forms, Operational Views   │
└────────────────────────┬────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────┐
│             AUTOMATION LAYER                        │
│   Salesforce Flow Builder (Record-Triggered Flows)  │
│   → Booking Confirmation Emails, Flight Alerts      │
└────────────────────────┬────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────┐
│          APPLICATION LOGIC LAYER                    │
│   Apex Triggers + Validation Rules                  │
│   → Seat Allocation, Overbooking Prevention,        │
│     Payment Validation, Data Integrity              │
└────────────────────────┬────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────┐
│                DATA LAYER                           │
│   Salesforce Custom Objects (Schema Builder)        │
│   → Flight, Passenger, Booking, Payment,            │
│     Aircraft, Staff                                 │
└─────────────────────────────────────────────────────┘
```

**End-to-end user flow (as documented in the published paper):**

```
User Visit
    │
    ▼
Search & Book Flight (LWC UI)
    │
    ▼
Apex Trigger fires on Booking save
    │  → Validates seat availability
    │  → Prevents overbooking
    │  → Updates Available_Seats__c on Flight
    ▼
Booking Record confirmed in database
    │
    ▼
Flow Builder triggers automatically
    │  → Fetches passenger email
    │  → Sends personalised confirmation (seat no. included)
    ▼
Receive Notification (Gmail)
    │
    ▼
Check-In & Travel
    │  → Booking data stored
    │  → Daily reminders via Salesforce Automation
    ▼
Data & Reminders (Salesforce Backend)
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Platform | Salesforce CRM (Developer Edition) |
| Frontend | Lightning Web Components (LWC) |
| Backend | Apex Classes & Triggers |
| Database Query | SOQL |
| Automation | Flow Builder — Record-Triggered After-Save Flows |
| Data Modelling | Schema Builder |
| Reporting | Salesforce Reports & Dashboards |
| Email | Salesforce Email Alerts via Flow |
| Security | Profiles, Permission Sets, Role Hierarchy |

---

## ⚙️ Salesforce Components — Built With Purpose

### 🗃️ Data Model — 6 Custom Objects (Schema Builder)

Designed a fully normalised relational schema covering all airline operational entities:

| Object | Key Fields | Relationship |
|---|---|---|
| `Flight__c` | flight_number, departure_city, arrival_city, departure_time, arrival_time | 1:N → Booking, Aircraft, Staff |
| `Passenger__c` | name, email, phone, passport_number | 1:N → Booking |
| `Booking__c` | booking_date, seat_number, status, passenger_id (FK), flight_id (FK) | Junction: Passenger ↔ Flight |
| `Payment__c` | amount, payment_method, payment_date | 1:1 → Booking |
| `Aircraft__c` | flight_number, departure_city, arrival_city, departure_time, arrival_time | 1:N → Booking |
| `Staff__c` | name, role, phone, flight_id (FK) | N:1 → Flight |

**Key relationships:**
- Passenger → Booking: **One-to-Many** (one passenger, multiple bookings)
- Booking → Payment: **One-to-One** (each booking has exactly one payment record)
- Flight → Aircraft & Staff: **Associated** (aircraft assignment + crew allocation per flight)

### ⚡ Apex Triggers — Business Logic at the Data Layer

Three critical rules enforced programmatically:
- **Automated Seat Allocation** — Identifies and assigns an available seat during booking creation
- **Overbooking Prevention** — Validates booking count against aircraft seating capacity before allowing record save
- **Payment Validation** — Booking status updates to "Confirmed" only after payment record is successfully created

Written following the **Trigger Handler pattern** — logic lives in handler classes, not directly in trigger files, ensuring maintainability and testability.

### 🔄 Flow Builder — Booking Confirmation Flow

A **Record-Triggered After-Save Flow** (`Booking_Confirmation_Flow`) activates on every new Booking record:
1. Fetches passenger name and email from the linked Passenger record
2. Constructs a personalised message body with flight details and seat number
3. Dispatches confirmation email automatically via Salesforce email service

A second flow fires when Flight details are updated — notifying affected passengers and staff of schedule changes or delays in real time.

### 🖥️ Lightning Web Components (LWC)

Built a custom **Seat Map component** that renders all seats dynamically, colour-codes availability in real time (🟢 available / 🔴 booked), and handles booking interactions — no third-party tool required.

### ✅ Validation Rules
- Departure time cannot be set after arrival time
- Booking creation blocked when `Available_Seats__c = 0`
- Mandatory field enforcement before any record save

### 📊 Reports & Dashboards
Operational dashboard tracking: flight status distribution, seat occupancy per flight, booking volume over time, revenue by route — enabling data-driven decisions without manual exports.

---

## 📊 Key Learnings & Outcomes

**Technical Skills Developed:**
- Designed a normalised, 6-object relational data model from scratch using Salesforce Schema Builder
- Built reusable LWC components with `@wire` adapters for real-time data binding
- Implemented trigger-based automation following the **Trigger Handler pattern** to keep business logic maintainable and testable
- Understood Salesforce **governor limits** and wrote bulkified Apex to handle large data volumes safely
- Made informed architectural decisions on **when to use Flow (declarative) vs. Apex (programmatic)**
- Implemented **role-based security** using Salesforce profiles and permission sets

**Research Contributions (Published — IJERT April 2026):**
- Demonstrated that a CRM-driven cloud platform (Salesforce) can effectively modernise airline operational management
- Showed how Schema Builder's visual relational modelling reduces development time and improves system maintainability
- Proved that record-triggered flows outperform manual email processes in speed and consistency
- Identified future directions: AI demand forecasting, real-time flight monitoring, advanced cloud deployment strategies

---

## 🎯 Business Impact

| Area | Before (Manual) | After (This System) |
|---|---|---|
| Booking confirmation | Hours, error-prone | Automated in seconds |
| Seat overbooking | Frequent (manual tracking) | Eliminated via Apex validation |
| Data entry errors | Common across systems | Minimised via validation rules |
| Operational visibility | Spreadsheet exports | Real-time dashboards |
| Staff-passenger communication | Manual emails | Automated flow notifications |
| System scalability | Fragmented, limited | Enterprise-grade cloud (Salesforce) |

---

## 📂 Project Structure

```
Airline-Management-System-Salesforce/
│
├── force-app/main/default/
│   ├── objects/
│   │   ├── Flight__c/              # Flight details, seat counts, status
│   │   ├── Passenger__c/           # Passenger profiles
│   │   ├── Booking__c/             # Booking records (junction object)
│   │   ├── Payment__c/             # Payment records (1:1 with Booking)
│   │   ├── Aircraft__c/            # Aircraft assigned to flights
│   │   └── Staff__c/               # Crew allocation per flight
│   │
│   ├── lwc/
│   │   └── seatMap/                # Dynamic real-time seat map component
│   │
│   ├── classes/
│   │   ├── BookingController.cls       # Apex controller for LWC
│   │   └── BookingTriggerHandler.cls   # Handler class (business logic)
│   │
│   ├── triggers/
│   │   └── BookingTrigger.trigger      # Thin trigger → delegates to handler
│   │
│   └── flows/
│       └── Booking_Confirmation_Flow.flow   # Post-booking email automation
│
├── screenshots/                    # UI screenshots from live Salesforce Org
├── paper/
│   ├── IJERTV15IS040776.pdf            # Published research paper
│   └── IJERTV15IS040776_Certi_A1.pdf  # Certificate of Publication
└── README.md
```

---

## 🧪 Future Enhancements

- **Payment Gateway Integration** — Stripe or Razorpay via Apex callouts for in-system payment processing
- **AI-Based Dynamic Pricing** — Einstein Analytics or external ML model to adjust seat prices based on demand and booking window
- **Real-Time Push Notifications** — Salesforce Platform Events to notify passengers of delays or cancellations instantly
- **Predictive Analytics** — Demand forecasting for flight load and revenue optimisation
- **Multi-Leg Booking Support** — Extend data model to handle connecting flights and layovers
- **Advanced Data Privacy** — Enhanced passenger data protection mechanisms for real-world deployment compliance

---

## 📸 Screenshots

| Flight Detail & Live Seat Map | Booking Confirmation Flow (Activated) |
|---|---|
| ![Flight Detail](screenshots/flight-detail-seatmap.png) | ![Flow](screenshots/booking-confirmation-flow.png) |

| New Flight Form | Confirmation Email (Gmail) |
|---|---|
| ![New Flight](screenshots/new-flight-form.png) | ![Email](screenshots/confirmation-email-gmail.png) |

*All screenshots from a live Salesforce Developer Org — data is real, not mocked.*

---

## 📑 Research Publication

**"Airline Management System using Salesforce Customer Relationship Management"**  
*Mr. Prathamesh Killol*  
Department of CSE(DS), PRMCEAM, Badnera, Maharashtra

| | |
|---|---|
| 📰 Journal | IJERT — ISSN: 2278-0181 |
| 📅 Published | Vol. 15, Issue 04, April 2026 |
| 🏷️ Reg. No | IJERTV15IS040776 |
| 📆 Date | 13-04-2026 |
| 🔗 Link | [www.ijert.org](https://www.ijert.org/) |

🏅 Peer-Reviewed | ✅ Certified by Chief Editor, IJERT | 📜 CC BY 4.0

---

## 📬 Contact

**Prathamesh Killol**  
B.E. Computer Science & Engineering | PRMCEAM, Badnera, Maharashtra  
Salesforce Developer | CRM & Automation | Published Researcher

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://linkedin.com/in/your-profile)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?style=flat&logo=github)](https://github.com/your-username)
[![Email](https://img.shields.io/badge/Email-Contact-red?style=flat&logo=gmail)](mailto:your@email.com)
[![IJERT](https://img.shields.io/badge/Published-IJERT%20April%202026-green?style=flat)](https://www.ijert.org/)

---

> *This project was built end-to-end on Salesforce and validated through peer-reviewed international research — demonstrating full-stack CRM development, system design, and automation skills applicable to enterprise environments.*
