# Foreign Ownership in Indonesian Infrastructure

An asset-first open-source intelligence (OSINT) mapping of corporate ownership chains, intermediate holding jurisdictions, and foreign investment links across five major Indonesian infrastructure assets.

- **Author:** Darrell Manua
- **Methodology:** Asset-First Open-Source Intelligence (OSINT) Mapping
- **Data Cutoff:** October 10, 2026 (`2026-10-10`)
- **Full Report:** [`report/Foreign_Ownership_Indonesian_Infrastructure.pdf`](report/Foreign_Ownership_Indonesian_Infrastructure.pdf)
- **Structured Dataset:** [`data/`](data/) (see [`DATA_DICTIONARY.md`](DATA_DICTIONARY.md))

---

## Executive Summary

Headline foreign direct investment (FDI) statistics rarely reveal the beneficial owners sitting behind multi-tiered offshore holding vehicles. This repository traces five Indonesian infrastructure assets backward from their physical facilities and local operating companies to their direct shareholders and ultimate upstream parents, explicitly distinguishing confirmed registry filings from reconstructed equity figures and unverified gaps.

| Asset (Location) | Sector | Operating Entity | Indonesian Owners | Foreign Ultimate Owners | Holding Jurisdictions |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **NeutraDC Nxera** (Batam) | Data Centre | PT Teknologi Data Infrastruktur (`E013`) | Telkom Indonesia (State), Medco Group (Private) | Temasek / Singtel (SG), KKR (US) | Indonesia, Singapore |
| **BW Digital NDP1** (Batam) | Data Centre | PT BWDIGITAL INFRA INDONESIA (`E017`) *(unverified link)* | None identified | BW Group *(ultimate owner unverified)* | Indonesia, Singapore, Bermuda |
| **Jawa Satu Power** (Karawang) | Power Plant | PT Jawa Satu Power (`E026`) | Pertamina (State) | Marubeni (JP), Sojitz (JP) | Indonesia, Netherlands, Japan |
| **Tower Bersama Portfolio** (National) | Telecom Towers | PT Tower Bersama Infrastructure Tbk (`E042`) | Saratoga Group, Provident Capital | Macquarie (AU) | Indonesia, Singapore, Australia |
| **Trans-Java Toll Road** (Java) | Toll Road | PT Jasamarga Transjawa Tol (`E063`) | Jasa Marga (State), Nusantara Infrastructure | GIC (SG), First Pacific / MPIC (HK/PH), Japanese Consortium (JP) | Indonesia, Singapore, Philippines, HK, Japan |

---

## Key Cross-Asset Patterns

1. **Offshore Hub Differentiation:** Intermediate holding jurisdictions serve distinct structural roles depending on investor type. **Singapore** functions primarily as a multi-party joint-venture and co-investment hub—hosting *Bersama Digital Infrastructure Asia Pte. Ltd.* (Tower Bersama), *Nxera Investment Holdings Pte. Ltd.* (NeutraDC Nxera), and *Warrington Investment Pte. Ltd.* (Trans-Java Toll Road). By contrast, the **Netherlands** functions as a single-parent holding jurisdiction for Japanese general trading houses, with both *Marubeni Corporation* (*Garuda Power Holdings B.V.*) and *Sojitz Corporation* (*Sojitz Global Investment B.V.*) routing their Jawa Satu Power stakes through Dutch B.V. entities.
2. **State-to-State Co-Investment:** Indonesian state-owned enterprises (*Telkom*, *Pertamina*, *Jasa Marga*) frequently co-invest alongside foreign sovereign wealth funds and state-linked investment vehicles—including Singapore's *Temasek* (via Singtel) and *GIC* (via Warrington Investment), the Philippine *Government Service Insurance System (GSIS)* (via MPIC), and a Japanese government-backed infrastructure consortium (via PT Margautama Nusantara).
3. **Layered Cross-Holdings vs. Headline Stakes:** Direct shareholding percentages at the operating-entity level can understate an investor's total economic or governance footprint when co-investors overlap across tiers—such as *GIC* holding 10.47% directly in JTT while also holding an indirect interest via *PT Margautama Nusantara* (4.4%), or *PT Wahana Anugerah Sejahtera* holding 9.37% directly in Tower Bersama alongside its stake in the 81.29% controlling vehicle *Bersama Digital Infrastructure Asia Pte. Ltd.*

---

## Repository Structure

```text
├── README.md                  # Project overview, master summary table, and key findings
├── DATA_DICTIONARY.md         # Relational schema definitions, key conventions, and date standards
├── report/
│   └── Foreign_Ownership_Indonesian_Infrastructure.pdf
└── data/
    ├── assets.csv             # 5 infrastructure assets and local operating entities
    ├── entities.csv           # 63 corporate vehicles, holding companies, and state institutions
    ├── ownership.csv          # 13 direct asset-level shareholding links
    └── sources.csv            # 49 primary filings, registry extracts, and disclosures
```

---

## Verification & Confidence Tiers

- **High / Confirmed:** Direct shareholding links and upstream parents verified across primary corporate and regulatory disclosures.
- **Reconstructed:** Exact equity percentages derived algebraically from sequential share issuance records (subject to minor rounding discrepancies).
- **Partial / Unverified:** Upstream corporate chain documented, but direct local equity link or ultimate beneficial owner remains unconfirmed in open sources.

---

## How to Cite

> Manua, Darrell (2026). *Foreign Ownership in Indonesian Infrastructure: An Asset-First OSINT Mapping*. GitHub Repository. Data cutoff: October 10, 2026.