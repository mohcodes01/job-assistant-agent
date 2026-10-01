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