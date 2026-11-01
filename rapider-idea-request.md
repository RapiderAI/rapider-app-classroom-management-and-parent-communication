<!-- Rapider Official App SOW & Specification | App #163: Classroom Management & Parent Communication (classroom-management-and-parent-communication) | Domain: EDU -->

# #163 Classroom Management & Parent Communication (`classroom-management-and-parent-communication`) — Scope of Work (SOW)

- **App Number & Name:** `#163` — Classroom Management & Parent Communication
- **Proposed App Key:** `classroom-management-and-parent-communication`
- **Suite / Domain Key & Model Prefix:** `EDU` (`Edu*`)
- **Representative Product (`P1`):** ClassDojo
- **Combined Feature Catalog:** [../combined-features/163-classroom-management-and-parent-communication-features.md](../combined-features/163-classroom-management-and-parent-communication-features.md)
- **Target Release Posture:** PBIS Classroom Culture, Multimodal Student Portfolios, Auto-Translated School-Home Messaging, Permission Slips & Conference Booking Microapplication

---

## 1. Executive Outcome & Target Audience

### 1.1 Business Problem Solved
Schools and academies routinely fragment daily classroom engagement across five or more disconnected consumer tools: one app for PBIS behavior points, another for student portfolios, unlogged WhatsApp/personal SMS threads for parent questions, paper permission slips lost in backpacks, and spreadsheet sign-ups for parent-teacher conferences. This fragmentation creates severe child-safety blind spots, burns out teachers with late-night parent texts, leaves non-English-speaking households unreached, and risks violating FERPA or court-ordered custody blocks. **Rapider Classroom Management & Parent Communication (`classroom-management-and-parent-communication`)** unifies positive classroom culture, moderated student portfolios, two-way 100+ language masked messaging, digital permission slips, and conference scheduling directly atop `#161 Student Information System (SIS)`.

### 1.2 Target Personas & Progressive Disclosure
- **SME Fast-Path Defaults (Elementary/Secondary Teachers, Preschools, Enrichment Academies):** Open any `#161` `EduCourseSection` roster and immediately award 1-tap PBIS praise points, post a Class Story photo update, approve student portfolio submissions, send auto-translated messages with default 5:30 PM Quiet Hours, and publish 15-minute conference slots in under three minutes.
- **Enterprise Progressive Disclosure (K-12 School Districts, Principals, Family Engagement & Compliance Directors):** Unlock campus/district omnichannel broadcasts (App + `MKT` Email/SMS) with read-receipt tracking, unreached-household radars, urgent weather/safety Quiet-Hour overrides via Home `WorkItem` governance, field-trip fee handoffs to `FIN` (`FinInvoice`), and FOIA-compliant immutable message archives with safety keyword flagging.

### 1.3 Measurable Business Outcomes
- **>= 95% Reachable Multilingual Households:** Automatic home-language translation and omnichannel SMS/email fallback reach families regardless of smartphone app installation or primary language.
- **Zero Personal Phone Exposure & 100% Custody Compliance:** Masked relays and hard server-side checks against `EduGuardianLink.nonContactRestriction` and `ferpaDirectoryOptOut` prevent unauthorized disclosures.
- **80% Reduction in Paper Permission Slip & Conference Admin Overhead:** Targeted non-responder reminders, digital consent signatures, and automated slot booking eliminate manual chasing.

### 1.4 Benchmark Summary (`P1`–`P6`)
Synthesizes the positive PBIS culture, Class/School Stories, Quiet Hours, and 190+ language translation of **`P1` ClassDojo**, the district-wide omnichannel alerts, permission slips, and conference/volunteer sign-ups of **`P2` ParentSquare**, the multimodal student-driven portfolios and pre-publish teacher moderation of **`P3` Seesaw**, the number-masked secondary SMS and FOIA compliance archiving of **`P4` Remind**, the SEL *Reflect* check-ins and weekly Guardian Digests of **`P5` Microsoft Education**, and the Household 360 engagement and grounded AI summaries of **`P6` Salesforce Education Cloud**.

---

## 2. In-Scope, Out-of-Scope & Suite Ownership Boundaries

### 2.1 In-Scope Capabilities
1. Configurable PBIS behavior/character rubrics (`EduBehaviorRubric`), 1-tap individual/group/class feedback & SEL pulse check-ins (`EduBehaviorEvent`), and live classroom projection tools (random picker, timer, group builder).
2. Student multimodal digital portfolios (`EduPortfolioArtifact`) tagged to `LrnSkillDefinition` competencies and governed by a `<rapider-kanban>` teacher moderation queue (`DRAFT` -> `PUBLISHED_TO_FAMILY`).
3. Class & campus stories/announcements (`EduClassroomBroadcast`) with per-household read receipts, automatic language translation, and unreached-household analytics.
4. Privacy-masked two-way educator-guardian threads (backed by `projectChannelMessage`), Quiet Hours enforcement, and immutable district communication compliance policies (`EduCommPolicy`).
5. Digital permission slips & volunteer/supply sign-ups (`EduPermissionSlip`, `EduGuardianSlipResponse`) with optional `FIN` fee handoffs, plus parent-teacher conference time-slot booking (`EduConferenceSlot`).

