# Job Search Agent

## Overview

The Job Search Agent discovers and analyzes job opportunities that align with a user's career profile, technical skills, experience, location preferences, and employment goals.

Its primary purpose is to automate repetitive job discovery and provide structured, relevant opportunities that can be consumed by the rest of the Job Search Agent workflow.

## Responsibilities

- Discover jobs from configured job platforms and sources.
- Parse and normalize job posting information.
- Compare job requirements with the user's profile.
- Filter opportunities using explicit user preferences.
- Identify required and preferred qualifications.
- Detect duplicate job postings across different sources.
- Calculate a transparent relevance score.
- Explain the main reasons behind each match.
- Track previously processed opportunities.
- Return structured job results to downstream agents.

## Input

The agent receives a job-search configuration:

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

Each job should be converted into a normalized opportunity:

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

## Matching Strategy

The agent should use multiple matching signals instead of relying exclusively on keyword overlap.

### Matching Signals

- Job title relevance
- Required skill coverage
- Preferred skill coverage
- Experience-level compatibility
- Location compatibility
- Remote-work compatibility
- Employment-type compatibility
- Salary compatibility
- Industry relevance
- User-defined keywords
- Company exclusions

Missing information should be treated as unknown rather than automatically considered a mismatch.

## Processing Flow

    User Profile
         │
         ▼
    Search Configuration
         │
         ▼
    Source Discovery
         │
         ▼
    Job Extraction
         │
         ▼
    Data Normalization
         │
         ▼
    Duplicate Detection
         │
         ▼
    Profile Matching
         │
         ▼
    Filtering
         │
         ▼
    Relevance Scoring
         │
         ▼
    Structured Results

## Deduplication

Duplicate detection should combine multiple identifiers where available:

- 