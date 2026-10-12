---
name: sesame-official-documents
description: >
  Generate official Sesame Technologies Pvt. Ltd. proposals, covering letters, AMC quotes, platform-upgrade
  quotes and business letters as branded Word (.docx) and PDF files with the company logo, header, footer and
  cover page, built from the bundled template (assets/Sesame_Proposal_Template.docx). Automatically adapts
  content, modules, security scope, compliance and pricing to the client type (school/college, co-operative
  bank/NBFC, corporate/business group, hospital, hotel/resort, e-commerce/retail, construction/real estate,
  government/PSU, trust/NGO, travel, custom application, platform upgrade & AMC). Use whenever the user asks
  for a proposal, quotation, quote, covering letter, AMC offer or official letter for any client.
---

# Sesame Technologies Official Document & Proposal Skill

This skill defines how to produce official documents for **Sesame Technologies Pvt. Ltd.** as **branded .docx (and PDF)** files, and how to adapt each document to the client's sector.

**Core idea:** the bundled template supplies the branding (logo, header, footer, cover page, styles). This skill supplies the content rules. Never produce plain `.txt` or unbranded output.

---

## 0. Execution Workflow (follow in order)

1. **Read the `docx` skill** (`/mnt/skills/public/docx/SKILL.md`) before touching any file, and the `pdf` skill if a PDF is needed.
2. **Identify the document type** (Section 3) and the **client type** (Section 5).
3. **Collect missing inputs** (Section 1). Ask for them in ONE short message. Never invent them.
4. **Copy the template** `assets/Sesame_Proposal_Template.docx` to a working folder. Always work on the copy.
5. **Unpack, edit, repack** the copy with the docx skill's workflow. Keep intact: header (Sesame logo + company name), footer (confidentiality line + "Page X of Y"), cover page layout, styles, numbering, table formatting.
6. **Fill the cover page, header/footer and every placeholder** (Section 2).
7. **Rewrite sections for the client type** (Section 5). The template is a *school* proposal; its school-specific text (Requirement, modules, school wording) MUST be replaced for any non-school client.
8. **Apply mandatory boilerplate** (Section 6) verbatim where marked.
9. **Update the Table of Contents** to match the sections actually included, and refresh page numbers.
10. **Convert to PDF** with LibreOffice (`soffice --headless --convert-to pdf`) and render pages to images to visually check logo, cover, tables and page breaks.
11. **Run the QA checklist** (Section 8), then deliver the `.docx` and the `.pdf` to `/mnt/user-data/outputs/` and share with `present_files`. Name files `Sesame_<Client>_<DocType>_v1.0.docx/.pdf`.

If the user asks for only Word or only PDF, deliver only that. Default is both.

---

## 1. Inputs to Collect (never fabricate)

| Input | Notes |
| :--- | :--- |
| Client name, recipient designation, address | For the covering letter and cover page |
| Client type / sector | Decides Section 5 profile |
| Specific requirements / modules | If the brief is thin, propose modules from the matching profile and mark them "proposed" |
| **Quote sequence number** | Needed for the Quote Ref. No. Ask; do not guess |
| **Website development cost** | Always ask. Never invent a development price |
| Number of third-party API integrations | Priced per API |
| Domain: new or client-owned | Affects investment table |
| Languages (English / Malayalam / other) | Bilingual affects scope |
| Free support period if different from default | Default: 1 year from go-live |

If the user gives a price, a date or a period that differs from this skill, **the user's value wins**. Keep all sections consistent with it, and tell the user in the reply that you overrode the default.

---

## 2. Company Identity, Header Fields & Placeholders

* **Company Name:** Sesame Technologies Pvt. Ltd.
* **Tagline / Metrics:** `25 Years | 1300 Projects | 750+ Customers | 13 Countries`
* **Workforce:** 30+ IT professionals
* **CEO / Signatory:** Sheen Chungath
* **Cell:** +91 9349138146 / +91 9349 11 89 84
* **Email:** sheen@sesametechnologies.net
* **Website:** www.sesametechnologies.net

### Cover page fields

