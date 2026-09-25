# Milestone 1

## Requirements and Analysis

**Asset Centric Maintenance Management System for Medical Device Field Service**

## 1. Project Context and Problem

Our client is Specialized Biomedical Services, a small biomedical service company operated by Charlotte Shaw. The company services medical equipment for private clinics and other medical facilities. The work includes scheduled preventive maintenance, inspections, repairs and maintaining the service records that clinics may later need for accreditation or auditing.

The main problem we identified is not that Charlotte lacks software completely. She already uses Jobber for scheduling and parts of the service workflow, while other information is stored through Word files, Excel spreadsheets, inspection forms and PDF documents. The problem is that these systems do not create one connected history around the actual medical device. Information about the same equipment may therefore exist in several different places, and finding something as simple as the previous service history of one device can require searching through multiple files. The original client proposal describes the same issue, especially the difficulty of answering when a particular device was last inspected, what was found and when the next inspection is due. 00_ALL_PROPOSALS(4)

After meeting Charlotte twice and seeing how she currently performs an inspection, our understanding of the project became much clearer. The system needs to be asset centric, meaning that the medical device remains the main reference point throughout its life. The clinic, technician, inspection form, maintenance schedule and even the location of the device may change over time, but the asset itself needs to keep one continuous history. The purpose of our system is therefore to bring the information that is currently scattered between different systems into one web based application where the equipment, inspection history, maintenance schedule and service information are connected and searchable.

A simple way we currently understand the workflow is:

Clinic → Asset → PM Schedule or Work Order → Correct Checklist → Inspection or Repair → Result and Service Information → Asset History → Search or Reporting

This flow became much more concrete during the second client meeting, where Charlotte demonstrated the current inspection process and explained how she uses the previous inventory, manually selects the correct checklist and records information again because Jobber does not maintain the complete asset record she needs. 2nd meet with charlotte at tru … 2nd meet with charlotte at tru …

## 2. Requirements Elicitation and Validation

Our requirements were not taken only from the initial project proposal. We treated the proposal as the starting baseline and then used our client meetings to clarify how the workflow actually operates.

The first meeting helped us understand the business, the types of maintenance performed, the existing use of Jobber and the need for a searchable history for every medical device. Charlotte also explained that she would like to search by information such as asset number, serial number, customer, site or model and immediately see previous inspections, repairs and other information connected with that equipment. first meet with Charlotte, Camp…

The second meeting was more detailed because Charlotte demonstrated a realistic service visit using three example devices. This allowed us to validate requirements around asset fields, inspection checklists, PM frequency, repair work orders, technician assignment, parts, test equipment, calibration records, service manuals and different inspection outcomes. For example, an inspection is not always simply pass or fail. A result can also be conditional and may need additional notes or measurements. Charlotte also explained that PM intervals vary between different devices and situations, so the interval must be stored with the asset and remain editable. 2nd meet with charlotte at tru …

This second walkthrough was important because it moved our understanding away from designing a generic job tracking application and toward the actual domain requirements of biomedical service work.

## 3. Stakeholder Analysis

The primary stakeholder is Charlotte, since she owns the business and currently performs much of the service and inspection work herself. Her main needs are reliable asset history, easier preparation for service visits, maintenance scheduling, faster retrieval of previous information and reduced dependence on manually remembering where information is stored.

A second stakeholder group is the field technician. Even though Charlotte currently performs much of this work, the system must also support other technicians. A technician needs quick access to the assigned work, equipment information, the correct inspection checklist, historical information, service manuals and any previous issues while working in the field.

The clinics and medical facilities are indirect users of the information produced by the system. They do not necessarily require full system access in the current scope, but they depend on SBS to maintain accurate and traceable service information for their medical equipment.

There is also an accreditation and audit context. An accreditation body is not expected to become a direct system user, but the records produced by the system may later be used as evidence. This creates stronger requirements around traceability, historical accuracy and retaining completed inspection records.

## 4. Functional Requirements

Based on the proposal and both client meetings, we currently consider the following to be the main functional requirements.

### FR01 — User Access The system shall allow authorized users to sign in and access the information and functions available to their role.

### FR02 — Clinic and Location Management The system shall maintain clinic or site records and associate assets with the clinic or location where they are currently used.

### FR03 — Asset Register The system shall maintain a persistent record for every medical device. The record should include information such as asset number, manufacturer, model, serial number, manufacture date, certification information, Health Canada licence information where applicable, maintenance frequency and other equipment specific information.

### FR04 — Asset Lifecycle The system shall support asset states such as active and retired while retaining the historical record of retired assets.

### FR05 — Asset Search The system shall allow users to search for equipment using information such as asset number, serial number, clinic, manufacturer or model.

### FR06 — Service History The system shall maintain a chronological service history for each asset, including inspections, preventive maintenance, repairs, findings and other relevant service information.

### FR07 — Preventive Maintenance Scheduling The system shall maintain a configurable PM interval for each asset and identify when the next service is approaching or overdue.

### FR08 — Work Orders The system shall support scheduled preventive maintenance and unscheduled demand maintenance. Work may be assigned to a technician or remain available for an authorized technician to claim.

### FR09 — Inspection Checklist Association The system shall associate the appropriate inspection checklist with the relevant equipment type so that the technician does not need to manually locate and attach the correct checklist every time.

### FR10 — Dynamic Inspection Forms Inspection forms shall support conditional sections. For example, if a test is marked Not Applicable, questions that are no longer relevant should not remain visible unnecessarily.

