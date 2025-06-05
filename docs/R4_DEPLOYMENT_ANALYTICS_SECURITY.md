# R4 — DEPLOYMENT, ANALYTICS & SECURITY  
_Last updated: 2025-06-05_

---

## 📦 Deployment Targets

### Web (Primary)
- **Hosting**: Firebase Hosting
- **Entry Point**: `web/index.html`
- **Build Command**: `flutter build web`
- **Deployment Flow**:
  1. CI build on push to `main` or `release/*`
  2. Deploy to Firebase Hosting via GitHub Actions
- **Routing**: Flutter web routing (Path-based)
- **Limitations**: Invitees who are not logged in access limited WebView interface

### Mobile (Secondary)
- **Framework**: Flutter
- **Platforms**: iOS & Android
- **Distribution**:
  - **Internal Testing**: Firebase App Distribution
  - **Public**: App Store & Google Play (via CI/CD)

---

## 📊 Analytics & Tracking

### Firebase Analytics
- Events tracked:
  - `appointment_created`
  - `appointment_joined`
  - `app_open`
  - `meeting_completed`
  - `premium_upgrade`
- User Properties:
  - `user_role` (personal/business/admin/studio)
  - `locale`
  - `subscription_status`

### Session Monitoring
- **Timeouts**:
  - Personal: 30 minutes inactivity
  - Business: 4 hours
  - Admins: 8 hours or manual logout
- **Activity Logging**:
  - Login/logout timestamps
  - Role-based action logs
  - Invite status (sent, opened, accepted)

---

## 🔐 Security Model

### Authentication
- **Provider**: Firebase Auth
- **Methods**:
  - Email + Password
  - Phone OTP (Twilio fallback)
  - Google Sign-In

### Authorization
- Handled via `R1.md` role matrix
- Middleware-based route guards
- Cloud Function rules for:
  - Preventing unauthorized reads/writes
  - Rate limiting sensitive actions (e.g., mass-invite)

### Firestore Rules
```js
match /users/{userId} {
  allow read, write: if request.auth.uid == userId;
}

match /appointments/{docId} {
  allow read: if isParticipantOrOwner(docId);
  allow write: if isOwner(docId);
}
```

Cloud Functions
• Admin-triggered CRON jobs (e.g., daily invite cleanup)
• Payment webhook validation (Stripe/Firebase)
• Abuse prevention: auto-block if >X meetings/hour

⸻

🔍 QA & Testing

Environments
• dev: feature previews, Flutter dev channel
• staging: pre-prod, Flutter stable channel
• prod: production deployment

Flags
• isTestEnv (bool) — toggles fake API & test Stripe key
• featurePreviewEnabled — for early access group

⸻

🔄 CI/CD Integration

GitHub Actions
• Auto build on PRs
• Linting + formatting check
• Unit + widget tests (flutter test)
• Deployment matrix:
• web: Firebase CLI
• mobile: Internal Testing tracks via Firebase

⸻

🛡️ Admin Audit Controls
• Role-based logs view
• Manual session revocation (admins only)
• Export activity to BigQuery (daily CRON)