| Field | Rule | Example |
| :--- | :--- | :--- |
| Title | `PROPOSAL FOR DEVELOPING <WHAT> FOR <Client Name>` (adapt to the document) | `PROPOSAL FOR DEVELOPING AN ATTRACTIVE WEBSITE FOR ABC CO-OPERATIVE BANK` |
| Quote Ref. No | `ST/<Sequence_Number>/<Day>/<Month>/<Year>` | `ST/104/18/2/2026` |
| Dated issued | `DD/MM/YYYY`, today's date | `18/02/2026` |
| Validity | `1 month from date issued` | |
| Version | `1.0` (`1.1` on revision) | |

### Placeholders to replace everywhere
* `<Client Name>` on the cover page (appears twice in the cover text frames; replace both).
* Footer: `Confidential document, prepared for <Client Nme> from Sesame Technologies`. **The template footer has a typo ("Nme"); write the footer as "...prepared for <Client Name> from Sesame Technologies".**
* Covering letter recipient block (`To`, designation, client name, address).
* Any `<...>` left in the body. After editing, search the XML for `&lt;` to confirm none remain.

Placeholders can be split across XML runs. Check the raw XML, not just the rendered text.

---

## 3. Document Types

### Type 1: Comprehensive Proposal (new website / application)
Full 12-part document. Starting point is the template as-is:
1. Covering Letter
2. Executive Summary
3. The Requirement
4. Solution by Sesame (site map / module breakdown)
5. Security Features
6. Investment
7. Annual Maintenance Contract (AMC)
8. Technical Proposal
9. Delivery and Payment Plans
10. Terms and Conditions
11. Company Overview
12. Our Infrastructure & Contact Details

(The template numbers the last two both as "11". Number them 11 and 12.)

### Type 2: Standalone Covering Letter
Single branded letter (use the template's header/footer, drop the cover page and TOC):
* Recipient block (`To: The Secretary / The President / <Name>`)
* Standard intro paragraph with the 25-year history
* Core capabilities list
* Request for consideration and call to action
* Sign-off: `Yours Sincerely, For Sesame Technologies Pvt. Ltd., Sheen Chungath | CEO`

### Type 3: Platform Upgrade & AMC Proposal
For upgrading an existing platform (for example end-of-life PHP) and securing an AMC. Remove sections that do not apply (Executive Summary and Company Overview are optional, keep them short):
1. Covering Letter
2. The Requirement
3. Solution by Sesame (risk evaluation of the end-of-life platform)
4. Scope of Work: Website Platform Upgrade
5. Free Support Period (1 year post go-live)
6. Annual Maintenance Contract (post one year)
7. Investment Table
8. Delivery and Payment Plans
9. Terms and Conditions
10. Our Infrastructure & Contact Details

### Type 4: AMC-only Quote / Official Notice / Business Letter
Branded letter plus, for AMC, Section 7 content and an investment table. Keep it to what was asked.

---

## 4. Branding & Layout Rules

* The Sesame logo sits in the template header (`word/header1.xml`, image `media/image1.jpg`). **Do not delete, replace or resize it.** Every page of every document must show it.
* Keep the template's fonts, heading styles (`Heading2`, `TOC2`, `Caption`, `NormalWeb`, `ListParagraph`), table styles, margins and page numbering.
* Insert content using the existing styles. Do not introduce new fonts or colours.
* New tables must copy the formatting of the template's existing tables (header row shading, borders).
* Keep the closing block "Authorized Signature / Company Seal" on the last page.
* Tone: professional, formal Indian corporate IT tone. Spelling: British/Indian English.

---

## 5. Client-Type Profiles (apply the matching profile)

For every client type, adapt **all** of these: cover title, covering letter subject (`Sub:`), Section 3 Requirement paragraph, Section 4 modules, Section 5 security scope, Section 6 investment extras, and the sector-first ordering of the industries list in the Executive Summary. Keep wording of unchanged boilerplate verbatim.

Greeting: use `Sir / Madam,` unless the recipient is known.
Subject pattern: `Sub: Proposal for developing <an attractive website / a web application / ...> for <Client Name>.`

### A. School / College / Educational Institution
* **Requirement:** Attractive, responsive website that presents the institution, academics, admissions and news, with an admin panel so staff can update content without depending on Sesame.
* **Modules:** use the template's Section 4 structure: Home (banner, features carousel, flash news, achievements, events) · Management (profile, leadership, vision and mission, principal's message, affiliations, infrastructure, mandatory disclosure, affidavit) · Academics (examinations, faculty, curriculum, KG section, calendar, teachers training, achievements) · Students (anthem, students corner, extracurricular, strength, alumni, parliament, downloads) · Parents (PTA) · General (careers, staff, annual report, circulars, gallery, news and events, guest book, academic session, location, TC checking, list of books) · Contact Us · Footer links (Help Desk, Terms, Disclaimer, Privacy).
* **Mandatory highlights:** mandatory disclosures, academic calendar, online admission enquiry form, news ticker, photo/video gallery, downloadable syllabus/TC documents, student/parent notice board.
* **Notes to retain:** third-party app data (for example a parent app) needs APIs from that vendor; legal page content (disclaimer, privacy, terms) is supplied by the client.
* **Security:** standard set (Section 6.5 items 1–9, 11–12); add 10 (maker-checker) only if requested.