### FR11 — Inspection Results The system shall support outcomes such as Pass, Fail and Conditional and shall allow notes, reasons and measured values where required.

### FR12 — Inspection Traceability Every completed inspection shall record the asset, person who performed the inspection, inspection result, date and next PM information.

### FR13 — Calibration Equipment The system shall record test and calibration equipment used during relevant inspections, including information such as model, serial number, calibration date and calibration due date. Charlotte explained that this information may be reviewed during accreditation, so the relationship between the inspection and calibrated test equipment needs to be preserved. 2nd meet with charlotte at tru …

### FR14 — Supporting Information The system should allow relevant photos, notes, service manuals or links to manuals to be associated with an asset or service record.

### FR15 — Information Retrieval and Export The system shall allow useful records to be retrieved or exported, including the inventory for a clinic, the complete history of an asset and service or work order information.

The original project proposal describes five core capabilities that support this requirement set: the equipment register, service history, preventive maintenance scheduling, configurable inspection forms and service records with an audit trail. 00_ALL_PROPOSALS(4)

## 5. Nonfunctional Requirements

The client proposal and the meetings also identified several requirements that are not individual features but still affect the way the system must be designed.

### NFR01 — Usability The application should be simple enough to use while working in a clinic or mechanical room, including situations where the technician may be operating the device with one hand.

### NFR02 — Mobile Accessibility The application shall be web based and usable on mobile phones, tablets and normal computers.

### NFR03 — Security and Authorization Only authorized users should be able to access the company's system and data. Different permissions may be needed for different user roles.

### NFR04 — Data Integrity Completed service and inspection records must not simply be edited or deleted. If a completed record needs correction, the original should remain in the history and a new linked record should supersede it.

### NFR05 — Historical Consistency Inspection forms need version control. If a checklist changes later, an older inspection should continue to display using the version that was originally completed.

### NFR06 — Auditability The system should maintain enough information to determine who performed an action and when it occurred.

### NFR07 — Canadian Data Residency Production data should be hosted in Canada because SBS maintains service information on behalf of Canadian clinics.

### NFR08 — Data Protection Information should be encrypted while being transmitted and while stored.

### NFR09 — Data Portability The client should be able to export the information held in the system.

These constraints are specifically identified in the original project proposal and affect the future architecture, even though architecture will be addressed in more detail during Milestone 2. 00_ALL_PROPOSALS(4)

## 6. Scope and Explicit Exclusions

One of the main things we want to avoid is turning the project into a replacement for every piece of software SBS currently uses. The course has a limited development period, so we believe the project should first deliver the asset and maintenance core properly.

The current core scope includes clinic and asset management, service history, preventive maintenance scheduling, work orders, inspection workflow, checklist association, search, authentication, auditability and useful export of service information.

Some features would be valuable but should only be attempted after the core is working. These include QR or barcode identification, OCR assisted asset entry, stronger offline synchronization, a client portal and other advanced automation. The original proposal also describes QR tagging, document attachments and a read only client portal as additions to consider only if the team has sufficient capacity. 00_ALL_PROPOSALS(4)

The current explicit exclusions are accounting, payroll, full invoicing functionality, QuickBooks integration and rebuilding the complete Jobber system. Jobber and QuickBooks were included in the proposal as context for the current business workflow rather than required integrations. 00_ALL_PROPOSALS(4)

There is one reporting boundary that still needs to be stated carefully. Charlotte explained during the first meeting that the system should provide the organized information and allow useful reports or exports to be pulled from the database, but automatically creating the final customer certification document is not currently the main focus of this project. first meet with Charlotte, Camp… We would like to confirm the exact boundary with the client and supervisor so that the requirement is not interpreted differently later.

## 7. Risk Register

| Risk | Likelihood | Impact | Response |
| --- | --- | --- | --- |
| Project scope grows beyond what can be completed in one term | High | High | Separate core, stretch and excluded features and validate the boundary early |
| Requirements remain unclear in specialized biomedical areas | Medium | High | Use weekly client meetings and validate uncertain requirements before implementation |
| Checklist structure becomes more complicated than expected | Medium | High | Model one or two real checklist types before attempting the complete checklist set |
| Historical data contains inconsistent formatting | High | Medium | Define validation rules and test importing with the anonymized client dataset |
| Mobile workflow becomes difficult to use in the field | Medium | High | Use mobile first interface prototypes and obtain client feedback early |
| Confidential or sensitive business information is exposed | Low to Medium | High | Use anonymized development data and restrict access to proprietary material |
| Team members develop isolated parts that do not integrate well | Medium | High | Agree interfaces early, review changes regularly and keep all work visible through GitHub |
| Architecture is designed before requirements are stable | Medium | High | Establish and validate the requirements baseline before committing to the data model and architecture |

## 8. Open Decisions and Next Steps

Although the core direction is now clear, some requirements still need further validation. The most important remaining items are the complete asset field list, the way modules or subcomponents with their own serial numbers should relate to a parent asset, the exact checklist structure, the final boundary for reporting, the expected notification behaviour and whether offline capability should remain a future enhancement.

Charlotte specifically left the question of how modules and subcomponents should be represented for the team to investigate, since some modules may move between machines while having their own serial number. 2nd meet with charlotte at tru …

Our immediate next step is therefore to finish the requirement baseline, confirm the remaining questions with Charlotte and establish a clear scope before moving into Milestone 2. Once the requirements are stable, the next phase can focus on the system architecture, database model, interface design and technology choices without forcing the team to redesign major parts later.