### 2.2 Out-of-Scope Capabilities (Delegated to Adjacent Rapider Apps)
- **Authoritative student demographics, custodial household definitions, official daily/period attendance ledgers, academic gradebooks, and transcripts:** Owned by `#161 Student Information System (SIS)` (`student-information-system-sis`).
- **Structured online courses, SCORM/video modules, quizzes, and high-stakes proctored exams:** Owned by `LRN` (`online-learning`, `content-studio`) and `#164 Online Examination & Assessment`.
- **Bulk marketing acquisition funnels for prospective non-enrolled families:** Owned by `#168 Education Admissions & Enrollment Management` and `MKT` (`campaigns`).
- **Payment card vaulting, invoicing ledgers, and accounting:** Owned by `FIN` (`billing`, `payments`, `acc`).

### 2.3 Cross-Suite Ownership & Integration Contract

| Domain / App | Owns (Canonical Models) | Integration Contract with `classroom-management-and-parent-communication` |
| :--- | :--- | :--- |
| **`classroom-management-and-parent-communication` (`#163` — This App)** | `EduBehaviorRubric`, `EduBehaviorEvent`, `EduPortfolioArtifact`, `EduClassroomBroadcast`, `EduPermissionSlip`, `EduGuardianSlipResponse`, `EduConferenceSlot`, `EduCommPolicy` | Manages daily classroom PBIS/SEL culture, moderated student portfolios, school-home feeds/messaging, permission slips, and conference bookings. |
| **`#161 Student Information System` (`EDU`)** | `EduStudentProfile`, `EduGuardianLink`, `EduCourseSection`, `EduSectionEnrollment`, `EduAttendanceRecord`, `EduSuccessCase` | `#163` reads rosters, guardian languages, `nonContactRestriction` & `ferpaDirectoryOptOut`; consumes `edu.attendance.unexcusedRecorded.v1` for truancy outreach; escalates severe behavioral incidents into `EduSuccessCase`. |
| **`LRN` Suite (`learning-experience-skills`, `online-learning`)** | `LrnSkillDefinition`, `LrnCourse` | `EduPortfolioArtifact` and `EduBehaviorRubric` link to canonical `LrnSkillDefinition.id` and `LrnCourse.id` for standards-aligned conference portfolios. |
| **`MKT` Suite (`email`, `sms`)** | `MktEmailMessage`, `MktSmsMessage` | Executes outbound email/SMS transport and masked inbound SMS webhook relay for guardians without mobile app sessions. |
| **`FIN` Suite (`billing`, `payments`)** | `FinInvoice`, `FinPaymentIntent` | Paid field-trip/activity `EduPermissionSlip` responses create canonical `FinInvoice` / `FinPaymentIntent` checkouts (`Decimal128`) and listen for `fin.payment.succeeded.v1`. |
| **`HR` Suite (`employees`)** | `HrEmployee`, `HrLocation` | Teachers, co-teachers, coaches, and campus principals reference canonical `HrEmployee.id` and `HrLocation.id`. |
| **Rapider Platform Services** | Identity/RBAC, Files/Drive, `projectChannelMessage`, Home `WorkItem` | Stores portfolio media in Files/Drive, hosts 2-way guardian threads in `projectChannelMessage`, and routes urgent broadcast approvals, fee waivers & safety flags via Home `WorkItem`s. |

---

## 3. Primary Web Pages & Sidebar Navigation Architecture (13 Pages)

Every visible sidebar section strictly enforces the **Minimum 3 Items Rule (`>= 3` items with `displayOnMenu: true`)**: `Classroom` (3 items), `Family Engagement` (3 items), and `Governance` (3 items) = 9 visible items + 4 hidden detail/drawer routes (`displayOnMenu: false`).

