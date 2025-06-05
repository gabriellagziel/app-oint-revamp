# R3 — FEATURES AND FLOW

_Last updated: 2025-06-05_

## 🧩 OVERVIEW

This document outlines the full range of core features and application flows within APP-OINT. It ensures all logic is accessible to Codex without relying on external source code or GitHub data.

---

## 🗂️ CORE FEATURES BY USER TYPE

### 👤 Personal Users
- Create and manage appointments
- Receive invitations via SMS, WhatsApp, or app notification
- One-click confirmation or rescheduling
- Notifications and reminders (with optional calendar sync)
- Personal profile and language preferences (28+ supported)
- Limited to 5 full meetings on free plan

### 🏢 Business Users
- Web dashboard for appointment management
- Create services and assign staff
- Set availability calendar per employee or department
- Automated customer communication
- Appointment limits and feature gating for free tier
- Smart Invite with fallback link for non-registered clients

### 🧑‍🎨 Studio / Enterprise Operators
- Cross-location calendar sync
- Staff performance analytics
- Embedded public booking links
- Multi-user team roles
- Usage dashboards and historical client interaction
- Admin override for slot prioritization

### 🛡️ Platform Administrators
- Full analytics: user growth, business conversions, booking volume
- Role and permission management (override and suspension)
- Fraud detection and spam filtering tools
- Enterprise onboarding via API
- Internal access logs, audits, and debug tools

---

## 🔁 UX FLOW HIGHLIGHTS

### Booking Flow (Invitee)
1. Receive invite (via app or link)
2. Review meeting title, time, location
3. Select one-click confirm / propose alternate
4. Confirmation screen and calendar integration option

### Booking Flow (Creator)
1. Create new appointment (title, type, location, time)
2. Add participants (from contacts or manual input)
3. Choose delivery method (in-app, WhatsApp, SMS)
4. Set smart invite behavior and access level
5. Send and track status (accepted / pending)

---

## 🎯 FEATURE GATING

### Free Tier Limits
- 5 meetings per user (personal) or account (business)
- No access to map location selector
- No group meetings or recurring meeting setup
- Smart Invite available only in basic mode

### Premium Unlock
- Unlimited meetings, group sessions, custom branding
- Advanced reminders and Google Calendar sync
- Analytics dashboard for businesses
- Custom fields and service durations
- External embed code for websites

---

## 📍 SYSTEM MODULES (INTERNAL)

- **Smart Invite Dispatcher**: Resolves delivery method per contact
- **Meeting Tracker**: Monitors engagement per invite
- **FeatureFlagService**: Enforces subscription-level feature control
- **AuditLogHandler**: Admin-only event monitor
- **TranslationEngine**: Localizes all user-facing text via 32 languages

---

## ✅ READY TO EXPORT

This document is standalone and ready for direct use within Codex. No GitHub references or source code assumptions exist.
