graph TB
    Patient -->|Books / reschedules / cancels appointment| SchedulingCore[Scheduling Core Engine]
    ClinicStaff[Clinic Staff] -->|Manages bookings on behalf of patients| SchedulingCore
    HealthcareProvider[Healthcare Provider] -->|Sets availability, views schedule| SchedulingCore
    SystemAdministrator[System Administrator] -->|Configures system, manages users & roles| SchedulingCore

    SchedulingCore -->|Emits confirmation / reminder / late-change events| NotificationService[Notification Service]
    NotificationService -->|SMS, Email, or Push notification| Patient

    SchedulingCore -->|Reads / writes patient & visit records| EHR[EHR / Patient Records System]
    SchedulingCore -->|Syncs provider availability| ProviderCalendar[Provider Calendar System]
    SchedulingCore -->|Processes co-pay / rescheduling fee| PaymentGateway[Payment Gateway]