| # | Route | Page Title | Sidebar Section | Menu Visible | Key Components & UX |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | `classroom-pulse` | Classroom & PBIS Live | `Classroom` | `true` (Order 1) | Section selector (`findSWR`), 1-tap PBIS student/group tile grid (`EduBehaviorEvent`), SEL check-in summary, and projection toolkit (Randomizer, Timer, Group Maker). |
| 2 | `portfolio-moderation` | Student Portfolios | `Classroom` | `true` (Order 2) | `<rapider-kanban>` teacher moderation board (`DRAFT` -> `SUBMITTED_FOR_REVIEW` -> `NEEDS_REVISION` -> `PUBLISHED_TO_FAMILY`) + list toggle, `#activeFilterTagsBar` (Section, Skill, Status), FERPA photo warning badges. |
| 3 | `behavior-ledger` | Behavior & SEL History | `Classroom` | `true` (Order 3) | Searchable `EduBehaviorEvent` log with `#activeFilterTagsBar`, positive-to-coaching ratio KPIs, clickable Student Name -> `student-engagement-detail`, icon+text Edit, icon-only Delete, and Escalate to Counselor action. |
| 4 | `stories-broadcasts` | Class & School Stories | `Family Engagement` | `true` (Order 1) | Rich feed & `EduClassroomBroadcast` table showing scope (Class, Grade, Campus), auto-translation badge, read-receipt % (`countSWR`), and New Broadcast drawer trigger. |
| 5 | `family-messages` | Two-Way Family Inbox | `Family Engagement` | `true` (Order 2) | Masked educator-guardian `projectChannelMessage` hub with Quiet Hours status banner, instant language translation toggle, `<rapider-phone-input>` SMS reach preview, and AI Tone Coach. |
| 6 | `slips-conferences` | Slips, Sign-Ups & Conferences | `Family Engagement` | `true` (Order 3) | Unified manager for `EduPermissionSlip` consent campaigns (with non-responder nudge button and `FIN` fee badge) and `EduConferenceSlot` schedule blocks. |
| 7 | `engagement-analytics` | Walk-the-Halls Analytics | `Governance` | `true` (Order 1) | Principal/District dashboard tracking campus PBIS ratios, weekly story reach %, permission-slip completion, and Unreached Households radar (`CMP-022`). |
| 8 | `rubrics-templates` | PBIS Rubrics & Templates | `Governance` | `true` (Order 2) | Manage `EduBehaviorRubric` skill sets (Elementary vs. Secondary display modes) and reusable permission-slip/newsletter templates. |
| 9 | `comm-safety-policies` | Quiet Hours & Safety Audit | `Governance` | `true` (Order 3) | Configure `EduCommPolicy` Quiet Hours, urgent broadcast override rules, custody/FERPA pre-flight rules, and FOIA/safety message audit exports. |
| 10 | `student-engagement-detail` | Student Portfolio & Family View | *(Hidden)* | `false` | Holistic classroom view (`#/student-engagement-detail?id=...`) showing approved `EduPortfolioArtifact` showcase, PBIS/SEL timeline, guardian reachability status, AI conference talking points, and `Back to list`. |
| 11 | `permission-slip-detail` | Permission Slip & Sign-Up Roster | *(Hidden)* | `false` | Detailed `EduPermissionSlip` tracker (`#/permission-slip-detail?id=...`) listing per-student `EduGuardianSlipResponse` status, digital signatures, volunteer slots, `FinInvoice` payment status, and 1-click "Remind Pending". |
| 12 | `broadcast-slip-drawer` | Publish Story / Permission Slip | *(Hidden)* | `false` | Sliding drawer to compose `EduClassroomBroadcast` or `EduPermissionSlip` with FERPA photo check, AI *Sidekick* draft helper, `Decimal128` trip fee field, `finally` button reset, and `closePageDrawer()`. |
| 13 | `portfolio-conference-drawer` | Submit Artifact / Conference Block | *(Hidden)* | `false` | Sliding drawer to upload/review `EduPortfolioArtifact` (`LrnSkillDefinition` tags) or generate `EduConferenceSlot` blocks with `closePageDrawer()`. |

**Mandatory Rapider UI Standards Enforced Across All 13 Pages:**
- **SWR & Soft-Delete Hygiene:** Initial loads exclusively call `window.rapiderApi.findSWR` / `countSWR` without redundant `isDeleted` filter clauses and filter `item.isDeleted !== true` in memory.
- **Table Actions & Navigation:** Zero standalone "View" buttons in `Actions`; clicking primary identifiers (Student Name, Slip Title, Broadcast Subject) navigates to detail routes; Edit buttons use icon + text; Delete buttons use icon-only with `title="Delete"` and `aria-label="Delete"`.
- **Contrast & Dialog Ban:** All primary and danger buttons enforce `#ffffff !important` white text; native `alert`/`confirm`/`prompt` are strictly banned.

---

## 4. Canonical Data Models (`Edu*` — 8 Models)

All models use platform-generated UUID `id` (`00000000-xxxx-xxxx-xxxx-xxxxxxxxxxxx` in sample seeds), omit `projectId`, enforce optimistic `version`, and store all monetary trip fees and weighted PBIS scores as `Decimal128`.

