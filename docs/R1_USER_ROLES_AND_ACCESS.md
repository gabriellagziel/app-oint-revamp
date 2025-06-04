# R1 — USER ROLES AND ACCESS

## 🎭 USER TYPES

APP-OINT supports four distinct user roles, each with specific permissions and UX flows:

### 1. Personal User
- **Platform**: Mobile app only
- **Target Audience**: Individuals using APP-OINT for personal scheduling
- **Permissions**:
  - Create and manage 1:1 meetings
  - Receive invites via phone number, app notification, or SMS
  - View limited dashboard of past/upcoming meetings
  - Upgrade to business plan from within app

### 2. Business User
- **Platform**: Web Dashboard (with optional mobile preview)
- **Target Audience**: Professionals, studios, service providers
- **Permissions**:
  - Create/manage calendar availability (weekly schedule)
  - Offer appointment slots with link-based sharing
  - Accept/decline bookings from external users (clients)
  - Customize appointment types, durations, meeting colors
  - Set up auto-confirmation or manual approval
  - View analytics and client list
  - Assign meeting-specific rules: payment, location, etc.

### 3. Studio/Organization Admin (Business Plus)
- **Platform**: Web Dashboard
- **Target Audience**: Businesses with multiple staff members
- **Permissions**:
  - Everything Business User can do, plus:
  - Add/manage team members (with permissions)
  - Assign services per staff member
  - Manage team calendar (combined view)
  - Route clients to appropriate team member
  - Access role-based usage analytics

### 4. Platform Administrator (System Owner)
- **Platform**: Admin Panel (internal use)
- **Target Audience**: APP-OINT system owners
- **Permissions**:
  - View system-wide analytics
  - Monitor financial reports & subscription usage
  - Manage users and freeze/ban accounts
  - Push platform-wide announcements
  - Modify pricing plans and feature access logic
  - Review flagged content or abuse reports

---

## 🔐 ACCESS LOGIC

### Shared by All Roles
- Login via phone number (OTP)
- Language selector (supports 32 languages)
- GDPR/CCPA-compliant consent on first use
- Session timeout logic based on role (admin longest)

### Meeting Access Rules
- Free users:
  - Limited to 5 full-featured meetings
  - Post-limit: restricted access (e.g. no maps, no multi-participant)
- Paid users:
  - Unlimited meetings
  - Full access to maps, calendar sync, and group features

### Invite Handling
- If invitee has the app: opens in-app
- If not:
  - Opens a web mini-version with RSVP capability
  - Prompts to download app for full scheduling access

---

## 📊 ADMIN INSIGHT & CONTROL

- Admin can track:
  - Active users by role
  - Subscription conversion rate
  - Most used features per segment
- Admin can impersonate a user (read-only) for support
- Admin audit logs every action taken from panel

---

## 🛡 SECURITY AND PERMISSIONS

- OTP login with rate limits and expiration logic
- All user roles scoped via Firebase Auth + Firestore rules
- Role-based access enforced both client- and server-side
- Admin-only APIs are firewalled from frontend clients
- Firebase Functions validate all mutations

---

## 🌐 MULTILINGUAL SUPPORT

- All users access a multilingual interface with auto-detection
- Currently supports 32 languages including EN, FR, ES, HE, RU, ZH, AR, HI, JA, DE, IT, PT, etc.

---

_Last updated: 2025-06-05_
