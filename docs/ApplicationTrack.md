# Application Tracking Agent

## Overview

The Application Tracking Agent manages and monitors a user's job applications throughout the hiring lifecycle.

It keeps application records organized, tracks status changes, stores important dates, and provides a clear view of the user's active and completed applications.

## Responsibilities

- Create and maintain application records.
- Track application status.
- Record application dates and deadlines.
- Associate applications with specific job opportunities.
- Store company and position information.
- Track interview stages.
- Record recruiter and hiring-manager information when provided.
- Track follow-up actions.
- Detect stale applications.
- Provide application history and current status.

## Application Status

Supported statuses may include:

- Saved
- Preparing
- Applied
- Application Viewed
- Recruiter Contacted
- Screening
- Interview
- Technical Interview
- Final Interview
- Offer
- Accepted
- Rejected
- Withdrawn
- Closed

The status model should remain configurable so additional hiring stages can be introduced later.

## Application Record

```ts
interface Application {
  id: string;
  jobId?: string;
  company: string;
  jobTitle: string;
  jobUrl?: string;
  status: ApplicationStatus;
  appliedAt?: string;
  updatedAt: string;
  deadline?: string;
  source?: string;
  notes?: string;
}
```

### Part 2 — Tracking Workflow & Data Model

# Application Tracking Workflow

## Workflow

```text
Job Opportunity
      │
      ▼
Save Application
      │
      ▼
Prepare Application
      │
      ▼
Submit Application
      │
      ▼
Track Status
      │
      ├──► Recruiter Contact
      │
      ├──► Screening
      │
      ├──► Interviews
      │
      ├──► Offer
      │
      └──► Rejection / Withdrawal
```


# Application Tracking — Analytics & Extensions

## Dashboard Information

The agent should provide an overview containing:

- Total applications
- Active applications
- Applications by status
- Upcoming interviews
- Pending follow-ups
- Recent status changes
- Offers received
- Rejected applications
- Withdrawn applications

## Notifications

The system may notify users about:

- Upcoming interviews
- Application deadlines
- Scheduled follow-ups
- Long-running applications
- Status changes
- Recruiter responses
- Required user actions

Notifications should be configurable by the user.

## Analytics

The system may calculate descriptive metrics such as:

- Applications submitted over time
- Applications by company
- Applications by role
- Status distribution
- Average time between application stages
- Interview conversion rate
- Offer conversion rate

Analytics should be presented as factual summaries of the user's stored application data.

## Constraints

The Application Tracking Agent must:

- Never fabricate application status.
- Never mark an application as submitted without confirmation.
- Preserve application history.
- Clearly distinguish user-provided information from imported information.
- Protect sensitive application data.
- Avoid sending messages or follow-ups without explicit authorization.
- Handle deleted or expired job postings gracefully.

## Future Extensions

- Email integration
- Calendar integration
- Recruiter communication tracking
- Automatic status detection
- Interview preparation integration
- Offer comparison
- Application pipeline visualization
- Job-search performance analytics
- Multi-agent career workflow integration