| Model Name | Key Fields & Types | Relationships & External Refs | Invariants & Lifecycle |
| :--- | :--- | :--- | :--- |
| **`EduBehaviorRubric`** | `id` (UUID), `name` (string), `ageMode` (`ELEMENTARY_ICONS`, `SECONDARY_BADGES`), `category` (`POSITIVE_PRAISE`, `COACHING_NEEDS_WORK`), `defaultPoints` (`Decimal128`), `iconKey` (string), `shareWithGuardiansDefault` (boolean), `status` (`ACTIVE`, `ARCHIVED`), `version` (int) | `campusLocationId` -> `HrLocation.id`, `lrnSkillId` -> `LrnSkillDefinition.id` (optional) | Schoolwide rubrics cannot be deleted while referenced by active term `EduBehaviorEvent` rows (archive only). |
| **`EduBehaviorEvent`** | `id` (UUID), `eventType` (`PBIS_POINT`, `SEL_CHECKIN`, `INCIDENT_REFERRAL`), `pointsAwarded` (`Decimal128`), `selMoodCode` (`ENERGIZED`, `CALM`, `TIRED`, `FRUSTRATED`, `ANXIOUS`), `note` (string), `visibleToGuardian` (boolean), `occurredAt` (Date), `escalatedSuccessCaseId` (UUID), `version` (int) | `studentId` -> `EduStudentProfile.id`, `sectionId` -> `EduCourseSection.id`, `rubricId` -> `EduBehaviorRubric.id`, `recordedByEmployeeId` -> `HrEmployee.id` | `SEL_CHECKIN` events default `visibleToGuardian = false` unless explicitly shared during counselor review; never publicly visible to peers. |
| **`EduPortfolioArtifact`** | `id` (UUID), `title` (string), `mediaType` (`IMAGE`, `VIDEO`, `AUDIO`, `DOCUMENT`, `JOURNAL_TEXT`), `driveFileId` (string), `studentReflection` (string), `teacherFeedback` (string), `moderationStage` (`DRAFT`, `SUBMITTED_FOR_REVIEW`, `NEEDS_REVISION`, `PUBLISHED_TO_FAMILY`), `ferpaCleared` (boolean), `publishedAt` (Date), `version` (int) | `studentId` -> `EduStudentProfile.id`, `sectionId` -> `EduCourseSection.id`, `skillIds` -> `LrnSkillDefinition.id[]`, `moderatedByEmployeeId` -> `HrEmployee.id` | Guardians can ONLY query artifacts where `moderationStage = PUBLISHED_TO_FAMILY` and `studentId` matches an active custodial `EduGuardianLink`. |
| **`EduClassroomBroadcast`** | `id` (UUID), `title` (string), `bodyMarkdown` (string), `scopeType` (`SECTION`, `GRADE_LEVEL`, `CAMPUS`, `DISTRICT`), `urgencyLevel` (`STANDARD`, `IMPORTANT`, `URGENT_SAFETY`), `channels` (string[]: `IN_APP`, `EMAIL`, `SMS`), `autoTranslateEnabled` (boolean), `scheduledFor` (Date), `publishedAt` (Date), `recipientHouseholdCount` (int), `readHouseholdCount` (int), `status` (`DRAFT`, `PENDING_URGENT_APPROVAL`, `SCHEDULED`, `PUBLISHED`), `version` (int) | `sectionId` -> `EduCourseSection.id`, `campusLocationId` -> `HrLocation.id`, `authorEmployeeId` -> `HrEmployee.id` | `URGENT_SAFETY` broadcasts require `CAMPUS_ADMIN` privilege or an approved Home `WorkItem` before bypassing Quiet Hours. |
| **`EduPermissionSlip`** | `id` (UUID), `title` (string), `slipType` (`FIELD_TRIP`, `MEDIA_CONSENT`, `POLICY_ACK`, `VOLUNTEER_SIGNUP`), `descriptionMarkdown` (string), `eventDate` (Date), `dueDate` (Date), `requiresFee` (boolean), `feeAmount` (`Decimal128`), `currency` (string), `allowFeeWaiverRequest` (boolean), `volunteerSlotsJson` (JSON array), `status` (`DRAFT`, `OPEN`, `CLOSED`), `version` (int) | `sectionId` -> `EduCourseSection.id`, `campusLocationId` -> `HrLocation.id`, `createdByEmployeeId` -> `HrEmployee.id` | If `requiresFee = false`, `feeAmount` MUST equal `0.00` (`Decimal128`). |
| **`EduGuardianSlipResponse`** | `id` (UUID), `decision` (`PENDING`, `APPROVED`, `DECLINED`), `signedFullName` (string), `signedAt` (Date), `emergencyPhoneE164` (string), `selectedVolunteerSlotKey` (string), `feeWaiverRequested` (boolean), `paymentStatus` (`NOT_REQUIRED`, `INVOICED`, `PAID`, `WAIVED`), `version` (int) | `permissionSlipId` -> `EduPermissionSlip.id`, `studentId` -> `EduStudentProfile.id`, `guardianLinkId` -> `EduGuardianLink.id`, `finInvoiceId` -> `FinInvoice.id` | Only an `EduGuardianLink` with `hasCustody = true` and `nonContactRestriction = false` can submit `APPROVED`/`DECLINED`; signed responses lock `signedFullName`/`signedAt` immutably. |
| **`EduConferenceSlot`** | `id` (UUID), `startAt` (Date), `endAt` (Date), `meetingMode` (`IN_PERSON`, `VIDEO_LINK`, `PHONE`), `locationOrRoom` (string), `status` (`AVAILABLE`, `BOOKED`, `COMPLETED`, `CANCELLED`), `interpreterLanguageCode` (string), `version` (int) | `hostEmployeeId` -> `HrEmployee.id`, `sectionId` -> `EduCourseSection.id`, `bookedStudentId` -> `EduStudentProfile.id`, `bookedGuardianLinkId` -> `EduGuardianLink.id` | Atomic optimistic concurrency (`version`) prevents two guardians from booking the same `AVAILABLE` slot simultaneously. |
| **`EduCommPolicy`** | `id` (UUID), `policyName` (string), `quietHoursStartLocal` (string, e.g., `17:30`), `quietHoursEndLocal` (string, e.g., `07:30`), `quietWeekendsEnabled` (boolean), `allowStudentDirectChatGrades6To12` (boolean), `safetyKeywordPatterns` (string[]), `archiveRetentionYears` (int), `version` (int) | `campusLocationId` -> `HrLocation.id` | Applies deterministically across all two-way `projectChannelMessage` relays and `MKT` SMS/email dispatches; audit logs are append-only. |

