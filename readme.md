# 🚛 Wadi Al Raihan Transport Management System
## 🌐 Complete Documentation (English & Urdu)
> **A fully client-side, offline-capable fleet operations & logistics ledger system.**  
> **مکمل آف لائن، کلائنٹ سائیڈ فلیٹ آپریشنز اور لاجسٹکس لیجر سسٹم۔**

---

## 📖 1. Overview / ایپ کا جائزہ
### 🇬🇧 English
Wadi Al Raihan Transport Management is a comprehensive, single-page, client-side application designed to manage all aspects of a transport/fleet company. It handles vehicles, drivers, maintenance scheduling, traffic fines, document expiries, corporate profiles, multi-branch catalogs, financial tracking, and automated backups. The system runs entirely in the browser using `IndexedDB`, requires no internet connection for daily operations, and stores all data locally on your device.

### 🇵🇰 اردو
وادی الریحان ٹرانسپورٹ مینجمنٹ ایک مکمل، کلائنٹ سائیڈ (براؤزر میں چلنے والی) ایپ ہے جو ٹرانسپورٹ/فلیٹ کمپنی کے ہر کام کو ایک جگہ منظم کرتی ہے۔ اس میں گاڑیاں، ڈرائیورز، مرمت کے شیڈول، ٹریفک جرمانے، دستاویزات کی میعاد، کمپنی پروفائل، ملٹی برانچ کیٹلاگ، مالی ٹریکنگ اور خودکار بیک اپ شامل ہیں۔ یہ سسٹم مکمل طور پر براؤزر میں `IndexedDB` ٹیکنالوجی استعمال کرتا ہے، روزمرہ استعمال کے لیے انٹرنیٹ کی ضرورت نہیں ہے، اور تمام ڈیٹا آپ کے ڈیوائس میں محفوظ رہتا ہے۔

---

## 🧩 2. Complete Modules & Features / مکمل ماڈیولز اور فیچرز

### 🔐 Authentication & User Roles / لاگ ان اور صارف کے رولز
| Feature / فیچر | Details / تفصیل | System Effect / سسٹم پر اثر |
|---|---|---|
| **Sign In** | Username + Password login | Grants access to dashboard based on role |
| **Register** | Create Username, Password, Confirm Password, Select Role | Adds new user to local storage |
| **Role: Administrator** | Full Access (Create, Read, Update, Delete, Settings, Backup) | Can modify all records, change themes, reset data |
| **Role: Standard User** | Read-Only + Deletes allowed | Can view/export data, delete entries, but cannot change system settings or backup |

### 📊 Dashboard & Realtime Alerts / ڈیش بورڈ اور ریئل ٹائم الرٹس
| Widget / ویجٹ | Details / تفصیل | System Effect / سسٹم پر اثر |
|---|---|---|
| **Total Vehicles** | Count of all registered vehicles | Base metric for fleet size |
| **Active Fleet** | Vehicles with status "Active" | Used in utilization & financial reports |
| **Expired Reg.** | Vehicles with registration past expiry | Triggers red alert on dashboard |
| **Total Fines (AED)** | Sum of all recorded fines | Flows into financial distribution & monthly outlay |
| **Insurance Expiry Soon** | Policies expiring within threshold | Shows in Expiry Tracker + Dashboard alert |
| **Maintenance Due** | Upcoming scheduled services | Auto-populates maintenance calendar & cost reports |
| **Total Expenses (AED)** | Sum of maintenance, fines, fuel, events | Updates financial charts automatically |
| **Recent Operational Activity** | Timeline of latest logs/events | Gives quick operational snapshot |
| **Quick Critical Alert** | Realtime updates automatically | Pushes expiry/fine/critical events to top of dashboard |

