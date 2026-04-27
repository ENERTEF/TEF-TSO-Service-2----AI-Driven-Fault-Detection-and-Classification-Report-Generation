# AI-Driven Fault Detection and Classification Report Generation

**Service:** AI-Driven Fault Detection and Classification Report Generation  
**Author:** ELES  
**Version:** 1.0  
**Last Updated:** 4 Feb 2026  

---

# 1. Business Context & Definitions

This service focuses on the interpretation and advanced analysis of disturbance events recorded by protection relays within the transmission power system. The service generates reports with processed and interpreted fault records in order to relieve protection system experts in the detection, review, labeling, and classification of fault and non-fault events.

By systematically organizing and interpreting relay event data, the service provides continuous situational awareness of transmission system conditions, supports post-fault analysis, and enables consistent event classification across the network. The outputs are used to assess protection system performance, identify abnormal system behavior, improve fault response procedures, and support further development of protection schemes.

## Key Terms

- **Protection relay:** A device that performs protection functions in a transmission system by detecting abnormal conditions and issuing trip commands to control the circuit breaker.
- **COMTRADE file:** Standard file for the exchange of oscillographs and digital signals.

---

## 1.1 ELES (Protection Relays Owner) Context

The service is intended for ELES, the combined transmission and distribution system operator of the Republic of Slovenia. With a professional approach, know-how, and advanced technology, ELES has been providing safe, reliable, and uninterrupted electric power transmission throughout Slovenia and across its borders for 100 years. In doing so, the company connects people and ensures quality of life. ELES endeavors to strategically, responsibly, and sustainably plan, construct, and maintain Slovenia’s high-voltage transmission network at three voltage levels: 400 kV, 220 kV, and part of the 110 kV network.

ELES is also the owner of the protection relay infrastructure used for capturing COMTRADE records for this service. The protection infrastructure is primarily used to ensure the safe operation of primary protection equipment, but it also records a range of parameters and oscillography data that can be helpful during the analysis of fault or test events within transmission systems.

Safe operation of the transmission system is one of the main priorities, and protection relays are one of the key components that ensure this. In order to further improve the operation of protection relays, this service will enable automated analysis and report generation of different events and ensure that future events are detected and cleared even faster. The reliability of the transmission system is crucial for the normal functioning of everyday life.

---

# 2. Problem Statement

The primary goal is to provide a sufficiently mature automated generation of reports with processed and interpreted protection relay records. The reports include interpreted event datasets, classification results, performance indicators, and analysis results. It is particularly important to consider that these reports will be useful to experts, and therefore the service must provide professional, detailed, and reliable results.

---

# 3. Data Description

Data shared for this service will be agreed upon and aligned with the service provider. Due to data sensitivity, not all data can be disclosed. Only the data strictly necessary for the performance of the service will be shared, under specific pre-agreed conditions defined in a Non-Disclosure Agreement (NDA). The service provider may use the shared data exclusively for the development and implementation of this service and shall not disclose or provide it to any third parties. Certain shared datasets will also be anonymized where applicable.

---

## 3.1 Data Dictionary of COMTRADE Records

The following table summarises the available features of the protection relays COMTRADE dataset:

| Variable | Variable name | Type | Measurement unit | Description | Allowed values / Examples |
|---|---|---|---|---|---|
| Row ID | id | Numeric | - | Row ID | 24242 |
| Event ID | protel_event_id | Numeric | - | Event ID | 46000 |
| Location | location | String | - | Location description based on COMTRADE standard | RTP XXX / DV 110 kV YYY II / 7SA611 / 7SA611 |
| Trip Date and Time | trip_date_time | Timestamp | YYYY-MM-DD HH:MM:SS.ms | Trip start timestamp | 1970-01-01 00:00:00.000 |
| Trip End Time | trip_end_time | Timestamp | YYYY-MM-DD HH:MM:SS.ms | Trip event timestamp | 1970-01-01 00:00:00.000 |
| Fetched Time | fetched | Timestamp | YYYY-MM-DD HH:MM:SS.ms | Timestamp when was fetched | 1970-01-01 00:00:00.000 |
| Insert Date and Time | insert_date_time | Timestamp | YYYY-MM-DD HH:MM:SS.ms | Timestamp when was inserted | 1970-01-01 00:00:00.000 |
| Type | type_text | String | - | Type | NULL |
| Type ID | type_id | Numeric | - | Type ID | 28 |
| Trip Cause | trip_cause | String | - | Cause of trip event | Slabo vreme |
| Location Distance | location_distance | Numeric | km | Exact location of trip event | 16.7 |
| System | system_text | String | - | Protection system | SIEMENS SIPROTEC 4 |
| System ID | system_id | Numeric | - | System ID | 3 |
| Configuration File | file_osc_cfg | String | - | Encoded COMTRADE configuration file | RUxFUyAvIFJUUCBDRVJLTk8gICBEViAxMTAga1YgSURSSUpBICAgN1NBNjExXzdTQTYxMSwwMDAw ... |
| Data File | file_osc_dat | String | - | Encoded COMTRADE data file | MSwwLC0wMDAwMzIsLTAwMDAzMCwwMDAwNjEsMDAwMDQ1LDAwMDA0MCwtMDAwMDg1LDAwMDAwMCwtMDE1NDc4LC0 … |
| Information File | file_event_list | String | - | Encoded COMTRADE information file | RUxFUy9SVFAgSURSSUpBL0RWIDExMCBrViBBSkRPVlNDSU5BLzdTQTUxMTs3U0E1MTEgMy4yLDgvMi8xMiwxMQ0KMDMwMQ … |
| Classification | classification | Numeric | - | Classification ID | 3 |
| Deleted | deleted | Numeric | - | Deleted information | 1 |
| Succesful APV | APV_succesful | Numeric | - | Information if APV was successful | 1 |
| VF Response OK | VF_response_ok | Numeric | - | Information if VF response was ok | 0 |
| Protection Working OK | protection_working_ok | Numeric | - | Information if protection is working ok | 1 |
| Seen | seen | Numeric | - | Seen information | 1 |
| User Update Name | userUpdateName | String | - | Username of user who checked COMTRADE record | NLOJZE |
| Update Date and Time | updateDatetime | Timestamp | - | Update of record timestamp | 1970-01-01 00:00:00.000 |

