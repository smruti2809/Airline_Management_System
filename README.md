# Airline Management System (AMS)

A Software Requirements Specification (SRS) for an Airline Management System — a centralized platform designed to modernize and automate core airline operations, replacing fragmented legacy systems with one unified solution.

## Documentation

- [SRS_Airline_Management.md](./SRS_Airline_Management.md) — Full Software Requirements Specification (v1.0), covering scope, interfaces, system features, and nonfunctional requirements.

## Purpose

Traditional airline systems are fragmented across separate platforms for scheduling, bookings, payments, check-in, crew management, and maintenance. AMS consolidates these into a single system that serves passengers, airline staff, administrators, crew, and regulatory authorities.

## Key Modules

| Module | Description |
|---|---|
| Flight Scheduling & Booking | Real-time flight search, seat selection, and reservation management with overbooking prevention |
| Payment Integration & E-Ticketing | Secure multi-method payments (cards, UPI, wallets, net banking) with instant e-ticket generation |
| Check-In & Boarding | Online/kiosk check-in, digital QR/barcode boarding passes, real-time gate updates |
| Crew Scheduling & Maintenance | Crew duty allocation, compliance tracking, and predictive aircraft maintenance |
| Analytics & Reporting | Dashboards and exportable reports (PDF/CSV/Excel) for revenue, operations, and compliance |

## Development Approach

AMS follows an Incremental Development Model, delivered in five phases:

1. Flight Scheduling & Booking
2. Payment Integration & E-Ticketing
3. Check-In & Boarding
4. Crew Scheduling & Maintenance
5. Analytics & Reporting

## Compliance & Standards

- IATA guidelines for flight operations
- DGCA (Directorate General of Civil Aviation) safety regulations
- PCI-DSS for payment security
- IEEE 830-1998 SRS documentation standard
- GDPR for user data privacy

## Prepared By

Diya Singh, Smruti Desai, Anushka Pawar, Pushkar Ghodke
RAIT

## Read More

See the full [SRS document](./SRS_Airline_Management.md) for detailed functional requirements, external interfaces, user classes, and nonfunctional requirements (performance, safety, security, and business rules).