### 🏢 Company Profile & Setup / کمپنی پروفائل اور سیٹ اپ
| Field / فیلڈ | Details / تفصیل | System Effect / سسٹم پر اثر |
|---|---|---|
| **Company Name, Trade Licence, Unified Licence, Reg. No.** | Core corporate identifiers | Printed on all executive reports & PDFs |
| **Owner/Manager Name, Mobile, Email, Address** | Contact & ownership info | Appears in headers, exports, and corporate directory |
| **Licence Issue/Expiry Date** | Legal validity period | Tracked in Expiry Tracker module |
| **Business Activities & Notes** | Operational scope & internal remarks | Visible in profile & reports |
| **Multi-Branch Catalog** | Register New Corporate Branch/Company (Name + Official Mobile) | Enables fleet segmentation across branches |

### 🎨 UI Theme Customizer / تھیم اور ڈسپلے سیٹنگز
| Option / آپشن | Details / تفصیل | System Effect / سسٹم پر اثر |
|---|---|---|
| **Font Family** | Inter, Outfit, System UI | Changes all text rendering |
| **Font Size** | Small (14px), Normal (16px), Large (18px) | Adjusts readability across all pages |
| **Theme Colors** | Accent Color, Header BG/Text, Sidebar BG/Text, Footer BG | Updates CSS variables globally; persists in local storage |

### 🔑 Password Management / پاس ورڈ مینجمنٹ
- **Current Password** → Validates existing credentials
- **New Password** → Minimum 8 characters + 1 symbol required
- **Confirm New Password** → Ensures match before saving
- *Effect:* Updates user authentication hash in IndexedDB. Requires re-login if session expires.

### 🚗 Vehicle Management / گاڑیوں کا انتظام
| Component / جزو | Details / تفصیل | System Effect / سسٹم پر اثر |
|---|---|---|
| **Add New Vehicle** | Internal Code, Plate No, Reg Emirate (7 UAE Emirates), Vehicle Type, Make/Brand, Model, Year, Body Color, Chassis (17 chars), Engine No, Fuel Type (Diesel/Petrol/CNG/Electric), Odometer, Assigned Driver, Location, Status, Reg Issue/Expiry, Insurance Co/Policy/Expiry, Permit No/Expiry, Comments | Core fleet record. Links to driver, maintenance, fines, expiry tracker, and reports |
| **Filters** | Type: Light Truck, Heavy Truck, Bus, School Bus, Passenger Bus \| Status: Active, Inactive, Under Maintenance, Sold | Filters table & report datasets dynamically |
| **Table Columns** | Internal Code, Plate No, Type, Brand/Model, Driver, Reg Expiry, Status, Actions | Quick reference view. Actions: Edit, View Details, Log Event, Delete |
| **Vehicle Detail View** | Print Vehicle Report, Log Event, Specifications & Diagnostics, Document Expiring Status, Policy & Permits, Operational Log Timeline (All, Maintenance, Repair, Accident, Fine, General Note) | Central hub for single vehicle history. Feeds data into reports & alerts |

### 👨‍✈️ Driver Roster / ڈرائیورز کی فہرست
| Component / جزو | Details / تفصیل | System Effect / سسٹم پر اثر |
|---|---|---|
| **Add New Driver** | Full Name, Mobile, Emirates ID Sequence, Licence ID, Licence Expiry, Assigned Vehicle, Employment Status (Active/Inactive), Internal Notes | Links driver to vehicle. Expiry feeds into tracker & dashboard |
| **Table Columns** | Driver Name, Mobile, Emirates ID, Licence No, Licence Expiry, Assigned Vehicle, Status, Actions | Quick roster view. Updates vehicle assignment counts & utilization metrics |
| **Cross-Link Effect** | Assigning a driver to a vehicle updates both rosters, triggers dashboard utilization stats, and appears in driver deployment reports |

