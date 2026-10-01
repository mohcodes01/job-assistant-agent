# Job Search Agent

## Overview

The Job Search Agent is responsible for discovering, filtering, analyzing, and organizing relevant job opportunities based on a user's profile, skills, experience, preferences, and career goals.

It transforms a broad job search into a structured pipeline that helps users identify relevant opportunities while reducing irrelevant listings and repetitive manual searching.

## Responsibilities

- Search for relevant job opportunities across supported sources.
- Match job requirements against the user's profile.
- Filter jobs based on:
  - Job title
  - Required skills
  - Experience level
  - Location
  - Remote / hybrid / onsite preference
  - Employment type
  - Salary range
  - Technology stack
  - Industry
- Extract structured information from job postings.
- Detect duplicate or highly similar job listings.
- Rank and prioritize jobs based on user-defined criteria.
- Track previously discovered jobs.
- Identify important application requirements and deadlines.
- Provide concise explanations for why a job matches the user's profile.

## Input

The agent should accept a structured job-search profile:

    interface JobSearchProfile {
      targetRoles: string[];
      skills: string[];
      experienceLevel?: string;
      locations?: string[];
      remoteOnly?: boolean;
      employmentTypes?: string[];
      salaryRange?: {
        min?: number;
        max?: number;
        currency?: string;
      };
      industries?: string[];
      excludedCompanies?: string[];
      keywords?: string[];
    }

## Output

Each discovered job should be normalized into a consistent structure:

    interface JobOpportunity {
      title: string;
      company: string;
      location?: string;
      remote?: boolean;
      employmentType?: string;
      salary?: string;
      description?: string;
      requirements?: string[];
      technologies?: string[];
      url: string;
      source: string;
      matchScore?: number;
      matchReasons?: string[];
      discoveredAt: string;
    }

## Job Matching

The agent should evaluate opportunities using multiple signals rather than relying only on keyword matching.

### Matching Signals

- Role/title similarity
- Technical skill overlap
- Experience compatibility
- Location compatibility
- Remote-work compatibility
- Employment-type compatibility
- Salary compatibility
- Industry relevance
- User-defined keywords
- Explicit exclusions

The matching system should distinguish between:

- Required qualifications
- Preferred qualifications
- Nice-to-have skills
- Potential mismatches

## Search Pipeline

    User Profile
         │
         ▼
    Search Configuration
         │
         ▼
    Job Discovery
         │
         ▼
    Job Extraction
         │
         ▼
    Normalization
         │
         ▼
    Deduplication
         │
         ▼
    Profile Matching
         │
         ▼
    Filtering
         │
         ▼
    Ranking
         │
         ▼
    Job Results

## Deduplication

The agent should avoid returning the same opportunity multiple times when it appears across different sources.

Potential deduplication signals include:

- Company
- Job title
- Location
- Canonical job URL
- External job ID
- Description similarity

## Ranking

Jobs may be ordered according to the user's configured preferences.

Example factors:

    Role Match
    + Skill Match
    + Experience Match
    + Location Match
    + Remote Match
    + Salary Match
    + Preference Match

The system should preserve the underlying matching signals so users can understand why a job was surfaced.

## Agent Constraints

The Job Search Agent should:

- Never fabricate job information.
- Preserve the original job URL whenever available.
- Clearly identify the source of each listing.
- Avoid treating missing information as a negative match.
- Distinguish explicit requirements from inferred requirements.
- Avoid applying for jobs automatically unless explicitly authorized by the user.
- Respect source-specific access and usage restrictions.
- Keep user profile data separate from publicly sourced job data.

## Error Handling

The agent should gracefully handle:

- Unreachable job sources
- Invalid job URLs
- Incomplete job descriptions
- Missing salary information
- Missing location information
- Duplicate listings
- Parsing failures
- Temporary source failures
- Unsupported job sources

A failed source should not prevent the agent from processing successfully retrieved opportunities.

## Future Extensions

- Personalized job alerts
- Job-change tracking
- Application deadline tracking
- Resume-to-job matching
- Cover-letter generation
- Application status tracking
- Interview preparation
- Company research
- Skill-gap analysis
- Multi-agent job-search workflows