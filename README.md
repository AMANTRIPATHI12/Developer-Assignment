# Namoza Developer Assignment

**Candidate:** Aman Tripathi

This repository contains the completed submission for the **Namoza Developer Assignment (Developer – Position 1: Client Web + Martech)**.

---

# Repository Structure

```
Developer-Assignment/
│
├── README.md
│
├── Task1/
│   └── GTM-Schema.md
│
├── Task2/
│   ├── index.html
│   └── PageSpeed.png
│
└── Task3/
    └── Integration.md
```

---

# Project Overview

The assignment consists of three tasks focused on web development, analytics implementation, conversion optimization, and CRM integration.

---

# Task 1 – GTM Event Schema

Designed a complete Google Tag Manager (GTM) and Google Analytics 4 (GA4) tracking strategy for OrthoNow.

### Deliverables

* Complete GTM Event Schema
* Event Names
* GTM Trigger Types
* Event Parameters
* GA4 Reports / Audiences
* Multi-Step Booking Funnel Tracking
* dataLayer JSON Examples
* Funnel Drop-off Tracking
* Google Ads Conversion Recommendation

---

# Task 2 – Consultation Landing Page

Developed a responsive healthcare landing page using only HTML, CSS, and Vanilla JavaScript.

### Features

* Responsive Design
* Mobile Optimized
* Semantic HTML5
* Embedded CSS
* Vanilla JavaScript
* Two-Field Consultation Form
* Client-side Validation
* Thank You State (Without Page Reload)
* GTM dataLayer Push
* Performance Optimized
* Lighthouse / PageSpeed Screenshot Included

---

# Task 3 – Integration Design

Designed an end-to-end lead management architecture integrating the landing page with HubSpot CRM, Karix WhatsApp Business API, and Google Ads.

### Covered Topics

* End-to-End Architecture
* HubSpot CRM Integration
* Contact Creation & Updates
* Phone Number Deduplication Strategy
* WhatsApp Automation
* Google Ads Conversion Tracking
* Failure Handling Strategy
* SLA Monitoring
* Retry & Recovery Mechanism

---

# Technologies Used

## Frontend

* HTML5
* CSS3
* Vanilla JavaScript

## Analytics

* Google Tag Manager (Conceptual Design)
* Google Analytics 4

## CRM & Marketing

* HubSpot CRM
* Google Ads
* Karix WhatsApp Business API

## Documentation

* Markdown

---

# Form Tracking

On successful form submission, the landing page pushes the following event into the GTM dataLayer:

```javascript
window.dataLayer.push({
    event: "consultation_form_submitted",
    patient_name: name,
    phone_number: phone,
    form_name: "consultation_form",
    page_location: window.location.href
});
```

This event is intended to be captured by Google Tag Manager and forwarded to Google Analytics 4 and Google Ads.

---

# Project Goals

* Improve landing page conversion rate
* Track complete user journey
* Measure booking funnel drop-offs
* Enable accurate Google Ads optimization
* Automate CRM lead capture
* Trigger WhatsApp confirmation messages
* Build a scalable marketing analytics foundation

---

# Assignment Deliverables

| Task                        | Status      |
| --------------------------- | ----------- |
| Task 1 – GTM Event Schema   | ✅ Completed |
| Task 2 – Landing Page       | ✅ Completed |
| Task 3 – Integration Design | ✅ Completed |
| PageSpeed Screenshot        | ✅ Included  |

---

# Notes

* Built entirely with HTML, CSS, and Vanilla JavaScript.
* No external frameworks or UI libraries were used.
* The landing page runs directly in the browser without requiring a server.
* Event tracking is implemented using `window.dataLayer.push()` to simulate production GTM integration.
* Documentation is provided in Markdown format for clarity and version control.

---

# Thank You

Thank you for reviewing my submission. I appreciate the opportunity to complete this assignment and demonstrate my approach to frontend development, analytics implementation, and marketing technology integration.

I look forward to discussing the implementation details during the technical interview.