### 🔧 Fleet Maintenance Scheduling / مرمت اور سروس شیڈولنگ
| Component / جزو | Details / تفصیل | System Effect / سسٹم پر اثر |
|---|---|---|
| **Book Maintenance** | Fleet Vehicle, Task Category/Type, Service Date, Next Service Due, Odometer Mileage, Total Cost (AED), Contractor/Workshop Name, Parts & Spares Replaced, Workflow Status (Completed/Pending/Scheduled), Maintenance Comments | Creates service record. Cost flows into financial reports. Next Due auto-triggers expiry/maintenance alerts |
| **Table Columns** | Vehicle, Task Category, Workshop, Service Date, Next Due Date, Cost (AED), Status, Actions | Schedule overview. Status updates dashboard counters & report analytics |
| **Effect on System** | Completed maintenance resets odometer/service counters, updates vehicle health status, and reflects in monthly outlay trends |

### 🎫 Violations & Traffic Fines / ٹریفک چالان اور جرمانے
| Component / جزو | Details / تفصیل | System Effect / سسٹم پر اثر |
|---|---|---|
| **Record Traffic Fine** | Violating Vehicle, Offending Driver, Ticket No, Fine Authority (9 UAE Authorities), Infraction Date, Penalty Cost (AED), Ledger Status (Unpaid/Paid/Disputed), Settlement Date, Offence Description, Internal Notes | Logs financial & legal liability. Unpaid fines highlight in dashboard. Paid fines update financial distribution |
| **Table Columns** | Ticket No, Vehicle, Driver, Authority, Fine Date, Amount (AED), Status, Actions | Quick violation tracker. Status filters affect report totals & alerts |
| **Effect on System** | Fine amounts auto-add to Total Expenses. Disputed status triggers review flags in reports. Settlement dates update ledger accuracy |

### 📅 Corporate Expiry & Renewal Tracker / میعاد ختم ہونے والی دستاویزات کا ٹریکر
| Component / جزو | Details / تفصیل | System Effect / سسٹم پر اثر |
|---|---|---|
| **Tracker Table** | Document/Resource Name, Context/Link, Expiration Date, Days Left, Alert Level (Green/Yellow/Red) | Centralized expiry monitor. Pulls data from vehicle insurance, permits, driver licenses, company licences |
| **Effect on System** | Triggers dashboard alerts, auto-highlights in reports, and prompts renewal actions. Prevents legal/financial penalties |

### 📈 Corporate Insights & Reporting / رپورٹس اور تجزیات
| Component / جزو | Details / تفصیل | System Effect / سسٹم پر اثر |
|---|---|---|
| **Export/Print** | Print Executive Report, Export CSV | Generates official PDFs & spreadsheets for accounting/audits |
| **Insights Categories** | Executive Summary & Charts, Fleet Inventory & Utilization, Maintenance Service & Costs, Ticket & Violation Analytics, Registrations & Permits Expiry, Driver Deployments & Profile | Aggregated analytics across all modules |
| **Filters** | Start Date, End Date, Apply Filters, Reset | Narrows dataset for time-bound analysis |
| **Visualizations** | Financial Distribution, Monthly Outlay Trend, Detailed Data Log | Auto-updates as new expenses, fines, or maintenance records are added |
| **Effect on System** | Provides decision-making data. Identifies high-cost vehicles, frequent offenders, maintenance trends, and licence compliance rates |

### 📝 Event Logging System / ایونٹ لاگنگ سسٹم
| Component / جزو | Details / تفصیل | System Effect / سسٹم پر اثر |
|---|---|---|
| **Add Log Event** | Category (Maintenance, Repair, Accident, Fine, Inspection, Insurance, Registration, Permit, Fuel, Driver Change, General Note), Headline/Title, Odometer (KM), Expense Cost (AED), Event Date, Detailed Description, Reference Document | Creates audit trail. Expenses flow into financial reports. Odometer updates vehicle diagnostics. Links to vehicle timeline |
| **Effect on System** | Maintains historical accuracy. Supports dispute resolution, warranty claims, and compliance audits |