### B. Co-operative Bank / Urban Bank / NBFC
* **Requirement:** Secure, RBI-aligned, CERT-In-audit-ready bank website with bilingual support and customer tools.
* **Modules:** Home · About the bank · Board of Directors directory · Products (deposits, loans) · FD and Loan interest rate calculators · Branch and ATM locators · Services · Downloads and forms · Annual financial statements archive · Notices · DICGC mandatory QR code display · Careers · Contact · English/Malayalam toggle.
* **Security:** the **complete 13-point suite** in Section 6.5, including maker-checker workflow and VAPT/CERT-In compliance. RBI cybersecurity framework alignment must be called out in Section 3 and Section 5.
* **Investment:** use the Banking Package table (6.6B) with VPS, backups, wildcard SSL and `.bank.in` domain option.
* **Delivery:** 60-day milestone plan (6.9).

### C. Corporate / Business Group / Manufacturing / Product Company
* **Requirement:** Professional corporate website that builds credibility and generates enquiries.
* **Modules:** Home · About (profile, leadership, vision and mission) · Products / Services (with detail pages) · Industries / Divisions · Clients and Projects · Certifications · Downloads and brochures · News and Blog · Careers · Enquiry / Contact with form and map · Admin panel (CMS).
* **Optional:** multilingual, product catalogue with enquiry cart, investor/CSR pages.
* **Security:** standard set; add maker-checker if the client has multi-level content approval.

### D. Hospital / Clinic / Healthcare
* **Requirement:** Trustworthy website that presents departments, doctors and facilities and lets patients book or enquire.
* **Modules:** Home · About · Departments / Specialities · Doctors directory · Appointment request form · Health packages · Facilities and Infrastructure · Insurance / TPA information · Patient testimonials · Gallery · News and Events · Careers · Contact with map.
* **Notes:** Online appointment booking or HIS/EMR integration needs APIs from the hospital's vendor and is priced per API. State that no patient medical data is stored on the website unless explicitly contracted.
* **Security:** standard set plus emphasis on data protection of enquiry and appointment data.

### E. Hotel / Resort / Homestay / Hospitality
* **Requirement:** Visually rich website that showcases rooms and experiences and converts visitors into bookings or enquiries.
* **Modules:** Home (hero slider) · About · Rooms / Suites with tariff display · Amenities · Dining · Experiences / Activities · Gallery (photo and video) · Offers · Booking enquiry form · Guest reviews · Location and how to reach · Contact.
* **Optional:** booking engine or channel-manager integration (priced per API), payment gateway.
* **Security:** standard set.

### F. E-commerce / Retail
* **Requirement:** Secure online store with catalogue, cart, checkout and order management.
* **Modules:** Home · Category and product pages · Search and filters · Cart and checkout · Customer accounts · Payment gateway · Order management · Inventory · Shipping/courier API · GST invoice generation · Coupons and offers · Admin dashboard and reports.
* **Notes:** Payment gateway and courier integrations are priced per API; gateway charges are borne by the client. Card data is handled by the gateway, never stored on Sesame-hosted servers.
* **Security:** full suite items 1–9 and 11, plus 13 (VAPT) when handling payments.

### G. Construction / Real Estate / Architecture
* **Requirement:** Portfolio-driven website that showcases projects and captures leads.
* **Modules:** Home · About · Projects (ongoing, completed, upcoming) with project detail pages · Floor plans and specifications · Gallery · Amenities · Location map · Enquiry / Site-visit request · Testimonials · Careers · Contact. Display RERA registration details where applicable.
* **Security:** standard set.

