# Task 1 – GTM Event Schema

**Assignment:** Developer – Position 1 (Client Web + Martech)  
**Client:** OrthoNow

---

# Objective

The objective of this GTM and GA4 implementation is to accurately track user behaviour across the OrthoNow website, measure appointment conversions, identify booking funnel drop-offs, build remarketing audiences, and provide reliable conversion data for Google Ads optimization.

---

# GTM Event Schema

| Event Name | Trigger Type | Key Parameters | GA4 Report / Audience |
|------------|--------------|----------------|-----------------------|
| page_view | Page View | page_title, page_location, page_path | Pages & Screens Report |
| session_start | Automatic | session_id, traffic_source, medium | Acquisition Report |
| clinic_page_view | Page View | clinic_name, city, page_location | Clinic Interest Audience |
| appointment_booking_started | Custom Event | clinic_location, specialty, page_location | Booking Funnel |
| booking_step_complete | Custom Event | step_number, step_name, clinic_location, specialty | Funnel Exploration |
| booking_completed | Custom Event | booking_id, clinic_location, specialty, booking_date | Conversion Report |
| booking_failed | Form Error | step_number, error_type, page_location | Error Analysis |
| booking_abandoned | Exit Intent / Timer | last_completed_step, clinic_location, session_duration | Remarketing Audience |
| consultation_form_started | First Input | page_location, device_type, traffic_source | Form Engagement Report |
| consultation_form_submitted | Form Submit | patient_name, phone_number, page_location | Primary Conversion |
| consultation_form_error | Validation Error | field_name, error_message, page_location | UX Optimization Report |
| call_now_click | Click | phone_number, clinic_name, page_location | Call CTA Performance |
| whatsapp_click | Link Click | clinic_name, device_type, page_location | WhatsApp Audience |
| patient_guide_form_submit | Form Submit | patient_name, phone_number, guide_name | Lead Generation Report |
| patient_guide_download | File Download | pdf_name, clinic_name, page_location | Download Report |
| blog_scroll_25 | Scroll Depth | page_title, scroll_percent, article_category | Content Engagement |
| blog_scroll_50 | Scroll Depth | page_title, scroll_percent, article_category | Content Engagement |
| blog_scroll_75 | Scroll Depth | page_title, scroll_percent, article_category | High Intent Readers |
| blog_scroll_100 | Scroll Depth | page_title, scroll_percent, article_category | Content Completion |
| cta_button_click | Click | button_text, page_location, section_name | CTA Performance |
| outbound_link_click | Link Click | destination_url, page_location, link_text | Referral Analysis |

---

# Booking Funnel Tracking

The OrthoNow appointment booking process consists of three steps:

```
Landing Page
      │
      ▼
Step 1
Select Clinic + Specialty
      │
      ▼
Step 2
Enter Name + Phone + Preferred Date
      │
      ▼
Step 3
Confirm Booking
      │
      ▼
Booking Successful
```

---

# Step 1 – Select Clinic & Specialty

## GTM Trigger

**Trigger Type:** Custom Event

**Event Name**

```text
booking_step_complete
```

## dataLayer Push

```javascript
window.dataLayer.push({
  event: "booking_step_complete",
  step_number: 1,
  step_name: "location_specialty_selected",
  clinic_location: "Bengaluru - Indiranagar",
  specialty: "Orthopaedics"
});
```

---

# Step 2 – Patient Details

## GTM Trigger

**Trigger Type:** Custom Event

**Event Name**

```text
booking_step_complete
```

## dataLayer Push

```javascript
window.dataLayer.push({
  event: "booking_step_complete",
  step_number: 2,
  step_name: "patient_details_entered",
  clinic_location: "Bengaluru - Indiranagar",
  specialty: "Orthopaedics",
  preferred_date: "2026-07-05"
});
```

---

# Step 3 – Booking Confirmation

## GTM Trigger

**Trigger Type:** Custom Event

**Event Name**

```text
booking_step_complete
```

## dataLayer Push