### 💾 Corporate Ledger Backup & Restore / ڈیٹا بیک اپ اور بحالی
| Feature / فیچر | Details / تفصیل | System Effect / سسٹم پر اثر |
|---|---|---|
| **Export Data Archive** | Packages entire IndexedDB schema, settings, logs into JSON. Regular offline exports recommended | Creates portable, version-controlled data snapshot |
| **Generate & Download Backup JSON** | One-click export | Saves file to device for cloud/USB storage |
| **Restore Data Archive** | Upload & Import JSON, validates records, merges non-duplicates | Safely recovers data across devices. Prevents overwrites |
| **Seed Sample Data** | Populates with realistic sample vehicles, drivers, violations, maintenance. Overwrites/merges | Demo/Testing mode. Useful for training or fresh setups |
| **Automated Daily Backup** | Enable Auto-Backup, Set Scheduled Time, Update Schedule Settings. Requires app to be open | Prevents data loss. Runs prompt-based export at chosen time |
| **Start Fresh** | Erases vehicles, drivers, fines, histories, maintenance. Keeps login & company profiles | Cleans operational data while preserving credentials & branding |
| **System Reset** | Permanently erases offline storage context. Clears all records, profiles, settings. Cannot be undone | Factory reset. Use only for complete system wipe |

---

## 📖 3. Step-by-Step Usage Guide / استعمال کا مرحلہ وار طریقہ

### 🟢 Step 1: Account Setup / اکاؤنٹ بنائیں
1. Open `index.html` in any modern browser.
2. Click **Register here**.
3. Enter Username, Password (8+ chars, 1 symbol), Confirm Password.
4. Select Role: `Administrator` (Full Control) or `Standard User` (View + Delete).
5. Click **Register** → Then **Sign In** with credentials.

### 🟢 Step 2: Company Setup / کمپنی کا ڈیٹا درج کریں
1. Go to **Profile** (`#/company`).
2. Fill all corporate fields (Name, Licences, Contact, Address, Dates, Notes).
3. Click **Save Profile Changes**.
4. (Optional) Add branches via **Register New Corporate Branch**.
5. Adjust **Theme Customizer** & **Password** if needed.

### 🟢 Step 3: Add Vehicles & Drivers / گاڑیاں اور ڈرائیورز شامل کریں
1. **Vehicles** → `Add New Vehicle` → Fill all fields (Plate, Emirate, Type, Brand, Model, Year, Chassis, Engine, Fuel, Odometer, Driver, Location, Status, Reg/Insurance/Permit dates) → **Save**.
2. **Drivers** → `Add New Driver` → Fill Name, Mobile, EID, Licence, Expiry, Assign Vehicle, Status → **Save**.
3. Cross-linking happens automatically. Dashboard counters update instantly.

### 🟢 Step 4: Schedule Maintenance & Record Fines / مرمت اور جرمانے ریکارڈ کریں
1. **Maintenance** → `Book Maintenance` → Select Vehicle, Task, Dates, Cost, Workshop, Parts, Status, Comments → **Save**.
2. **Fines** → `Record Traffic Fine` → Select Vehicle/Driver, Ticket No, Authority, Date, Amount, Status, Description → **Save**.
3. Financial totals & expiry alerts update in real-time.

### 🟢 Step 5: Monitor Expiries & Generate Reports / میعاد اور رپورٹس چیک کریں
1. **Expiry Tracker** → View `Days Left` & `Alert Level`. Renew items before red alerts.
2. **Reports** → Set Date Range → `Apply Filters` → View Charts/Logs → `Print Executive Report` or `Export CSV`.
3. Use **Event Log** for any operational notes, fuel fills, inspections, or driver changes.

### 🟢 Step 6: Backup & Data Safety / بیکاپ اور ڈیٹا محفوظ رکھیں
1. Go to **Backup & Restore**.
2. Click **Generate & Download Backup JSON** weekly.
3. Enable **Automated Daily Backup** & set time.
4. Use **Restore** to import on new devices.
5. Use **Start Fresh** for clean operational reset, or **System Reset** for complete wipe.

---

## 🔗 4. How Each Feature Affects the Entire System / ہر فیچر کا پورے سسٹم پر اثر