### H. Government / PSU / Autonomous Body
* **Requirement:** Secure, accessible, bilingual website aligned with government web guidelines and audit requirements.
* **Modules:** Home · About · Organisation structure · Services · Schemes / Programmes · Notices and Circulars · Tenders · RTI · Downloads · Gallery · Contact · English/Malayalam toggle.
* **Security:** complete 13-point suite, CERT-In audit readiness, and accessibility compliance (screen reader, keyboard navigation, text resizing, high contrast) called out prominently; mention alignment with GIGW (Guidelines for Indian Government Websites).
* **Delivery:** 60-day plan.

### I. Trust / NGO / Religious / Charitable Organisation
* **Requirement:** Clear, credible website that presents the organisation's work and supports donations and volunteering.
* **Modules:** Home · About and History · Activities / Projects · Events · Gallery · Publications / Newsletters · Donation page with payment gateway (priced per API) · Volunteer registration · Contact.
* **Security:** standard set.

### J. Travel & Tourism
* **Modules:** Home · Destinations · Tour Packages with itineraries · Package enquiry/booking form · Gallery · Testimonials · Blog · Contact. Payment gateway optional (per API).

### K. Custom Web / Mobile Application (bespoke)
* **Requirement:** Written from the client's brief as a business problem, not a feature list.
* **Solution:** Replace the site map with a **module breakdown** and **user roles**. Ask the user for the module list; do not invent functional scope.
* **Technical:** keep Section 6.8; add mobile stack only if provided.
* **Investment:** effort-based (modules / man-days). Ask the user for the figures.
* **Scope control:** state that development is strictly per the approved CRS (Terms 8 and 14).

### L. Platform Upgrade & AMC (Type 3)
* **Mandatory highlights:** vulnerability analysis of the end-of-life framework/PHP version, staging environment setup, zero-downtime migration strategy, regression testing, 1-year complimentary bug-fix window, transparent yearly AMC cost (INR 3,000 – INR 15,000 depending on platform size; confirm with user).

### M. Any other sector
Choose the closest profile above, build Requirement and modules from the user's brief, mark assumed modules as "proposed", and ask the user to confirm them.

---

## 6. Mandatory Section Content & Boilerplate

### 6.1 Covering Letter (keep wording; change only recipient, subject, and the "enquiry" sentence to match the document)

```text
To
<Recipient Designation / Name>,
<Client Organization Name>
<Address / Location>

Sub: Proposal for developing <...> for <Client Name>.

Sir / Madam,

We introduce ourselves, Sesame Technologies Pvt Ltd., as one among the fastest growing companies in information technology industry of Kerala. With our brilliant work force of 30+, we have been successfully serving the IT segment for the past 25 years.

We have to our credit more than 750 satisfied clients from 13 countries and has done more than 1300 successful projects.

The expertise gained from doing such a wide array of projects in multiple domains and verticals has helped us in offering dependable solutions in the areas like:
• Web designing & development
• Web & Mobile application development
• E-Commerce solutions
• Cyber security
• IT consulting services

Based on your enquiry for <developing a new website / ...> for your esteemed concern, we are happy to provide the proposal & quote for the same.

I kindly request you to spare some of your valuable time to go through this quotation, and please don't hesitate to get in touch with us for any further clarification on this quote and proposal.

Thanking you,

Yours Sincerely,
For Sesame Technologies Pvt. Ltd.,

Sheen Chungath | CEO | Cell: +91 9349138146 | Email: sheen@sesametechnologies.net
```

### 6.2 Executive Summary (verbatim; list the client's sector first in "Industry Experience")

```text
Sesame Technologies Pvt. Ltd. is led by a team of experts in the IT industry who has commendable knowledge in Information Technology, Administration & Finance, Operations, and Sales & Marketing. Our leadership team has vast experience in developing customized applications, products, and services and has proven their skills by successfully running this establishment so that our customers are always ensured to get the best and professional solutions for their pain points. The stability of our leadership team has helped the company to showcase a proven and winning track record of more than 25 years in the IT industry.

Our Mission: To help people and businesses to experience innovations in Information Technology and build long-term win-win relationships and also to provide a dynamic and challenging working environment for our team members helping them to learn, collaborate, interact and innovate.

Our Vision: To take Sesame Technologies to greater heights and popularizing Sesame across the IT industry as a Niche skill company who can contribute value additions to any IT solution.

Industry Experience:
• Education
• Hospitality
• Construction
• Retail
• Health Care
• Manufacturing
• Travel
• Co-operative Banking & NBFC
```

