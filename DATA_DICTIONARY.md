\# Data Dictionary \& Relational Schema



All datasets in `/data` are UTF-8 encoded CSV files normalized into four relational tables with a research cutoff date of \*\*2026-10-10\*\*.



\## Key Conventions \& Standards

\- \*\*Primary \& Foreign Keys:\*\*

&#x20; - `A###` (`assets.csv`) — Physical infrastructure assets or asset portfolios (`A001`–`A005`).

&#x20; - `E###` (`entities.csv`) — Corporate entities, operating companies, holding vehicles, sovereign funds, and state institutions (`E001`–`E063`).

&#x20; - `O###` (`ownership.csv`) — Direct asset-level ownership edges (`O001`–`O013`).

&#x20; - `S###` (`sources.csv`) — Primary corporate filings, registry records, and open-source disclosures (`S001`–`S049`).

\- \*\*Date Format:\*\* All exact dates follow \*\*ISO 8601 (`YYYY-MM-DD`)\*\* stored as plain text. Where an exact filing date was unavailable, year-only dates (`YYYY`) or access dates are recorded alongside an explicit `date\_type` classification column.

\- \*\*Null Values:\*\* Blank cells represent unverified, undisclosed, or not-applicable values rather than placeholder strings (`N/A` or `TBD`).



\---



\## 1. `assets.csv` (5 rows)

Physical infrastructure facilities and asset portfolios examined in the study.



| Column | Type | Description |

| :--- | :--- | :--- |

| `asset\_id` | String | Primary key (`A001`–`A005`). |

| `asset\_name` | String | Project or facility name (e.g., `NeutraDC Nxera`, `Jawa Satu Power`). |

| `sector` | String | Infrastructure subsector (`Data Centre`, `Power Plant`, `Telcom Tower`, `Toll Road and Facilities`). |

| `location` | String | Geographic location in Indonesia. |

| `operator` | String | Operational manager or project sponsor. |

| `operating\_entity` | String | Legal name of the Indonesian entity holding or operating the asset. |

| `operating\_entity\_id` | String | Foreign key referencing `entities.csv` (`E###`). |

| `status` | String | Operational or development status (`Operating`, `Ongoing`). |

| `capacity` | String | Physical capacity or scale (e.g., MW, telecom site count, toll road length). |

| `foreign\_link` | String | Summary of confirmed or unverified foreign equity participation. |

| `foreign\_country` | String | Comma-delimited jurisdictions of confirmed foreign upstream parents/investors. |

| `source\_id` | String | Foreign key(s) referencing `sources.csv` (`S###`, comma-delimited). |



\---



\## 2. `entities.csv` (63 rows)

Corporate vehicles, operating companies, holding companies, and state institutions across the ownership chains.



| Column | Type | Description |

| :--- | :--- | :--- |

| `entity\_id` | String | Primary key (`E001`–`E063`). |

| `legal\_name` | String | Registered legal name of the entity. |

| `country` | String | Jurisdiction of incorporation. |

| `entity\_type` | String | Structural role (`Independent`, `Subsidiary`, etc.). |

| `parent\_entity` | String | Direct upstream parent entity ID (`E###`) or `-` if top-level/independent. |

| `shareholders` | String | Summary of known upstream shareholders and equity percentages. |

| `source\_id` | String | Foreign key(s) referencing `sources.csv` (`S###`, comma-delimited). |

| `notes` | String | Analytical caveats, intermediate holding notes, or verification gaps. |

| `as\_of\_date` | String | Standardized verification date (`YYYY-MM-DD`); blank if inferred, circumstantial, or unspecified. |

| `date\_type` | String | Precision/nature of `as\_of\_date` (`Filing / Effective Date`, `Accessed Date`, `Inferred`, `Circumstantial`, `Unspecified`). |



\---



\## 3. `ownership.csv` (13 rows)

Direct ownership links mapping each asset-operating entity (`E###`) to its direct shareholders (`E###`). \*(Multi-tier upstream corporate chains are modeled inside `entities.csv`.)\*



| Column | Type | Description |

| :--- | :--- | :--- |

| `ownership\_id` | String | Primary key (`O001`–`O013`). |

| `target\_asset` | String | Legal name of the target operating entity holding the asset. |

| `target\_entity\_id` | String | Foreign key referencing the target operating entity in `entities.csv` (`E###`). |

| `owner\_entity` | String | Legal name of the direct shareholder (`TBD / not publicly verified` if unconfirmed). |

| `owner\_entity\_id` | String | Foreign key referencing the direct owner in `entities.csv` (`E###`); blank if unverified. |

| `stake\_pct` | Float | Direct equity percentage (`0–100`); blank if undisclosed or unverified. |

| `ownership\_type` | String | Nature of shareholding (`Direct Shareholder`, `TBD / not publicly verified`). |

| `country` | String | Jurisdiction of incorporation of the `owner\_entity`. |

| `source\_id` | String | Foreign key(s) referencing `sources.csv` (`S###`, comma-delimited). |



\---



\## 4. `sources.csv` (49 rows)

Primary corporate filings, regulatory disclosures, and open-source records supporting each claim.



| Column | Type | Description |

| :--- | :--- | :--- |

| `source\_id` | String | Primary key (`S001`–`S049`). |

| `source\_title` | String | Title of the filing, annual report, registry extract, or announcement. |

| `publisher` | String | Issuing company, stock exchange, regulator, or corporate registry. |

| `source\_type` | String | Document category (e.g., `Annual Report`, `Information Disclosure`, `Company Announcement`). |

| `source\_tier` | String | Evidentiary reliability tier (`Primary`, `Secondary`). |

| `url` | String | Direct URL or archive reference. |

| `claims\_supported` | String | Summary of ownership figures, entity links, or asset specifications verified by the source. |

| `publication\_date` | String | Standardized disclosure or access date (`YYYY-MM-DD`, or `YYYY` where only year is published). |

| `date\_type` | String | Precision/nature of `publication\_date` (`Filing / Effective Date`, `Accessed Date`, `Year Only`). |

