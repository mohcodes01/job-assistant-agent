# Application Support Agent

## Overview

The Application Support Agent assists users throughout the job application process after a relevant opportunity has been identified.

It analyzes job postings, prepares application materials, validates application requirements, and helps users complete applications accurately while keeping the process under explicit user control.

## Responsibilities

- Analyze job-specific application requirements.
- Compare the job description against the user's profile and resume.
- Identify missing or potentially weak application information.
- Prepare application-specific responses.
- Generate tailored application content when requested.
- Extract application questions from job forms.
- Suggest answers based on verified user information.
- Validate application completeness before submission.
- Track application-related metadata.
- Provide clear explanations for generated or suggested content.

## Core Principle

The agent should assist with applications without fabricating user information or submitting applications without explicit user authorization.

## Input

The agent may receive:

- Job posting
- Company information
- User profile
- Resume / CV
- Portfolio information
- Relevant project history
- Job-specific application questions
- User preferences
- Existing application data

### Application Context

```ts
interface ApplicationContext {
  jobId?: string;
  jobTitle: string;
  company: string;
  jobUrl?: string;
  jobDescription?: string;
  resume?: string;
  profile?: UserProfile;
  questions?: ApplicationQuestion[];
  existingAnswers?: ApplicationAnswer[];
}