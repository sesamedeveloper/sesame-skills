# 📄 Sesame Official Documents Skill

**An agent skill that writes official Sesame Technologies proposals, covering letters and AMC quotes — branded, formatted, and adapted to the client.**

![Type](https://img.shields.io/badge/type-agent%20skill-blue)
![Output](https://img.shields.io/badge/output-DOCX%20%2B%20PDF-green)
![Client Types](https://img.shields.io/badge/client%20types-12-orange)
![Template](https://img.shields.io/badge/template-included-purple)

Tell it who the client is and what they need. It builds the document from the official Sesame template (logo, header, footer, cover page), rewrites the content for that client's sector, and hands back a `.docx` and a `.pdf` ready to send.

> 🧾 **This skill is a drafter, not a guesser.** It never invents prices, quote numbers, or client details. If something is missing, it asks.

---

## 📋 Table of Contents

- [What it does](#️-what-it-does)
- [Document types](#-document-types)
- [Client types covered](#-client-types-covered)
- [Hard rules](#-hard-rules)
- [Output](#-output)
- [Usage](#-usage)
- [Repo structure](#-repo-structure)
- [Installing](#-installing)
- [Core principle](#-core-principle)

---

## ⚙️ What it does

| Step | Description |
| :--- | :--- |
| **1. Identify** | Works out the document type (full proposal, covering letter, platform upgrade & AMC, AMC-only quote) and the client's sector. |
| **2. Collect** | Asks once for anything missing: client name and address, quote sequence number, development cost, number of API integrations, domain, languages. |
| **3. Build** | Copies the bundled template and keeps its logo, header, footer, cover page and styles intact. |
| **4. Adapt** | Rewrites the requirement, modules, security scope, pricing table and delivery plan for the client type. No school text is left in a bank proposal. |
| **5. Apply boilerplate** | Inserts the mandatory text verbatim: covering letter, executive summary, 15 terms and conditions, company overview, four-office contact block. |
| **6. Check** | Renders the PDF and runs a QA checklist: logo on every page, no leftover placeholders, TOC correct, consistent free-support period. |
| **7. Deliver** | Saves the Word and PDF files and summarises assumptions in chat. |

---

## 📑 Document types

| Type | Used for |
| :--- | :--- |
| **Type 1: Comprehensive Proposal** | New websites and applications. All 12 sections, from covering letter to contact details. |
| **Type 2: Covering Letter** | A single branded letter to accompany a quotation. |
| **Type 3: Platform Upgrade & AMC** | Upgrading an end-of-life platform and securing a maintenance contract. |
| **Type 4: AMC Quote / Official Notice** | AMC-only offers and general business letters. |

---

## 🎯 Client types covered

Each profile changes the requirement text, site modules, security scope, pricing package and delivery plan.

| Client type | Highlights |
| :--- | :--- |
| 🏫 **School / College** | Mandatory disclosure, admissions form, academic calendar, TC checking, circulars, gallery |
| 🏦 **Co-operative Bank / NBFC** | RBI alignment, CERT-In audit readiness, DICGC QR, bilingual toggle, rate calculators, branch/ATM locator, full 13-point security suite |
| 🏢 **Corporate / Business Group** | Products and services, clients, certifications, careers, enquiry forms, CMS |
| 🏥 **Hospital / Healthcare** | Departments, doctors directory, appointment requests, health packages, insurance info |
| 🏨 **Hotel / Resort / Hospitality** | Rooms and tariff, amenities, gallery, booking enquiry, reviews |
| 🛒 **E-commerce / Retail** | Catalogue, cart, payment gateway, orders, inventory, GST invoices |
| 🏗️ **Construction / Real Estate** | Project portfolio, floor plans, enquiry, RERA details |
| 🏛️ **Government / PSU** | Full security suite, accessibility, bilingual, tenders, RTI, GIGW alignment |
| 🤝 **Trust / NGO / Religious** | Activities, events, donations, volunteer registration |
| ✈️ **Travel & Tourism** | Packages, itineraries, enquiry and booking |
| 🧩 **Custom Web / Mobile App** | Module breakdown and user roles from the client's brief |
| 🔧 **Platform Upgrade & AMC** | Risk evaluation, staging, zero-downtime migration, free support window |

Anything else falls back to the closest profile, and assumed modules are marked as proposed.

---

## 🚫 Hard rules

**Never allowed**

- ❌ Inventing prices, quote numbers, client details, deadlines or functional scope
- ❌ Editing, merging, reordering or dropping the 15 terms and conditions
- ❌ Removing or resizing the Sesame logo
- ❌ Leaving another client's name or sector wording in a document
- ❌ Producing plain `.txt` or unbranded output

**Always required**

- ✅ Build from the bundled template
- ✅ Ask for missing inputs in one short message
- ✅ Keep the tagline, metrics and four-office contact block verbatim
- ✅ GST note under every price table
- ✅ Same free-support period in the Investment, AMC and delivery sections
- ✅ If the user's instruction conflicts with the skill, follow the user and say so in one line

---

## 📄 Output

Every run produces two files in `/mnt/user-data/outputs/`:

| File | Contents |
| :--- | :--- |
| `Sesame_<Client>_<DocType>_v1.0.docx` | Editable Word document with logo, header, footer, cover page and table of contents. |
| `Sesame_<Client>_<DocType>_v1.0.pdf` | PDF converted from the Word file, ready to send. |

Ask for only Word or only PDF and you get just that one.

**Cover page fields**

| Field | Format |
| :--- | :--- |
| Quote Ref. No | `ST/<Sequence>/<Day>/<Month>/<Year>` |
| Date issued | `DD/MM/YYYY` |
| Validity | 1 month from date issued |
| Version | `1.0` (`1.1` on revision) |

---

## 🚀 Usage

Ask your agent to prepare a proposal, quote, covering letter or AMC offer:

```text
Create a website proposal for ABC Co-operative Bank
Prepare a covering letter for St. Mary's School, Calicut
Make an AMC quote for XYZ Hospital, PHP upgrade included
Proposal for a hotel website, development cost INR 1,50,000
```

If the request is missing details, the skill asks for them before building. Name the client type and it uses that profile. Don't name it, and the skill picks the closest match.

---

## 📁 Repo structure

```text
.
├── README.md
└── skills/
    └── sesame-official-documents/
        ├── SKILL.md
        └── assets/
            └── Sesame_Proposal_Template.docx
```

---

## 📦 Installing

```bash
npx skills add <owner>/sesame-skills
```

Update later with `npx skills update`.

> 🔒 This skill contains Sesame's rate card, terms and template. Keep the repository **private** unless that content has been removed.

---

## 🎯 Core principle

**Accurate, on-brand documents, not fast guesses.** A proposal with a missing price is better than one with an invented price.

Identify the client → ask for what is missing → build on the template → adapt to the sector → apply the mandatory text → check the render → deliver.

---

Made with ❤️ at Sesame Technologies Pvt. Ltd.