The template also has a closing sentence about gaining an edge over the competition. Keep it unchanged.

### 6.3 The Requirement
One to two paragraphs, written from the client's perspective using the profile in Section 5. Never leave the template's school wording in a non-school document.

### 6.4 Solution by Sesame
Open with the template's "25 years of expertise..." lead-in, then the numbered module breakdown from the client profile (4.1, 4.2 ...), then **Notes** (editable-by-client sections, back-end admin panel, third-party APIs to be provided by their vendors, legal page content to be supplied by client).

### 6.5 Security Features (Section 5 of the document)
Use the template's NormalWeb heading + bullet format. Scope depends on client type (Section 5). The complete suite:

1. **Secure User Verification:** Google reCAPTCHA to prevent automated bots and spam.
2. **Protected Cookies & Session Management:** `Secure`, `HttpOnly`, `SameSite` flags against XSS and session hijacking.
3. **Firewall Hardening:** Access restricted to ports 80 (HTTP) and 443 (HTTPS); unnecessary inbound/outbound traffic blocked.
4. **Disabling Legacy Services:** Removal of Telnet, Finger, rlogin, FTP; SFTP/FTPS enforced.
5. **Safe Library Versions:** Upgraded jQuery, Lodash, framework dependencies with routine security audits.
6. **Modern Security Headers:** HSTS, CSP, Referrer-Policy, Permissions-Policy.
7. **Database Protection:** Private network isolation; no public DB port binding.
8. **Hardened SSH Access:** Key-based authentication only; 2FA for server access.
9. **VPS Security Hardening:** Latest Linux kernel security patches, isolated VPS, DDoS mitigation.
10. **Maker-Checker Approval Workflow:** Dual-authorization pipeline for critical content and data actions.
11. **Bot & Crawler Control:** Whitelist legitimate search engines (Google, Bing, Yahoo) and AI bots (ChatGPT); block malicious crawlers.
12. **Accessibility Compliance:** Screen-reader support, keyboard-only navigation, text resizing tool, high-contrast UI.
13. **VAPT & CERT-In Audit Compliance:** full support for VAPT testing; fixing Critical, High, Medium and Low findings; CERT-In audit compliance fixing (headers, server hardening, SSL); coordination with CERT-In empanelled auditors; OWASP Top 10 mitigation (SQL Injection, XSS, Broken Authentication, Data Exposure, Access Control).

Banks, financial institutions and government bodies: **always all 13.**

### 6.6 Investment & Commercials
All prices in the template's table format, with the GST note: `*18% GST is extra on all rates quoted here.` Never invent the development cost (ask). Keep an "Inclusions" and "Exclusions" list and a "Please note" list (for example "The site will be in English language" or "bilingual English/Malayalam" as applicable).

#### A. Standard Package (schools, companies, hospitality, trusts and similar)
| Service | Cost (INR) | Remarks |
| :--- | :--- | :--- |
| Website development cost | `<Amount>` + GST | One time |
| API integration works (per API) | 20,000 + GST | One time |
| Domain name registration | INR 1,400 + GST, or "Client already has" | Yearly |
| Web hosting / server space | 12,500 + GST | Yearly |
| SSL certificate (single domain) | 4,500 + GST | Yearly |
| AMC | 20% of development cost | Yearly (post free-support period) |

#### B. Banking / High-Security Package
| Service Item | Cost (INR) | Remarks |
| :--- | :--- | :--- |
| Website Development Cost | INR `<Amount>` + GST | One time |
| Domain Name Registration (`.bank.in` / `.com` / `.org`) | INR 1,400 + GST (or Client Provided) | Yearly |
| VPS Server Space (2 Core CPU, 4GB RAM, 80GB SSD) | INR 26,000 + GST | Yearly |
| Server Setup & Hardening | INR 5,000 + GST | One time |
| Daily Automated Backup | INR 8,000 + GST | Yearly |
| Weekly Offsite Backup | INR 5,200 + GST | Yearly |
| Wildcard SSL Certificate (`*.domain.com`) | INR 9,850 + GST | Yearly |
| SSL Implementation & Configuration | INR 4,000 + GST | One time |
| Annual Maintenance Contract (AMC) | 20% of development cost | Yearly (post 1st year) |
| Additional Customization / T&M Support | INR 1,000 + GST | Per hour |