---

## 5. Core End-to-End User Journeys

### 5.1 Journey 1: SME Teacher Fast-Path — PBIS Praise, Moderated Portfolio & Translated Class Story
1. Teacher opens `classroom-pulse`, selects `Grade 4 Homeroom` (`EduCourseSection` synced from `#161`), and taps **Teamwork (+1)** for Table Group B—instantly creating `EduBehaviorEvent` records.
2. During science lab, students upload project photos as `EduPortfolioArtifact` items (`SUBMITTED_FOR_REVIEW`); Teacher opens `portfolio-moderation` (`<rapider-kanban>`), tags `LrnSkillDefinition` *"Scientific Inquiry"*, and drags three items to `PUBLISHED_TO_FAMILY`.
3. Teacher opens `broadcast-slip-drawer`, clicks **AI Sidekick Draft** (`CMP-025`) to summarize the week's science highlights, and publishes a `SECTION` `EduClassroomBroadcast`. Spanish-, Arabic-, and Mandarin-speaking `EduGuardianLink` households automatically receive the update in their home language while a restricted non-custodial contact (`nonContactRestriction = true`) receives zero payload.

### 5.2 Journey 2: Digital Field-Trip Permission Slip + `FIN` Fee Payment / Waiver
1. Teacher creates a `FIELD_TRIP` `EduPermissionSlip` (*"Natural History Museum — May 14"*) with `feeAmount = \$25.00` (`Decimal128`), `allowFeeWaiverRequest = true`, and 3 chaperone volunteer slots.
2. `#163` generates `PENDING` `EduGuardianSlipResponse` rows for every enrolled student in the section.
3. Custodial Parent A signs digitally (`APPROVED`), verifies `<rapider-phone-input>` emergency phone, claims 1 chaperone slot, and triggers a canonical `\$25.00` `FinInvoice` / `FinPaymentIntent` in `FIN`; Custodial Parent B signs and checks `feeWaiverRequested = true`, routing a discreet Home `WorkItem` to the Principal (`WAIVED` on approval).
4. Two days before `dueDate`, Teacher opens `permission-slip-detail` and clicks **Remind Pending (4)**—nudging only the 4 households still in `PENDING`.

### 5.3 Journey 3: Quiet Hours Two-Way Masked Chat & Safety Keyword Escalation
1. At 8:45 PM, a parent replies via SMS in Vietnamese asking about homework. `#163` ingests the masked SMS via `MKT`, appends both original Vietnamese and English translation to the `projectChannelMessage` thread, and holds teacher push notification until `07:30` per `EduCommPolicy` Quiet Hours.
2. In a separate supervised Grade 10 educator-student channel, a message matches a self-harm/bullying `safetyKeywordPatterns` rule; `#163` immediately generates a high-priority Rapider Home `WorkItem` for the Campus Counselor/Principal and links an `EduSuccessCase` in `#161`.

