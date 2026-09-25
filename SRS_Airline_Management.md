# SOFTWARE REQUIREMENTS SPECIFICATION
# AIRLINE MANAGEMENT SYSTEM
### Version 1.0 (approved)

**Prepared by:**
Diya Singh, Smruti Desai, Anushka Pawar, Pushkar Ghodke
RAIT

---

## Table of Contents
1. [Introduction](#1-introduction)
2. [Overall Description](#2-overall-description)
3. [External Interface Requirements](#3-external-interface-requirements)
4. [System Features](#4-system-features)
5. [Other Nonfunctional Requirements](#5-other-nonfunctional-requirements)

---

## 1. Introduction

### 1.1 Purpose

The **Airline Management System (AMS)** is a comprehensive software solution designed to modernize and automate airline operations. Traditional airline systems are fragmented, with separate platforms handling flight scheduling, passenger bookings, payments, check-in, boarding, crew scheduling, and maintenance tracking. This fragmentation results in operational inefficiencies, delayed communication, resource mismanagement, and poor customer experiences, ultimately leading to revenue loss and lower airline reliability.

The purpose of AMS is to streamline these processes into one centralized system that provides a unified interface for passengers, airline staff, administrators, and regulatory authorities. This SRS document serves as a blueprint for:

- Developers to implement robust features aligned with operational requirements.
- Airline management and stakeholders to ensure the system meets strategic business goals.
- Testers and auditors to verify the system's compliance with aviation standards and regulations.
- End users, including passengers and crew members, to interact with an efficient, secure, and user-friendly platform.

**Key functions addressed by AMS include:**

- Flight scheduling and reservation management with real-time availability updates.
- Secure digital payment processing and e-ticket generation.
- Check-in and boarding operations, including mobile boarding passes and gate assignment updates.
- Crew rostering and duty allocation with compliance to aviation labor laws.
- Aircraft maintenance tracking for operational safety and predictive servicing.
- Data analytics and reporting for management and regulatory audits.

The AMS will be developed using the **Incremental Development Model**, which enables:

- Early deployment of core modules such as booking and payments.
- Gradual integration of advanced features like analytics and crew scheduling.
- Continuous stakeholder feedback and reduced project risks.

This document fully specifies the **functional and non-functional requirements**, scope, assumptions, dependencies, and standards necessary to design, implement, and maintain AMS.

### 1.2 Document Conventions

This document follows standard conventions for clarity and consistency throughout all sections.

**a) Diagram conventions**
All models use standard UML notation for Use Case, Activity, and DFD representations, following IEEE 830 SRS guidelines.

**b) Terminology**
The system is referred to as **Airline Management System (AMS)** on first use and simply **AMS** thereafter. External systems are written in quotes when first introduced (e.g., "Payment Gateway API").

**c) Acronyms and abbreviations**

| Acronym | Meaning |
|---|---|
| AMS | Airline Management System |
| API | Application Programming Interface |
| OTP | One-Time Password |
| TLS | Transport Layer Security |
| SSL | Secure Sockets Layer |
| PCI-DSS | Payment Card Industry Data Security Standard |
| IATA | International Air Transport Association |
| DGCA | Directorate General of Civil Aviation |
| UI | User Interface |
| UML | Unified Modeling Language |
| DFD | Data Flow Diagram |
| PNR | Passenger Name Record |
| RBAC | Role-Based Access Control |
| 2FA | Two-Factor Authentication |
| GDPR | General Data Protection Regulation |
| ETL | Extract, Transform, Load |
| DBMS | Database Management System |
| FR/NFR | Functional / Non-Functional Requirement |

**d) Protocols Convention**
All network and system communications mentioned in this document follow standardized and secure protocols. References to web, data, and system communication imply the following conventions:

- All web-based interactions use secure HTTPS connections.
- Real-time updates are handled through WebSocket communication.
- Email transmissions are performed via standard mail protocols.
- File transfers between systems are assumed to use secure transfer mechanisms.
- All APIs follow REST architecture with JSON as the default data format unless specified otherwise.
- Any data exchange or synchronization described in later sections is expected to comply with these protocol standards.

### 1.3 Intended Audience

This SRS is intended for a wide range of readers, each with different objectives and levels of technical expertise:

- **Developers and Engineers:** To understand system requirements and design modular, scalable solutions.
- **Project Managers:** To plan resources, timelines, and deliverables for phased implementation.
- **Airline Operations Team:** To manage day-to-day functions such as flight scheduling, passenger services, and crew allocation.
- **Testers and Quality Assurance Teams:** To verify compliance, functionality, performance, and security of the system.
- **Regulatory Authorities:** To audit system compliance with aviation and data privacy laws.
- **Passengers (Indirect Users):** Though they will not read the SRS, their needs are reflected in user interface design and feature requirements.

### 1.4 Product Scope

The **Airline Management System (AMS)** is a centralized, end-to-end platform for managing all core airline operations. It focuses on delivering seamless passenger experiences, efficient resource utilization, and regulatory compliance through automation and data-driven insights.

**Primary Goals:**

- Replace outdated, isolated airline systems with a unified solution.
- Ensure real-time updates for passengers, crew, and administrators.
- Improve flight scheduling accuracy and reduce overbooking incidents.
- Provide robust payment processing with multiple secure payment options.
- Simplify check-in and boarding through digital boarding passes and automated gate assignments.
- Enable predictive aircraft maintenance tracking for safety and reliability.
- Generate detailed analytics and compliance reports for decision-making.

**Key Benefits:**

- **Operational Efficiency:** Streamlined workflows reduce delays and manual errors.
- **Customer Satisfaction:** Passengers receive timely notifications and a smooth booking experience.
- **Financial Control:** Improved revenue tracking and fraud prevention.
- **Scalability:** Easily adaptable for growing airline fleets and passenger bases.
- **Compliance:** Built-in features for IATA and government regulatory standards.

By implementing AMS, airlines can transform operations into a digital-first, integrated environment capable of meeting modern aviation demands.

### 1.5 References

1. IATA Guidelines for Flight Operations Management, v2025.
2. PCI-DSS Compliance Standards for secure payment processing.
3. IEEE Standard 830-1998 for Software Requirement Specification documentation.
4. OpenAPI Specification v3.1 for REST API integration.
5. DGCA (Directorate General of Civil Aviation) Safety Regulations, India v2025.
6. Airline Reservation System Integration Guide, v2024.
7. Airline industry research papers on operational efficiency and passenger management.
8. Stakeholder interviews and internal airline policy documents.

---

## 2. Overall Description

### 2.1 Product Perspective

The **Airline Management System (AMS)** is a centralized, integrated software platform built to modernize and streamline the operations of an airline. Current airline systems are often fragmented, with separate, legacy solutions handling booking, payment, check-in, crew management, and reporting. These disparate systems fail to synchronize data in real time, resulting in:

- Overbooking of flights.
- Communication delays between departments.
- Inefficient crew scheduling and resource allocation.
- Poor passenger experiences due to last-minute updates and errors.
- Complications in meeting regulatory compliance and audit requirements.

AMS is designed to replace these isolated systems with one unified solution that manages every operational aspect of an airline. It uses the Incremental Development Model, meaning the system will be built and deployed in phases (increments), each delivering a complete and functional set of features.

- **Increment 1 -- Flight Scheduling & Booking:** Search flights, seat selection, reservation system.
- **Increment 2 -- Payment Integration & E-Ticketing:** Secure online payments, digital ticket generation.
- **Increment 3 -- Check-In & Boarding:** Mobile/online check-in, boarding pass generation, gate assignment.
- **Increment 4 -- Crew Scheduling & Maintenance:** Crew duty allocation, predictive maintenance tracking.
- **Increment 5 -- Analytics & Reporting:** Dashboards, compliance reports, operational insights.

This phased approach enables early deployment of essential modules like booking and payment while subsequent increments add advanced features like maintenance tracking and analytics.

**System Context and Interfaces**

AMS interacts with internal components and external services to provide seamless airline operations.

- **Internal Interfaces:**
  - Centralized database for storing flight schedules, passenger records, bookings, payments, and crew details.
  - Internal APIs connecting booking, check-in, payment, and crew scheduling modules.
  - Authentication and authorization services to manage role-based access.

- **External Interfaces:**
  - **Payment Gateways:** Integration with banking systems, UPI, cards, and digital wallets for secure transactions.
  - **Notification Services:** SMS, email, and push notifications to keep passengers updated about bookings, delays, or cancellations.
  - **Government APIs:** Passenger verification and compliance reporting (e.g., DGCA).
  - **Partner Travel Platforms:** APIs for third-party agencies to access flight data and availability.

AMS can function as a stand-alone product for small airlines or as a scalable platform integrated with other enterprise systems for larger carriers.

### 2.2 Product Functions

The AMS provides a wide range of functionalities that cover every core airline operation. Below are its major, high-level functions:

**1. Flight Scheduling & Booking**
- Schedule flights with routes, timings, and seat layouts.
- Allow passengers to search, view availability, and book seats.
- Prevent overbooking with real-time seat updates.

**2. Payment Integration & E-Ticketing**
- Support secure multi-method payments (cards, UPI, wallets, net banking).
- Generate instant digital tickets after payment confirmation.
- Manage refunds, cancellations, and reconciliation.

**3. Check-In & On-Boarding**
- Provide online and mobile check-in options.
- Generate QR/barcode boarding passes.
- Update gate and flight information in real time.

**4. Crew Scheduling & Tracking**
- Assign crew based on certifications and duty hours.
- Manage shift schedules and compliance logs.
- Track crew availability and performance.

**5. Maintenance Management**
- Maintain aircraft inspection and service records.
- Schedule preventive maintenance to avoid breakdowns.
- Use predictive analytics for fault detection.

**6. Security Operation Management**
- Monitor passenger and baggage screening.
- Manage access control for restricted airport zones.
- Handle emergency incidents and ensure safety compliance.

**7. Analytics & Reporting**
- Generate dashboards for revenue and flight statistics.
- Create compliance and performance reports.
- Export insights in formats like PDF, CSV, and Excel.

### 2.3 User Classes and Characteristics

AMS is built for multiple user groups, each with different goals, access levels, and technical expertise. Clearly defining these user classes ensures role-based security, optimized workflows, and usability.

**Administrators**
- **Role & Responsibilities:** Configure system, oversee operations, ensure compliance.
- **Access Level:** Full access
- **Technical Expertise:** Advanced
- **Special Requirements:** Security dashboards, performance monitoring

**Airline Staff**
- **Role & Responsibilities:** Manage check-in, boarding, and passenger issues.
- **Access Level:** Moderate access
- **Technical Expertise:** Moderate
- **Special Requirements:** Simple interface, real-time updates

**Crew Members**
- **Role & Responsibilities:** View flight schedules, assigned duties, and submit availability updates.
- **Access Level:** Limited access
- **Technical Expertise:** Basic

**Passengers**
- **Role & Responsibilities:** Search flights, book tickets, check-in, and view boarding passes.
- **Access Level:** Personal data only
- **Technical Expertise:** Varies (basic to moderate)
- **Special Requirements:** Intuitive navigation, quick booking

**Regulatory Authorities**
- **Role & Responsibilities:** Audit compliance data and flight operations.
- **Access Level:** Read-only
- **Technical Expertise:** High
- **Special Requirements:** Secure access to reports only

**IT Support Team**
- **Role & Responsibilities:** Maintain uptime, troubleshoot issues, and manage backups.
- **Access Level:** Technical admin access
- **Technical Expertise:** Advanced
- **Special Requirements:** System diagnostics and alerts

### 2.4 Operating Environment

AMS is designed to function across diverse airline environments, from small regional carriers to global operators.

1. **Server Infrastructure**
   - Cloud-hosted or on-premise servers with high availability.
   - Multi-core processors, 16GB+ RAM, and SSD storage for fast performance.
   - Redundant backups and disaster recovery mechanisms.

2. **Passenger Devices**
   - Smartphones (Android, iOS) for mobile apps.
   - Web browsers: Chrome, Firefox, Safari, Edge.

3. **Staff Devices**
   - Desktop computers at check-in counters.
   - Kiosks for self-check-in.
   - Boarding pass printers and barcode scanners.

4. **Software Requirements**
   - Server OS: Linux or Windows Server.
   - Database: MySQL, PostgreSQL, or equivalent cloud databases.
   - APIs for payment, notification, and government integrations.

5. **Network**
   - Secure TLS/SSL connections for all transactions.

### 2.5 Design and Implementation Constraints

AMS development must adhere to strict regulatory and operational constraints:

1. **Compliance:**
   - Must meet IATA and DGCA standards for airline operations.
   - PCI-DSS compliance for handling payment data securely.

2. **Security:**
   - End-to-end encryption for sensitive data like passenger records and payments.
   - Multi-factor authentication for admins and staff.

3. **Performance:**
   - Flight search and booking operations must complete within **3 seconds** under normal load.
   - Real-time synchronization across booking, check-in, and crew scheduling.

4. **Scalability:**
   - Support for peak holiday traffic and growing airline fleets.

5. **Technology Stack:**
   - Backend: Node.js, Python, or Java (flexible depending on deployment).
   - Frontend: Web and mobile apps built using React or similar frameworks.

### 2.6 User Documentation

AMS will include detailed documentation to ensure smooth onboarding, usage, and troubleshooting.

1. **Quick Start Guides** -- For passengers: booking, check-in, boarding pass retrieval. For staff: gate management, check-in workflows.
2. **Role-Based Manuals** -- Separate guides for administrators, staff, crew members, and auditors.
3. **Interactive Tutorials** -- Short video walkthroughs for key operations.
4. **Troubleshooting and FAQs** -- Common issues with step-by-step resolutions.
5. **System Maintenance Guide** -- For IT teams to perform backups, monitor uptime, and update software.
6. **Online Help Center** -- Built-in search feature for quick assistance.

### 2.7 Assumptions and Dependencies

**Assumptions:**

- Airlines will have stable internet connectivity at all operational points.
- Staff will receive proper training before full deployment.
- Passenger devices will meet minimum hardware requirements (modern browsers and smartphones).

**Dependencies:**

- External payment gateways for online transactions.
- Notification service providers for SMS and email updates.
- Government APIs for compliance reporting and passenger verification.
- Cloud infrastructure for hosting and scaling services.

---

## 3. External Interface Requirements

This section specifies how the **Airline Management System (AMS)** will interact with external entities, including users, hardware devices, third-party software, and communication protocols. It defines the characteristics and requirements of all interfaces to ensure seamless integration and optimal system performance.

### 3.1 User Interfaces

The **User Interface (UI)** of AMS plays a vital role in ensuring smooth and efficient interaction between the system and its stakeholders, including passengers, airline staff, administrators, crew members, and regulatory authorities. The UI must be user-friendly, responsive, and accessible, while maintaining a consistent design across different platforms such as web and mobile.

**3.1.1 General UI Requirements**

- Must follow Material Design guidelines or equivalent industry standards for consistency and clarity.
- Responsive design for desktops, tablets, and mobile devices.
- Clear and intuitive navigation with meaningful icons and text labels.
- Support for multiple languages to cater to international passengers and staff.
- Accessibility compliance with features like screen reader support, high-contrast mode, and keyboard navigation.
- Error messages must be descriptive, providing corrective suggestions.
- Notifications should be clear and concise, using banners, pop-ups, or push notifications.

**3.1.2 User Interface Components**

**1. Passenger Portal**
*Purpose:* Allows passengers to search for flights, make reservations, manage bookings, check in, and access their boarding passes.

*Key Features:*
- Flight search with filters such as date, time, source, destination, class, and direct/non-stop flights.
- Seat selection using a visual seat map.
- Booking summary and multiple payment options.
- Mobile and web-based check-in functionality.
- Digital boarding pass with QR or barcode for scanning at boarding gates.
- Booking history with cancellation and refund options.
- Real-time flight notifications for delays, gate changes, or cancellations.

*Sample Layout:*
- **Home Page:** Flight search bar with promotional offers and recent searches.
- **Booking Page:** Visual seat map, fare details, and add-ons like extra baggage or meal preferences.
- **Check-In Page:** Seat confirmation and boarding pass download option.

**2. Airline Staff Interface**
*Purpose:* Used by check-in agents, gate staff, and ground crew to manage passenger handling and flight operations efficiently.

*Key Features:*
- Passenger check-in and identity verification system.
- Gate management tools for boarding operations and flight coordination.
- Real-time dashboard for monitoring flight status and passenger flow.
- Passenger issue handling such as complaints and lost baggage reporting.
- Internal staff communication and notifications.

*Sample Layout:*
- **Dashboard:** List of active flights, delayed flights, and check-in status.
- **Check-In Module:** Search passengers by booking ID, ticket number, or passport.
- **Gate Management:** Boarding announcements and gate reassignment alerts.

**3. Admin Dashboard**
*Purpose:* Provides administrators with a centralized view to oversee and manage airline operations.

*Key Features:*
- Flight scheduling and management interface.
- Role-based access and user account management.
- Revenue and operational analytics.
- System performance and uptime monitoring.
- Comprehensive compliance reporting.

*Sample Layout:*
- **Main Dashboard:** Displays total flights, revenue, cancellations, and real-time passenger metrics.
- **Report Section:** Generate, view, and export reports in formats such as PDF and Excel.

**4. Crew Portal**
*Purpose:* Enables pilots and flight crew to view their schedules, duties, and compliance data.

*Key Features:*
- View upcoming flights and duty hours.
- Submit availability and leave requests.
- Receive updates on last-minute changes to schedules.
- View compliance reports for rest periods and certifications.

**3.1.3 Common UI Standards**

- **Font Family:** Clean sans-serif fonts like Arial or Roboto for readability.
- **Primary Colors:** Blue (#007BFF) for action buttons/highlights, White (#FFFFFF) for backgrounds, Gray (#6C757D) for secondary/muted text.
- **Error Notifications:** Red banner with descriptive text for errors.
- **Success Notifications:** Green banner for successful actions like booking confirmations.
- **Consistent Layouts:** All screens must maintain consistent headers, footers, and navigation menus.

### 3.2 Hardware Interfaces

AMS integrates with various hardware components at airports and operational centres to support efficient airline operations. Below are the key hardware interactions:

- **Boarding Gate Scanners:** Used to scan digital or printed boarding passes for verification at the boarding gate using barcode or QR code technology.
- **Printers:** Used by airline staff to print boarding passes, payment receipts, and operational reports. Supports both wired and wireless connectivity.
- **Baggage Tag Printers:** Generates baggage tracking labels to monitor and manage passenger luggage. These devices connect through Bluetooth or Wi-Fi for real-time updates.
- **Airport Display Screens:** Used to display flight schedules, gate information, and announcements to passengers. The system pushes data to these screens through real-time APIs.

### 3.3 Software Interfaces

AMS must connect with various internal and external software systems to perform its functions effectively. Below are the critical integrations:

- **Payment Gateway:** Provides secure and seamless online payment processing through cards, UPI, digital wallets, and other methods. Integration is done via REST APIs and must be PCI-DSS compliant.
- **Notification Services:** Used to send flight updates and alerts through SMS, emails, and push notifications. Integration is done using webhook and API-based services.
- **Government Verification APIs:** Ensures passenger identity verification and compliance reporting to government authorities. Authentication and secure communication are done using OAuth tokens and encrypted data transfer.
- **Cloud Database:** Centralized storage of passenger data, bookings, flight schedules, crew information, and maintenance. Supports both SQL and NoSQL data structures.
- **Airline Partner Platforms:** Enables data sharing with third-party travel agencies and partner platforms. Uses JSON or XML-based API integration for flight data exchange.
- **Analytics Tools:** For generating reports, dashboards, and business insights. Integrates with data pipelines for ETL (Extract, Transform, Load) processes.

### 3.4 Communications Interfaces

The AMS relies on robust, secure, and real-time communication systems to ensure continuous and reliable airline operations.

**3.4.1 Communication Standards**
- **HTTPS Protocol:** For secure web communication between client and server.
- **TLS/SSL Encryption:** For encrypting sensitive data like passenger information and payment details.
- **Network Bandwidth:** Minimum bandwidth of 5 Mbps per terminal for uninterrupted access.
- **Redundancy:** Backup internet connections for failover in case of network failures.

**3.4.2 Message Formats**
- **Booking Data:** JSON format containing passenger details, flight information, and seat allocation.
- **Payment Data:** Encrypted tokens following PCI-DSS guidelines to ensure security and privacy.
- **Notification Data:**
  - *Email:* HTML format for rich notifications.
  - *SMS:* Plain text format containing essential flight details.
  - *Push Notifications:* JSON payload for mobile notifications.

**3.4.3 Synchronization Mechanisms**
- Real-time synchronization between modules like booking, check-in, and crew scheduling.
- Automatic retry mechanism for data transmission failures due to network issues.
- WebSocket technology for live updates such as gate changes and flight delays.

**3.4.4 Security Protocols**
- **Data Encryption:** All sensitive information, including personal and financial data, must be encrypted using AES-256.
- **Authentication Mechanisms:** Two-Factor Authentication (2FA) for administrators and airline staff; OTP-based verification for passengers during booking and check-in.
- **Access Control:** Strict role-based access levels to limit permissions to only necessary functions.

---

## 4. System Features

This section provides a comprehensive description of the core functional modules of the Airline Management System (AMS). Each feature includes its purpose, priority, expected user interactions, and the functional requirements necessary to support the feature.

The features are presented incrementally, reflecting the development model adopted for AMS. Each system feature is described with three subsections:

1. **Description and Priority** -- An overview of the feature and its importance.
2. **Stimulus/Response Sequences** -- How the system responds to specific user actions or events.
3. **Functional Requirements** -- Detailed list of required functions for proper operation.

### 4.1 Flight Scheduling and Booking

**4.1.1 Description and Priority**

This is the core module of AMS and has high priority, as it forms the foundation for all other airline operations. The module enables administrators to create and manage flight schedules, including routes, timing, seat layouts, and aircraft allocation. It also allows passengers to search for flights, view availability in real time, and reserve seats without errors or overbooking.

Its primary objective is to ensure that passenger bookings are accurate, secure, and efficient, while providing the airline with precise control over flight capacities.

**4.1.2 Stimulus/Response Sequences**

- A passenger logs into the system and enters details like travel date, source, and destination to search for available flights.
  - The system responds by displaying all matching flights with departure times, arrival times, fare classes, and available seats.
- The passenger selects a flight and preferred seat.
  - The system temporarily locks that seat to prevent other passengers from booking it simultaneously.
- The passenger proceeds to checkout and confirms booking details.
  - The system calculates the total fare and presents payment options.
- Once payment is successful, the system confirms the reservation, generates an e-ticket, and sends a confirmation email or SMS.
- In case of failed payment, the system automatically releases the locked seat back into the availability pool and notifies the user.

**4.1.3 Functional Requirements**

- The system shall allow real-time search and filtering of flights by date, route, class, and availability.
- The system shall prevent overbooking by maintaining a synchronized seat inventory.
- The system shall allow seat selection using a visual seat map.
- The system shall generate a unique booking reference number (PNR) for each confirmed reservation.
- The system shall automatically release locked seats if payment is not completed within a predefined time window.
- The system shall send booking confirmation via email and SMS with flight and passenger details.
- The system shall maintain booking history for passengers and staff access.

### 4.2 Payment Integration and E-Ticketing

**4.2.1 Description and Priority**

This feature is of high priority, as secure and reliable payment processing is critical for airline operations. The module integrates with multiple payment methods, including credit/debit cards, UPI, digital wallets, and net banking, ensuring a smooth booking experience for passengers.

It also handles the generation of digital tickets (e-tickets) immediately after successful payment, ensuring that passengers receive confirmation without delays.

**4.2.2 Stimulus/Response Sequences**

- After selecting a flight and confirming details, the passenger chooses a preferred payment method.
  - The system securely redirects to the chosen payment gateway.
- The passenger completes the payment by providing necessary credentials, such as card details or UPI PIN.
  - The system validates the payment in real time.
- If the payment is successful:
  - The system confirms the booking.
  - An e-ticket is generated automatically.
  - The passenger is notified via SMS and email.
- If the payment fails:
  - The system notifies the passenger of the failure.
  - The booking is canceled automatically, and the seat is released.

**4.2.3 Functional Requirements**

- The system shall integrate with at least three payment gateways for redundancy.
- The system shall comply with PCI-DSS standards to ensure secure handling of financial data.
- The system shall support multiple payment methods, including cards, UPI, wallets, and net banking.
- The system shall automatically generate a digital ticket upon successful payment.
- The system shall send notifications for successful or failed transactions.
- The system shall maintain transaction logs for auditing and refund processing.

### 4.3 Check-In and Boarding

**4.3.1 Description and Priority**

The check-in and boarding feature has high priority as it directly impacts passenger experience and operational efficiency. It enables passengers to check-in online or at kiosks, select or confirm seats, and receive boarding passes digitally. It also helps airline staff manage boarding processes, including gate assignments and last-minute flight changes.

**4.3.2 Stimulus/Response Sequences**

- A passenger logs into the system before the flight and chooses to check in online.
  - The system verifies the booking details and displays available seat options.
- The passenger selects a seat and confirms check-in.
  - The system generates a digital boarding pass with a QR or barcode.
- At the airport:
  - The passenger scans the boarding pass at a kiosk or gate scanner.
  - The system validates the pass and updates the boarding status in real time.
- If the boarding pass is invalid or duplicated, the system alerts staff immediately.

**4.3.3 Functional Requirements**

- The system shall allow online and kiosk-based check-ins.
- The system shall generate secure digital boarding passes.
- The system shall update real-time gate assignments.
- The system shall validate boarding passes at check-in counters and boarding gates.
- The system shall notify passengers of flight delays or gate changes instantly.
- The system shall maintain check-in logs for auditing and reporting.

### 4.4 Crew Scheduling and Maintenance

**4.4.1 Description and Priority**

This feature has medium to high priority, focusing on airline staff and flight crew management. It ensures proper allocation of pilots and crew to flights, compliance with aviation labor rules, and maintenance tracking for aircraft.

It also supports predictive maintenance planning, reducing downtime and improving flight safety.

**4.4.2 Stimulus/Response Sequences**

- The administrator enters crew details, certifications, and availability into the system.
  - The system suggests optimal crew assignments for upcoming flights.
- The crew member receives a notification about assigned flights and duty schedules.
  - They can confirm availability or request leave through the crew portal.
- For maintenance:
  - The system logs routine inspections and service records.
  - If predictive analytics detect a potential issue, an alert is sent to the maintenance team.

**4.4.3 Functional Requirements**

- The system shall allocate crew based on availability, qualifications, and legal duty limits.
- The system shall track and store historical data on crew assignments.
- The system shall generate crew duty rosters automatically.
- The system shall log aircraft maintenance history and schedule inspections.
- The system shall provide alerts for predictive maintenance needs.
- The system shall restrict flights from being scheduled if required maintenance is pending.

### 4.5 Analytics and Reporting

**4.5.1 Description and Priority**

This feature has medium priority, focused on providing data-driven insights to improve airline decision-making and operational performance. The module generates real-time and historical reports for administrators, auditors, and regulatory authorities.

It covers operational metrics, revenue statistics, compliance status, and passenger trends.

**4.5.2 Stimulus/Response Sequences**

- The administrator selects a report type and applies filters such as date range or flight routes.
  - The system fetches data from the central database.
- The system processes the data and generates a report.
  - The report can be viewed on-screen or exported in PDF, Excel, or CSV formats.
- The administrator can schedule automated report generation for recurring audits.

**4.5.3 Functional Requirements**

- The system shall generate reports on bookings, revenues, flight delays, cancellations, and maintenance activities.
- The system shall allow filtering and sorting of report data by date, route, or other parameters.
- The system shall support export of reports in multiple formats such as PDF, CSV, and Excel.
- The system shall provide dashboards with real-time performance metrics.

---

## 5. Other Nonfunctional Requirements

This section outlines the nonfunctional requirements (NFRs) for the Airline Management System. Unlike functional requirements, which define *what the system does*, nonfunctional requirements focus on *how the system operates*. These requirements ensure that AMS is secure, reliable, efficient, and compliant with aviation and IT industry standards.

### 5.1 Performance Requirements

The performance of AMS is critical to delivering a smooth passenger experience and supporting airline operations, especially during peak travel times. The system must be designed to handle high volumes of concurrent users, real-time updates, and fast response times.

**Detailed Requirements:**

- The system shall process passenger flight searches and display results within 3 seconds under normal load conditions.
- The system shall support at least 10,000 concurrent users during peak travel seasons without performance degradation.
- The database shall handle 1 million booking records with real-time read and write capabilities.
- Payment processing, including authorization and confirmation, shall complete within 5 seconds.
- The system shall update booking, check-in, and boarding information instantly across all connected modules to prevent conflicts like double bookings.
- Notifications such as flight delays or gate changes must be sent to passengers within 1 second of the event being logged.
- The system shall maintain 99.9% uptime to ensure operational continuity.
- Scheduled maintenance shall not exceed 2 hours per month, and must be announced at least 24 hours in advance.
- The application shall optimize resource usage to reduce server costs and ensure scalability during sudden demand spikes.
- The system shall support real-time synchronization between internal modules (booking, check-in, maintenance) and external services like payment gateways and notification APIs.

### 5.2 Safety Requirements

Safety is of utmost importance in airline operations, as system failures can lead to serious operational disruptions and passenger risks. The AMS must include safeguards to ensure data integrity, fault tolerance, and system reliability.

**Detailed Requirements:**

- The system shall provide automatic data backups every hour to prevent data loss.
- In case of critical system failure, data recovery shall be possible within 30 minutes.
- Flight data, crew assignments, and passenger information must be stored in secure, redundant servers with disaster recovery capabilities.
- The system shall provide error logging and monitoring to detect issues before they escalate into failures.
- Any module crash shall not affect other modules due to modular architecture and isolation mechanisms.
- The system shall prevent booking of flights that have maintenance or safety alerts flagged.
- Backup servers shall automatically take over within 10 seconds of a primary server failure.
- Maintenance tracking logs must be protected against unauthorized modifications to ensure aircraft safety compliance.
- In case of network disruptions, the system shall store transactions locally and synchronize automatically once the connection is restored.
- Critical alerts, such as maintenance warnings or crew shortages, must be immediately communicated to administrators via SMS and email.

### 5.3 Security Requirements

Airline systems handle highly sensitive data, including passenger details, payment information, and operational data. Therefore, AMS must implement robust security protocols to protect against threats like hacking, data breaches, and unauthorized access.

**Detailed Requirements:**

- All sensitive data, including passwords and payment information, must be encrypted using AES-256 encryption.
- All communications between clients, servers, and third-party services must use HTTPS with TLS/SSL encryption.
- The system shall enforce role-based access control (RBAC) to limit access to sensitive modules based on user roles (e.g., passenger, staff, admin).
- Staff and administrators must log in using two-factor authentication (2FA).
- Passengers must verify identity using OTP-based authentication for booking and check-in.
- The system shall maintain audit logs of all transactions and user activities, stored securely for at least one year.
- The system shall comply with PCI-DSS standards for handling payment card information.
- All passwords must be stored using salted and hashed algorithms such as SHA-256.
- The system shall detect suspicious activities, such as multiple failed login attempts, and automatically lock the account temporarily.
- Regular security audits and penetration tests must be conducted every quarter to identify vulnerabilities.
- The system must support automatic session timeouts after 15 minutes of inactivity to prevent unauthorized access.
- User data shall comply with data privacy laws, such as GDPR, and must only be used for operational purposes.

### 5.4 Software Quality Attributes

The quality attributes define how well the AMS performs under different conditions. These attributes ensure that the system is scalable, maintainable, reliable, and user-friendly.

- **Adaptability:** The system must be flexible to accommodate new features, third-party integrations, or additional user roles without requiring major redesigns.
- **Availability:** The AMS must be available 24/7, with minimal downtime to support global airline operations.
- **Correctness:** All calculations, such as ticket fares, taxes, and discounts, must be accurate and validated before transactions are processed.
- **Flexibility:** The system must support multiple device types, operating systems, and screen resolutions, including mobile devices, kiosks, and desktop systems.
- **Maintainability:** Code should be modular and well-documented to simplify troubleshooting, updates, and feature enhancements.
- **Portability:** The system must be deployable on both cloud-based and on-premise infrastructures, supporting Linux and Windows environments.
- **Reliability:** AMS must perform consistently, even during peak traffic, without data corruption or system crashes.
- **Reusability:** Core components like booking, payment, and notifications must be reusable in other related airline projects or expansions.
- **Robustness:** The system must handle unexpected inputs gracefully, such as invalid bookings or duplicate requests, without crashing.
- **Testability:** Each module must be independently testable, with automated test suites to verify functionality before deployment.
- **Usability:** The user interface must be intuitive, with minimal learning curve for passengers and staff.

### 5.5 Business Rules

Business rules define the operational policies and procedures that AMS must enforce. These rules ensure consistent decision-making, compliance with aviation regulations, and proper airline management.

**Booking and Reservation Rules:**
- A seat must be locked for a maximum of 10 minutes during booking until payment is completed.
- Overbooking is strictly prohibited; bookings must not exceed actual seat capacity.
- Refunds must be processed within 7 business days of cancellation.
- Special fares (e.g., discounts for senior citizens or military personnel) must be applied automatically based on eligibility.

**Payment Rules:**
- Only verified and authenticated payment methods are allowed.
- Failed transactions must be logged with error codes for troubleshooting.
- Refunds must be processed using the original payment method only.

**Check-In and Boarding Rules:**
- Online check-in must open 24 hours before departure and close 1 hour before flight time.
- Gate assignments must be finalized at least 30 minutes before boarding.
- Boarding passes must include flight number, gate number, and passenger details.

**Crew Scheduling Rules:**
- Crew duty hours must comply with aviation labor laws, ensuring adequate rest periods between shifts.
- Only certified staff members can be assigned to specialized tasks like piloting or safety checks.

**Maintenance Rules:**
- Aircraft cannot be scheduled for flights if pending maintenance checks are flagged.
- Maintenance logs must be locked and digitally signed to prevent tampering.

**Reporting and Compliance Rules:**
- Monthly compliance reports must be automatically generated and archived.
- Regulatory data must be accessible only to authorized government personnel.
- All reports must be digitally signed and time-stamped.