Use package B for banks, NBFCs and government clients, and for any client who needs VPS-grade hosting or backups. If the user gives different infrastructure rates, use theirs.

#### Standard inclusions / exclusions
* **Inclusions:** development of the site as per the scope; one-time hosting to the web server; free support period (see 6.7).
* **Exclusions:** email IDs if required; support after the free period; content entry; third-party charges (payment gateway, SMS, maps and similar).

### 6.7 Annual Maintenance Contract (AMC)
* **Standard Rate:** 20% of initial development cost per annum.
* **Free Support Period:** **1 year from go-live** (bug fixes, minor compatibility adjustments, server maintenance), unless the user specifies another period. **The template's Investment exclusions mention a "3-month free period": replace it with the chosen period so the document is consistent.**
* **AMC Inclusions:** bug fixes, security patches, framework maintenance, routine backup monitoring; server uptime, disk, CPU and memory monitoring; server-level backup configuration and restore support.
* **AMC Exclusions:** new features, modules, pages or website redesign; major content changes, bulk uploads or content creation; structural design revisions; third-party API integration changes.
* **T&M Rate:** out-of-scope work billed at INR 750 – INR 1,000 per man-hour.
* Keep the template's structure: 7.1 Scope, 7.2 Inclusions (A. Website Maintenance, B. Server Maintenance), 7.3 Exclusions, 7.4 General Conditions.

### 6.8 Technical Proposal (template table, keep as is unless the user specifies a different stack)
| Layer | Specification |
| :--- | :--- |
| Platform / OS | Linux (Ubuntu / RHEL / AlmaLinux) |
| Web Server | Nginx (hardened) |
| Front-end | Next.js / Gulp.js / HTML5 / CSS3 / JavaScript |
| Application Type | Web-based application (hosting mode: Internet) |
| Backend | Laravel / PHP (latest stable supported version) |
| Database | MySQL (hosting mode: data server) |
| Architecture | Three-Tier (Presentation, Logic, Database) |
| Third Party | Nil, or list the integrations in scope |
| Browser Compatibility | Chrome, Firefox, Edge, Safari |
| Device Compatibility | Desktop, Laptop, Mobile, Tablet |
| Deployment & DevOps | Git version control, CI/CD pipeline |

### 6.9 Delivery & Milestone Payment Plans
Choose the plan by project size and replace the template's table accordingly.

#### Standard plan (49 days): schools, companies, hospitality, hospitals, trusts (template default)
| Activity | Deliverables | Payment |
| :--- | :--- | :--- |
| Day 1: Order confirmation | Work order | 50% advance |
| Day 2-3: Project plan preparation | Execution plan | - |
| Day 4-15: Templates | Design templates | - |
| Day 16-30: Development | - | - |
| Day 31-40: Coding | Website 1st trial for the client | - |
| Day 41-45: CR corrections | Website 2nd trial for the client | - |
| Day 46: Final review | Final trial for the client | 25% |
| Day 47: Beta hosting | Beta release at trial location | - |
| Day 48: Training | Staff training | - |
| Day 49: Go-live | Hosting to the actual domain; site ready for use | 25% balance |

#### Extended plan (60 days): banks, government, e-commerce, complex applications
| Milestone Activity | Deliverables | Payment |
| :--- | :--- | :--- |
| Day 1: Order Confirmation | Work Order Sign-off | 50% Advance |
| Day 2-3: Project Planning | Execution Plan & CRS | - |
| Day 4-15: Design Mockups | Home & Inner Page Wireframes | - |
| Day 16-35: Development | Interactive Prototype | - |
| Day 36-46: Coding & Integration | 1st Client Review Trial | - |
| Day 47-55: CR & Feedback | 2nd Client Review Trial | - |
| Day 56: Final Review | Final Client Approval Sign-off | 25% |
| Day 57-58: Beta Hosting & Training | Staff Training & Admin Handover | - |
| Day 60: Go-Live | Live Hosting & Final Handover | 25% Balance |

#### Basic accelerated plan (17 days): basic template-based sites
* Day 1: Order confirmation and work order (80% advance)
* Day 2-10: Template and coding
* Day 12-15: Final review and staff training
* Day 17: Go-live and final launch (20% balance)

### 6.10 Standard Terms and Conditions (mandatory 15 points, verbatim)