---

## 3.2 Data Dictionary of Operational Log

The following table summarises the available features of the operational log dataset:

| Variable | Variable name | Type | Measurement unit | Description | Allowed values / Examples |
|---|---|---|---|---|---|
| Event ID | ID | Numeric | - | Unique ID of event | 12345 |
| Status | Stanje | Numeric | - | ID for unique status | 5 |
| Event Start | Zacetek_dogodka | Timestamp | YYYY-MM-DD HH:MM:SS.ms | Start timestamp of event | 1970-01-01 00:00:00.000 |
| Event End | Konec_dogodka | Timestamp | YYYY-MM-DD HH:MM:SS.ms | End timestamp of event | 1970-01-01 00:00:00.000 |
| Type of Asset 1 | Vrsta_naprave_1 | String | - | Type of the affected asset | energetske postaje |
| Type of Asset 2 | Vrsta_naprave_2 | String | - | Subtype of the affected asset | energetski transformator / 400 kV |
| Type of Asset 3 | Vrsta_naprave_3 | String | - | Subtype of the affected asset | ostala polja / 400 kV |
| Asset ID | ID_naprave | Numeric | - | ID of asset | 1000 |
| CIM ID | CIM_ID | String | - | Common Information Model ID | _00000000000000000000000000000000 |
| Asset | Naprava | String | - | Substation bay information | DV 110 kV XXX-YYY |
| Microlocation | Mikrolokacija | String | - | Detailed information about location | Kompenzacijska naprava |
| Maintenance Area | Obmocje_vzdrzevanja | String | - | Maintenance area team | CVZ XX |
| Owner | Lastnik | String | - | Owner of affected asset | ELES |
| Event Type ID 1 | ID_vrsta_dogodka1 | Numeric | - | Event type ID | 2 |
| Event Type 1 | Vrsta_dogodka_1 | String | - | Event type description | načrtovani |
| Event Type ID 2 | ID_vrsta_dogodka2 | Numeric | - | Event subtype ID | 3 |
| Event Type 2 | Vrsta_dogodka_2 | String | - | Event subtype description | planski izklop |
| Event Type ID 3 | ID_vrsta_dogodka3 | Numeric | - | Event subtype ID | 33 |
| Event Type 3 | Vrsta_dogodka_3 | String | - | Event subtype description | planski izklop |
| Event Cause ID 1 | ID_vzrok_dogodka1 | Numeric | - | Event cause ID | 40 |
| Event Cause 1 | Vrsta_vzroka_1 | String | - | Event cause description | lastni |
| Event Cause ID 2 | ID_vzrok_dogodka2 | Numeric | - | Event sub-cause ID | 44 |
| Event Cause 2 | Vrsta_vzroka_2 | String | - | Event sub-cause description | osnovni |
| Event Cause ID 3 | ID_vzrok_dogodka3 | Numeric | - | Event sub-cause ID | 49 |
| Event Cause 3 | Vrsta_vzroka_3 | String | - | Event sub-cause description | vzdrževanje |
| Event Cause ID 4 | ID_vzrok_dogodka4 | Numeric | - | Event sub-cause ID | 3349 |
| Event Cause 4 | Vrsta_vzroka_4 | String | - | Event sub-cause description | revizija |
| Cause Description | Opis_vzroka | String | - | Cause additional description | AKZ stebrov |
| Assets | Naprave | String | - | Affected assets | DV 110 kV XXX-YYY;RTP ZZZ DV polje 110 kV WWW; |
| Operating status before event | Obrt_stanje_pred_dogodkom | String | - | Operating status description before event | normalno stanje |
| Operating status after event | Obrt_stanje_po_dogodku | String | - | Operating status description after event | normalno stanje |
| Weather | Vreme | String | - | Weather information | dež |
| Event Connection | Povezava_dogodka | String | - | If event is connected with other? | Da |
| Event Connection 1 | Povezava_dogodka_1 | Numeric | - | Connected events ID | 24869 |
| Event Consequence | Posledica_dogodka | String | - | Event consequence description | ni posledic |
| Trip Start | Zacetek_prekinitve | Timestamp | YYYY-MM-DD HH:MM:SS.ms | Timestamp of the start of trip event | 1970-01-01 00:00:00.000 |
| Trip End | Konec_prekinitve | Timestamp | YYYY-MM-DD HH:MM:SS.ms | Timestamp of the end of trip event | 1970-01-01 00:00:00.000 |
| Number of Affected Customers | St_prizadetih_odjemalcev | Numeric | - | Number of affected customers during trip event | 10000 |
| Planned Start | Nacrtovani_zacetek | String | - | Planned start | NULL |
| Planned End | Nacrtovani_konec | String | - | Planned end | NULL |
| Upon Request | Na_zahtevo | String | - | Upon request of | NULL |
| Approved | Odobren | String | - | Approved | NULL |
| Grounded | Ozemljen | String | - | Grounded | NULL |
| Work Coordinator | Koordinator_del | String | - | Work Coordinator | NULL |
| Description | Opis | String | - | Additional description of event | AKZ stebrov |