| Action / عمل | Immediate Effect / فوری اثر | Downstream Impact / آگے چل کر اثر |
|---|---|---|
| Add Vehicle | Appears in dashboard count, vehicle table | Enables driver assignment, maintenance scheduling, fine logging, expiry tracking, report generation |
| Assign Driver to Vehicle | Updates driver roster & vehicle detail | Reflects in utilization reports, deployment analytics, legal liability mapping |
| Log Maintenance | Updates cost totals, vehicle service status | Triggers next due date alerts, affects financial distribution charts, resets service counters |
| Record Fine | Adds to Total Expenses, flags vehicle/driver | Impacts violation analytics, legal compliance tracking, dashboard alerts, executive summaries |
| Document Expiry Approaches | Changes Alert Level (Green→Yellow→Red) | Pushes dashboard critical alert, highlights in reports, prompts renewal workflow |
| Log Event | Creates timeline entry, updates odometer/cost | Feeds audit trails, supports dispute resolution, updates detailed data logs |
| Theme/Profile Change | Updates UI immediately, persists locally | Affects print headers, export branding, user experience consistency |
| Backup/Restore | Packages/imports JSON schema | Ensures cross-device continuity, prevents data loss, enables version control |
| Role Change | Alters UI permissions dynamically | Restricts/enables access to settings, backups, deletions, exports |

---

## 👥 5. User Roles & Access Control / رولز اور اجازتیں

| Role / رول | Permissions / اجازتیں | Restrictions / پابندیاں |
|---|---|---|
| **Administrator** | Full CRUD, Theme/Profile edits, Backup/Restore, Reset, Report generation, Export, Sample data load | None |
| **Standard User** | View all modules, Add/Edit/Delete records, Log events, Export CSV, Print reports | Cannot change company profile, theme, password, backup settings, or system reset |

---

## 🛡️ 6. Technical Architecture (Client-Side Only) / ٹیکنیکل ڈھانچہ

| Aspect / پہلو | Implementation / نفاذ |
|---|---|
| **Frontend** | HTML5, CSS3 (CSS Variables for theming), Vanilla JavaScript |
| **Routing** | SPA Hash Routing (`#/dashboard`, `#/vehicles`, etc.) |
| **Database** | `IndexedDB` (Local, Offline, Structured JSON Schema) |
| **State Management** | Real-time DOM updates, Auto-refresh counters, LocalStorage for theme/auth |
| **Backup Format** | Structured JSON export/import with duplicate validation & safe merge |
| **Offline Capability** | 100% functional without internet. Auto-backup requires app open |
| **Security** | Client-side password hashing, Role-based UI gating, Local-only storage |
| **Performance** | Filtered tables, Lazy-loaded charts, Debounced inputs, JSON compression |

---

## 📞 7. Support & Credits / سپورٹ اور کریڈٹس
- **Developer / ڈویلپر:** Yasin Ullah – Bannu Software Solutions
- **Contact / رابطہ:** 📱 WhatsApp: [03361593533](https://wa.me/923361593533)
- **Last Updated / آخری اپڈیٹ:** June 2026
- **License / لائسنس:** Private Client Distribution. All rights reserved.

> 🌟 **Note for Client / کلائنٹ کے لیے نوٹ:**  
> This system is designed to run locally on your computer or tablet. No internet is required for daily use. Always perform weekly backups. If you see a red alert, renew the document immediately to avoid fines. For training, demo, or technical support, contact the developer via WhatsApp.  
> *یہ سسٹم آپ کے کمپیوٹر یا ٹیبلیٹ پر مقامی طور پر چلتا ہے۔ روزمرہ استعمال کے لیے انٹرنیٹ کی ضرورت نہیں۔ ہفتہ وار بیک اپ ضرور کریں۔ سرخ انتباہ آنے پر فوراً دستاویز تجدید کروائیں۔ تربیت یا سپورٹ کے لیے واٹس ایپ پر رابطہ کریں۔*

---
📄 **Documentation Version:** `1.0.0` | **Compatibility:** `All Modern Browsers (Chrome, Edge, Firefox, Safari)` | **Architecture:** `Client-Side SPA + IndexedDB`