1. **Tax Applicability:** As per Govt. rules, GST (18%) applies to all finalized order values.
2. **Renewal Obligation:** Domain registration and web server hosting must be renewed annually at the end of each contract year.
3. **Price Revision & Market Conditions:** Rates reflect current market conditions and third-party provider tariffs (registrars/cloud hosters). Revisions mandated by regulatory or third-party bodies will apply directly.
4. **Content Ownership:** Sesame is strictly the technology developer; client holds full ownership and sole legal responsibility for all published website content.
5. **Access & Credentials:** If client mishandles DNS pointing, domain settings, or FTP/SSH credentials, Sesame is not liable for service downtime. Recovery assistance will be billed at standard hourly rates.
6. **Scope Creep & Change Requests:** Post-approval design or functional changes after live hosting will be charged at INR 750 – INR 1,000 per man-hour work.
7. **Storage Limits:** If server space consumption exceeds provisioned quota, client must purchase additional space or purge existing data.
8. **CRS Scope:** Modules are built strictly per approved Customer Requirement Specification (CRS). Deviations are billed under standard Man-Day/Man-Hour rates.
9. **Project Hold & Delays:** Detailed execution plans specify target dates. If project stays on hold due to client delays for >30 days without notice, advance paid is forfeited and project is halted. Resume requires fresh quote.
10. **Intellectual Property Rights (IPR):** Quoted rates cover executable licenses. Core code IPR remains with Sesame unless full source code ownership is purchased separately under written agreement.
11. **Source Code Modifications:** If client modifies purchased source code causing system breakdown, Sesame will not provide complimentary fixes; ongoing support will reference Sesame's baseline code repository only.
12. **Hosting Terms:** Server SLA and uptime terms mirror underlying infrastructure provider agreements.
13. **Data Entry Exclusion:** Quotes exclude manual content/data entry. Data entry remains client responsibility unless explicitly contracted.
14. **Study & Estimation Adjustments:** If detailed analysis uncovers requirements exceeding initial feasibility study, quotation will be revised accordingly.
15. **Final Ownership Transfer:** Full operational control and administrative ownership handovers occur only after all pending financial dues are cleared.

Do not edit, merge, reorder or drop these. Add sector-specific extras only as points 16 onwards, and only if the user asks.

### 6.11 Company Overview
Copy the template's Company Overview unchanged (divisions, achievements, client website lists by sector). Do not add, remove or invent client names.

### 6.12 Our Infrastructure & Contact Details (mandatory, verbatim, last page before the signature block)

```text
CALICUT: No: 1712, 7th Floor, HiLite Business Park, NH bypass Road, Calicut-14, Kerala, India | Cell: +91 9349138146
COCHIN: Room No: 33/1498, JKS 48, Kandekath Lane, Perumbotta Road, Elamakkara, Cochin-22
BANGALORE: A2 Ashirwad Layout, Horamavu Junction, Outer Ring Road, Bangalore
TRICHUR: No. 24, Pradhitha Road, Nehru Nagar P O, Kuriachira, Thrissur | Cell: +91 9349 11 89 84
```

Keep the template's layout (one block per office) and the "Authorized Signature / Company Seal" block.

---

## 7. Behaviour Rules

* Never fabricate prices, quote numbers, client details, deadlines or functional scope. Ask.
* Never leave another client's name, sector wording or school text in a document.
* Never alter the 15 terms, the contact block, the tagline or the metrics.
* If the user's instruction conflicts with this skill, follow the user and mention the deviation in one line.
* Keep replies short: state what was produced, list assumptions and anything that needs confirmation.

---

## 8. QA Checklist (all must pass before delivery)

- [ ] Logo visible in the header on every page (check the rendered PDF)
- [ ] Cover page shows correct client name, quote ref, date, validity, version
- [ ] Footer shows the correct client name (no "Nme" typo) and "Page X of Y"
- [ ] No `<...>` placeholders or school-specific text remain (unless the client is a school)
- [ ] Sections, modules, security scope, investment table and delivery plan match the client type
- [ ] Free-support period is the same in Investment, AMC and the delivery plan
- [ ] Table of Contents entries and page numbers match the final document
- [ ] 15 terms and the 4-office contact block are present and verbatim
- [ ] GST note present under every price table
- [ ] Both `.docx` and `.pdf` open and render correctly; no broken tables or orphan headings
