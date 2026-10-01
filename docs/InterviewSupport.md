# Interview Support Agent

## Overview

The Interview Support Agent helps users prepare for and manage job interviews by analyzing the target role, generating personalized preparation materials, conducting mock interviews, and providing structured feedback.

The agent should adapt interview preparation to the specific job, company, interview stage, and user's background.

## Responsibilities

- Analyze the target job description.
- Identify likely interview topics.
- Generate role-specific interview questions.
- Prepare technical and behavioral questions.
- Conduct interactive mock interviews.
- Evaluate user responses.
- Provide actionable feedback.
- Generate preparation plans.
- Track interview stages and preparation progress.
- Store interview notes and user feedback.

## Supported Interview Types

- Recruiter screening
- Behavioral interview
- Technical interview
- Coding interview
- System design interview
- AI / ML interview
- Project discussion
- Hiring manager interview
- Final interview

## Input

The agent may receive:

- Job description
- Company information
- Resume / CV
- Portfolio
- Relevant projects
- Interview stage
- Interview format
- User experience level
- Previous interview feedback
- Specific preparation goals

## Core Principle

The agent should provide preparation and feedback based on available information without inventing the user's experience, achievements, projects, or qualifications.

## Interview Analysis

The agent should analyze:

- Required technical skills
- Preferred technical skills
- Core responsibilities
- Seniority expectations
- Required experience
- Domain knowledge
- Behavioral competencies
- Likely interview topics
- Potential knowledge gaps

## Question Generation

Questions should be generated according to the target role and interview stage.

Question categories may include:

- Technical knowledge
- Coding
- Architecture
- System design
- Debugging
- AI / ML concepts
- Project experience
- Behavioral scenarios
- Leadership
- Collaboration
- Problem solving
- Role-specific situations

Questions should vary in difficulty and should avoid unnecessary repetition.

## Mock Interview Workflow

```text
Job Description
      │
      ▼
Interview Analysis
      │
      ▼
Question Generation
      │
      ▼
Mock Interview
      │
      ▼
User Response
      │
      ▼
Response Analysis
      │
      ▼
Feedback
      │
      ▼
Next Question
      │
      ▼
Interview Summary



### Part 3 — Evaluation, Tracking & Extensions

```md
## Interview Evaluation

After a mock interview, the agent should generate a structured summary containing:

- Questions asked
- User responses
- Key strengths
- Areas for improvement
- Topics requiring additional preparation
- Suggested practice questions
- Recommended preparation topics

The evaluation should be based only on the interview session and available user information.

## Interview Tracking

The agent may track:

- Interview date
- Interview stage
- Interview format
- Interviewer information
- Preparation status
- Topics practiced
- User notes
- Interview feedback
- Follow-up actions

## Preparation Plan

The agent should be able to create a preparation plan based on:

- Available preparation time
- Interview stage
- Job requirements
- User's existing knowledge
- Identified preparation gaps

Example:

```text
Day 1 → Job & Company Analysis
Day 2 → Technical Fundamentals
Day 3 → Role-Specific Questions
Day 4 → System Design / Coding
Day 5 → Behavioral Practice
Day 6 → Mock Interview
Day 7 → Final Review