```javascript
window.dataLayer.push({
  event: "booking_step_complete",
  step_number: 3,
  step_name: "booking_confirmed",
  clinic_location: "Bengaluru - Indiranagar",
  specialty: "Orthopaedics",
  booking_status: "confirmed"
});
```

---

# Booking Successfully Completed

## GTM Trigger

**Trigger Type:** Custom Event

**Event Name**

```text
booking_completed
```

## dataLayer Push

```javascript
window.dataLayer.push({
  event: "booking_completed",
  booking_id: "BK458921",
  clinic_location: "Bengaluru - Indiranagar",
  specialty: "Orthopaedics",
  booking_date: "2026-07-05"
});
```

---

# GTM Trigger Configuration

| GTM Trigger | Trigger Type | Fires When |
|-------------|--------------|------------|
| Page View | Page View | Every page load |
| Clinic Page View | Page View | URL contains `/clinics/` |
| Appointment Booking Started | Custom Event | `appointment_booking_started` |
| Booking Step Complete | Custom Event | `booking_step_complete` |
| Booking Completed | Custom Event | `booking_completed` |
| Consultation Form Started | Element Visibility / First Input | User starts typing in the consultation form |
| Consultation Form Submitted | Form Submission | Form submitted successfully |
| Call Now Click | Click | User clicks any `tel:` link |
| WhatsApp Click | Click | User clicks any `wa.me` link |
| Patient Guide Form Submit | Form Submission | User submits guide download form |
| Patient Guide Download | Link Click | PDF successfully downloaded |
| Blog Scroll | Scroll Depth | 25%, 50%, 75%, and 100% scroll |
| CTA Button Click | Click | Any primary CTA button is clicked |
| Outbound Link Click | Link Click | User clicks an external website |

---

# GA4 Funnel Exploration

A Funnel Exploration should be configured in GA4 using the following sequence of events:

| Funnel Step | Event |
|-------------|-------|
| Landing Page Visit | `page_view` |
| Booking Started | `appointment_booking_started` |
| Step 1 Completed | `booking_step_complete` (step_number = 1) |
| Step 2 Completed | `booking_step_complete` (step_number = 2) |
| Step 3 Completed | `booking_step_complete` (step_number = 3) |
| Booking Completed | `booking_completed` |

This funnel allows marketers to identify the exact stage where users abandon the booking process and optimize the user experience accordingly.

---

# Example Funnel Drop-off

| Funnel Stage | Users | Conversion Rate | Drop-off |
|--------------|------:|----------------:|----------:|
| Landing Page Visit | 1000 | 100% | - |
| Booking Started | 720 | 72% | 28% |
| Step 1 Completed | 610 | 61% | 15.3% |
| Step 2 Completed | 470 | 47% | 22.9% |
| Step 3 Completed | 390 | 39% | 17.0% |
| Booking Completed | 360 | 36% | 7.7% |

From this report, the largest drop-off occurs between Step 1 and Step 2, indicating that the patient details form may require simplification or UX improvements.

---

# Google Ads Conversion Recommendation

## Selected Conversion

```
consultation_form_submitted
```

## Justification

I would import the **consultation_form_submitted** event into Google Ads as the primary conversion.

This event represents the main lead generation goal of the consultation landing page and occurs before appointment confirmation, allowing Google Ads Smart Bidding to receive a higher volume of conversion signals. More conversion data helps Google's machine learning optimize campaigns more effectively while still targeting users with strong purchase intent. Since the marketing campaign is designed to generate consultation enquiries, this event best aligns with the business objective.

---

# Implementation Notes

The `window.dataLayer.push()` statements shown above **must be implemented by the front-end developer** at the point where each booking step is successfully completed.

Google Tag Manager **does not automatically detect progress within a custom multi-step form**. Instead, GTM listens for the custom events pushed into the `dataLayer` and then triggers the appropriate GA4 tags based on those events.

This implementation provides:

- Complete booking funnel visibility
- Accurate conversion tracking
- Remarketing audience creation
- Google Ads optimization
- Detailed user behaviour analysis
- Actionable insights for UX improvements