### 5.4 Journey 4: Parent-Teacher Conference Slot Booking with Interpreter Coordination
1. Teacher opens `portfolio-conference-drawer` and generates sixteen 15-minute `EduConferenceSlot` blocks with 5-minute buffers for Thursday evening.
2. Guardians book available slots; one household selects `interpreterLanguageCode = "es"`, alerting the campus coordinator. Before the meeting, Teacher opens `#/student-engagement-detail?id=...` to review the grounded AI Conference Talking Points (`CMP-028`).

### 5.5 Journey 5: Automated Unexcused Absence Outreach <-> `#161 SIS`
1. `#161 SIS` emits `edu.attendance.unexcusedRecorded.v1` at 9:15 AM when a student misses Period 1.
2. `#163` immediately dispatches a translated SMS/in-app notice to authorized custodial guardians; the parent replies with a doctor-visit excuse, which `#163` relays back to `#161` for front-office attendance verification.

### 5.6 Journey 6: Click-Through Navigation & `#activeFilterTagsBar` State Restoration
1. Principal opens `behavior-ledger`, types `"Rivera"`, and selects `Event: "PBIS_POINT"`—rendering dismissible chips in `#activeFilterTagsBar`.
2. Principal clicks **Sofia Rivera**, smoothly navigating to `#/student-engagement-detail?id=...` without `<base href>` 404 diversion, inspects approved portfolio work, and clicks **Back to list** to return to the exact filtered table.

---

## 6. Consolidated Feature Priorities & Work Packages

### `P0` Foundation Work Packages (Must-Have Core Release)
- **WP-P0-1 — PBIS Classroom Culture & Moderation Portfolios (`CMP-001`, `CMP-002`, `CMP-006`, `CMP-007`):** Deliver `EduBehaviorRubric`, `EduBehaviorEvent`, `classroom-pulse`, `behavior-ledger`, and `EduPortfolioArtifact` `<rapider-kanban>` teacher moderation queue.
- **WP-P0-2 — Auto-Translated Stories, Masked Two-Way Chat & Quiet Hours (`CMP-010`, `CMP-011`, `CMP-012`, `CMP-013`, `CMP-014`):** Deliver `EduClassroomBroadcast`, `MKT` email/SMS delivery + read receipts, `projectChannelMessage` two-way masked threads with `<rapider-phone-input>`, 100+ language translation, and `EduCommPolicy` Quiet Hours.
- **WP-P0-3 — Permission Slips, Conference Slots & Custody/FERPA Gates (`CMP-017`, `CMP-018`, `CMP-021`):** Build `EduPermissionSlip`, `EduGuardianSlipResponse`, `EduConferenceSlot` atomic booking, and hard server-side enforcement of `#161` `nonContactRestriction` and `ferpaDirectoryOptOut`.

### `P1` Enterprise Scale Work Packages
- **WP-P1-1 — SEL Check-Ins, Portfolio Skills, Urgent Alerts & Truancy Sync (`CMP-003`, `CMP-004`, `CMP-008`, `CMP-009`, `CMP-015`, `CMP-016`):** Add SEL *Reflect* check-ins, `#161` `EduSuccessCase` escalations, `LrnSkillDefinition` portfolio tagging, family encouragement comments, urgent Quiet-Hour override `WorkItem`s, and `#161` unexcused-absence outreach.
- **WP-P1-2 — Volunteer Sign-Ups, `FIN` Trip Fees, Unreached Radar & FOIA Audit (`CMP-019`, `CMP-020`, `CMP-022`, `CMP-023`, `CMP-024`):** Add volunteer/supply slot quotas, `FinInvoice` field-trip fee/waiver integration, unreached-household analytics, Walk-the-Halls KPIs, and immutable FOIA/safety keyword monitoring.

### `P2` Adjacent & Grounded AI Work Packages
- **WP-P2-1 — Classroom Toolkit, Weekly Digests & Grounded Educator AI (`CMP-005`, `CMP-025`, `CMP-026`, `CMP-027`, `CMP-028`):** Deliver live classroom randomizer/timer/group tools, AI *Sidekick* newsletter drafting, AI reading-level/tone coaching, automated Friday Guardian Digests, and grounded AI conference talking points.

---

## 7. Roles, Permissions & Field-Level Governance