---

# 4. Analytics, Scope & Update Frequency

## Temporal Scope

Analytics are computed on fault or other event records that are around one or two seconds long. Usually fault events are one or two periods long, approximately 50–100 ms, but protection relays also record some time before and after the event.

## Update Frequency

Results are refreshed or reports are generated after each event within the protection relay.

## Output Format

For each protection relay record, the service provides oscillography, parameters, and metadata, including:

- System location
- Relay information
- Event timestamp
- Analog and digital signal flow
- Classification of events
- Interconnection with other records that collectively represent or constitute a single real fault event

---

# 5. Evaluation Protocols & Metrics

Evaluation is required to ensure that the service report meets the requirements of protection system experts who will use the report findings. The evaluation is primarily focused on the quality of the report, where it is important to assess:

- the correctness of recorded event interpretation and classification
- the quality of oscillograms
- the usability of data

---

## 5.1 Data Usage & Analytical Protocol

- The service shall process every new recorded event received on the platform from protection relays.
- The service shall be capable of analysing input data of varying size, as event records are not always uniform.
- Complete event records shall be analysed in their entirety, as typical protection relay recordings span approximately one to two seconds.
- All analytical outputs shall be fully reproducible, based on clearly documented model versions, configuration parameters, and input datasets.

---

## 5.2 Data Gaps and Exceptions

- Service should be able to distinguish between real fault events and testing.
- Data from testing are not directly relevant for fault events interpretation.
- Periods with missing or invalid data in fault event records shall be excluded from analysis.

---

## 5.3 Service Evaluation Metrics & KPIs

The service shall be evaluated using the following quantitative metrics:

| Metric | Description |
|---|---|
| Classification accuracy | Measures whether the AI model correctly detects and classifies grid faults based on disturbance recordings. Measured with true and false classifications. |
| Response time for events | Percentage time required for the system to detect, classify, and present event information to experts. Measured by average response times with timestamping response times. |
| Reduction in required time for analysis (%) | Measures efficiency improvement compared to traditional manual fault analysis. KPI = (manual_time – tool_time) / manual_time × 100% |

---

# 6. Deliverables & Submissions

The selected provider shall deliver three (3) reports, aligned with the lifecycle of the service, together with the required technical specifications and deployment artefacts.

---

## 6.1 Deliverable Reports

Three delivery reports should be submitted for this service.

### 1. Pre-Service Deliverable – Service Design & Setup Report

Submitted prior to service start, this report shall describe the proposed analytical approach, calculation methodology, baseline definition, report format or template, data requirements, system architecture, security measures, and integration plan. It shall also define the operational schedule and procedures for service execution.

### 2. Intermediate Deliverable – Interim Performance & Operations Report

Submitted at an agreed midpoint of the service period, this report shall summarize reports generation to date, data coverage, preliminary analytical results, and performance against the defined metrics and KPIs. Examples of reports should also be provided. Any issues, adaptations, or refinements to the methodology shall be documented.

### 3. Final Deliverable – Final Evaluation & Recommendations Report

Submitted at the end of the service period, this report shall present analyzed final performance results, process insights, identified inefficiencies, prioritized improvement or retrofit recommendations, and lessons learned. The report should also include guidance for future service continuation or scaling.

---

## 6.2 Technical Specifications & Submissions

**Service Interface Documentation:** Full documentation of APIs, platform instructions, data formats, authentication, and access controls.

**Deployment Artefacts:** The provider shall specify the deployment approach.

**Configuration, Versioning & Handover:** Documentation of configuration parameters, model and data versioning, and operational handover procedures shall be provided. The algorithm or platform used for report generation shall then be formally handed over to the customer.

**Security & Data Protection Documentation:** Description of data handling, cyber security, access control, and compliance with applicable data protection requirements. The requirements shall be agreed with the service provider prior to the commencement of service development.

---

# 7. Notes

The above specification is not final. Both parties - the service provider and the customer may, prior to the commencement of cooperation or during the development phase, modify certain parts of it if such changes prove necessary for the proper performance of the service.
