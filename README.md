Hostel Management System
Overview
The Hostel Management System is a simple application that implements a filter-based processing system for handling hostel applications. It uses the Observer pattern to notify interested parties (such as the Hostel Management and Applicants) about the application's status at various stages of the process. The system checks for eligibility, payment status, and service availability (AC requirements) using the Pipe and Filter design pattern.

Components
1. Observer Pattern
The Observer pattern is used to notify different parties (e.g., hostel management and applicants) whenever there is an update in the applicant's status.
HostelManagementObserver: Notified when an applicant’s status changes.
ApplicantStatusObserver: Notified about the applicant’s status update.
2. Applicant Class
Represents an individual applicant with attributes such as name, age, payment amount, payment status, and AC requirement.
It provides getter methods to retrieve these attributes.
3. Filter Pattern
The Filter interface allows the system to process applicants through different checks.
EligibilityFilter: Checks if the applicant meets the age criteria (18 to 30 years).
PaymentFilter: Verifies if the applicant has paid the required amount (5000 or more).
ServiceAvailabilityFilter: Verifies if the required service (AC) is available.
4. Pipe Class
Manages the list of filters and observers.
Processes an applicant through the added filters, and notifies observers about the status of the process.
If the applicant passes all filters, the process is successful; otherwise, it fails, and the applicant is not approved.
5. Main Class (HostelSystem)
The main class that brings everything together.
Creates an applicant, adds filters, adds observers, and processes the applicant.
How it Works
The system creates an Applicant with specified details (name, age, payment amount, payment status, and AC requirement).
A Pipe is created, and filters are added to process the applicant:
Eligibility: Checks if the applicant’s age is within the acceptable range (18-30 years).
Payment: Ensures the applicant has paid the required amount.
Service Availability: Checks if the requested service (AC) is available.
Observers (Hostel Management and Applicant Status) are added to listen for updates on the applicant's status.
The process method of the Pipe class runs the filters on the applicant:
If all filters are passed, the applicant is approved.
If any filter fails, the applicant is rejected, and the observers are notified.
Updates are sent to the observers, which will print messages based on the applicant's status.