| Role | Permitted Actions | Restricted / Field-Level Boundaries |
| :--- | :--- | :--- |
| **Student** | Submit `EduPortfolioArtifact` drafts, complete private SEL check-ins, view own PBIS points, and (Grades 6–12 only when enabled by `EduCommPolicy`) message assigned teachers in supervised channels. | Cannot view peers' private behavior/SEL logs, publish unmoderated portfolio items to families, or initiate private unsupervised DMs. |
| **Custodial Guardian (`EduGuardianLink`)** | View own child's `PUBLISHED_TO_FAMILY` portfolio items, shared PBIS summaries, Class/School Stories, reply in masked translated threads, sign `EduPermissionSlip`s, and book `EduConferenceSlot`s. | Zero access if `nonContactRestriction = true` or `hasCustody = false`; never sees personal educator phone numbers or other students' private records. |
| **Teacher / Co-Teacher (`HrEmployee`)** | Award PBIS points, moderate `EduPortfolioArtifact`s, publish `SECTION` stories/permission slips, host `EduConferenceSlot`s, and message assigned section guardians within `EduCommPolicy` rules. | Cannot send `URGENT_SAFETY` campus/district broadcasts without approval, delete archived `projectChannelMessage` audit logs, or override `nonContactRestriction` blocks. |
| **Counselor / Dean of Students** | Review SEL trend alerts, escalated `EduBehaviorEvent` referrals, and safety-keyword `WorkItem`s; coordinate interpreter support for conferences. | Cannot modify `FIN` payment ledgers or alter immutable guardian e-signatures on `EduGuardianSlipResponse`. |
| **Principal / District Comms Admin** | Publish `CAMPUS`/`DISTRICT` broadcasts, approve `URGENT_SAFETY` overrides and fee-waiver `WorkItem`s, configure `EduCommPolicy`, inspect Walk-the-Halls analytics, and run FOIA compliance exports. | Cannot retroactively edit or purge append-only message archives or signed `EduGuardianSlipResponse` audit records. |

---

## 8. Technical APIs, Guarded Commands, Events & `requiredWorkflows`

### 8.1 Guarded Domain Commands
Every state-mutating API requires `idempotencyKey`, `correlationId`, and `expectedVersion`:
- `edu.classroom.recordBehaviorOrSel` — Records `EduBehaviorEvent` (`Decimal128` points or SEL mood) and optionally escalates an `INCIDENT_REFERRAL` via Home `WorkItem` + `#161` `EduSuccessCase`.
- `edu.classroom.moderatePortfolioArtifact` — Transitions `EduPortfolioArtifact.moderationStage`, enforcing `ferpaCleared = true` before `PUBLISHED_TO_FAMILY`.
- `edu.classroom.publishBroadcast` — Validates scope ACLs, screens recipients against `#161` `EduGuardianLink.nonContactRestriction`, enforces Quiet Hours (or queues `PENDING_URGENT_APPROVAL` `WorkItem`), translates per household language, and dispatches via `MKT`.
- `edu.classroom.submitPermissionSlipResponse` — Verifies custodial guardian authority, seals `signedFullName`/`signedAt`, decrements volunteer slot inventory atomically, and triggers `FIN` `FinInvoice` or fee-waiver `WorkItem`.
- `edu.classroom.bookConferenceSlot` — Claims an `AVAILABLE` `EduConferenceSlot` using optimistic `expectedVersion` locking to guarantee zero double-bookings.

### 8.2 Domain Events Published & Consumed (Kafka)
- **Published:** `edu.behavior.recorded.v1`, `edu.behavior.incidentEscalated.v1`, `edu.portfolio.published.v1`, `edu.broadcast.dispatched.v1`, `edu.permissionSlip.signed.v1`, `edu.conference.booked.v1`, `edu.comm.safetyFlagged.v1`.
- **Consumed:** `edu.attendance.unexcusedRecorded.v1` (from `#161` for immediate truancy outreach), `edu.section.enrolled.v1` (updates roster recipients), `fin.payment.succeeded.v1` (marks `EduGuardianSlipResponse.paymentStatus = PAID`).

### 8.3 `requiredWorkflows` (Declared in `app.manifest.json`)
1. `multilingualOmnichannelBroadcastWorkflow` — Resolves eligible custodial `EduGuardianLink` recipients, runs per-language translation, respects Quiet Hours/digest windows, and tracks `MKT` delivery/read receipts.
2. `permissionSlipFeeAndReminderWorkflow` — Provisions `FinInvoice` records for paid trips, manages fee-waiver `WorkItem`s, and sends scheduled reminders exclusively to `PENDING` households.
3. `commSafetyArchiveAndKeywordScanWorkflow` — Archives two-way messages immutably and routes `safetyKeywordPatterns` hits to Campus Safety/Counselor Home `WorkItem`s in real time.
4. `weeklyGuardianDigestWorkflow` — Compiles and delivers personalized weekly student PBIS, portfolio, and upcoming deadline digests every Friday.

### 8.4 Grounded Rapider AI Rules
- AI *Sidekick* Newsletter Drafter (`CMP-025`), Tone Coach (`CMP-026`), and Conference Talking Points (`CMP-028`) MUST cite retrieved `EduPortfolioArtifact`, `EduBehaviorEvent`, `LrnCourse`, and `#161` records.
- Group newsletter drafts MUST NEVER include individual student names, behavior incidents, or FERPA-restricted details, and AI NEVER dispatches messages, publishes portfolio items, or approves permission slips without explicit educator confirmation.

---

## 9. Security, Privacy, Compliance & Non-Functional Requirements

- **COPPA, FERPA & Child Safety Protection:** Student portfolio media in Rapider Files/Drive uses private signed access scoped strictly to the student, assigned educators, and verified custodial `EduGuardianLink` accounts (`nonContactRestriction = false`). Multi-student media flags any tagged learner with `ferpaDirectoryOptOut = true` prior to publication.
- **Number Masking & FOIA Archiving:** Personal mobile numbers (`<rapider-phone-input>` E.164) of teachers and guardians are masked behind workspace relay numbers; all two-way threads and broadcasts retain immutable source + translated text for configurable district FOIA retention windows (e.g., 7 years).
- **Exact `Decimal128` Precision:** Activity/field-trip fees (e.g., `\$25.00`), partial scholarships/waivers, and weighted PBIS rubric ratios use `Decimal128` with explicit ISO currency codes.
- **Accessibility & Responsive Mobile-First UX:** Full WCAG 2.2 AA compliance (high-contrast `#ffffff !important` primary/danger buttons across light and dark themes, screen-reader labels on icon-only Delete buttons and PBIS tiles) across `390px` mobile (guardian/teacher handsets), `768px` classroom tablets, and `1440px` desktops.

---

## 10. Deterministic Acceptance Criteria

1. **Sidebar 3-Item Section Rule:** `app.manifest.json` defines 3 visible sidebar sections (`Classroom`, `Family Engagement`, `Governance`), each containing exactly 3 visible items (`displayOnMenu: true`), while all 4 detail/drawer pages set `displayOnMenu: false`.
2. **SWR & Soft-Delete Query Hygiene:** Initial loads across all pages invoke `findSWR` / `countSWR` with zero manual `isDeleted` filter clauses in API payloads and filter `item.isDeleted !== true` in memory.
3. **Search, `#activeFilterTagsBar` & Clear All:** Searching or selecting section/status/skill filters on `portfolio-moderation`, `behavior-ledger`, `stories-broadcasts`, or `slips-conferences` renders HTML-escaped chips in `#activeFilterTagsBar` with `[Clear all]`, restoring the full dataset in one click.
4. **Table Action Standard:** Zero standalone "View" buttons appear in table `Actions`; primary identifiers navigate to `#/student-engagement-detail?id=...` or `#/permission-slip-detail?id=...`; Edit buttons render icon + text and Delete buttons render icon-only with `title="Delete"` and `aria-label="Delete"`.
5. **Custom Elements Adoption:** Every phone field in `family-messages`, `slips-conferences`, and `broadcast-slip-drawer` uses `<rapider-phone-input>`, and `portfolio-moderation` uses `<rapider-kanban>`.
6. **Optimistic Lifecycle & Drawer Auto-Close:** Saving `broadcast-slip-drawer` or `portfolio-conference-drawer` resets button state in a `finally` block, calls `closePageDrawer()`, clears SWR cache, broadcasts events, and refreshes parent tables/kanban immediately; deletions confirm via `#rapiderConfirmOkBtn` with zero native `alert`/`confirm`/`prompt`.
7. **Custody & FERPA Hard Gate:** Publishing a broadcast, message, portfolio item, or permission slip deterministically excludes any `EduGuardianLink` where `nonContactRestriction = true` and blocks unapproved `ferpaDirectoryOptOut` group photos.
8. **Portfolio Pre-Publish Moderation Gate:** Student-created `EduPortfolioArtifact` items remain invisible to guardians until an educator transitions `moderationStage` to `PUBLISHED_TO_FAMILY`.
9. **Quiet Hours & Urgent Override Governance:** Standard messages sent during `EduCommPolicy` Quiet Hours queue notifications until Quiet Hours end, whereas `URGENT_SAFETY` broadcasts require `CAMPUS_ADMIN` or an approved Home `WorkItem` to bypass Quiet Hours.
10. **Atomic Conference Slot & Paid Slip Integrity:** Concurrent `edu.classroom.bookConferenceSlot` requests on the same slot succeed for exactly one guardian (`expectedVersion` guard), and approving a `\$25.00` (`Decimal128`) `EduPermissionSlip` creates a canonical `FinInvoice` (or Home `WorkItem` on waiver request).
11. **Click-Through Navigation & Base-URL Guard:** Clicking a slip row in `slips-conferences` navigates to `#/permission-slip-detail?id=...` without `<base href>` 404 diversion, renders response rows, and `Back to list` restores active filter chips.
12. **Dark/Light Theme & No `projectId`:** All 13 pages pass `validate_theme` across light and dark modes with `#ffffff !important` button contrast, and zero `Edu*` schemas or payloads contain `projectId`.
