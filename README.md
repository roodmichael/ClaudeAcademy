# The Claude Academy

A personal AI-powered college. Pick anything you want to learn — it builds the course, personalizes it to you, and teaches it one session at a time.

## What this is

This repository is a curriculum engine. You register as a student, then enroll in topics — homebrewing, Kafka, political philosophy, coffee roasting, whatever — and Claude designs a complete course from scratch: sessions, exercises, quizzes, a midterm, and a final project. Then it teaches you through that curriculum interactively.

The goal is structured learning over casual Q&A. Instead of getting a quick answer, you build real understanding through a course designed for everyone but taught specifically for you.

## Getting started

```
/register       Create your student profile (do this first)
/enroll <topic> Build a course and enroll in it
/study          Begin or continue your current session
```

## Commands

| Command | What it does |
|---------|-------------|
| `/register` | Create your student profile with a brief intake |
| `/enroll <topic>` | Build a new course (if needed) and enroll in it |
| `/study` | Begin or continue your current session |
| `/ask <question>` | Ask the tutor a question scoped to your course |
| `/catalog` | Browse all available courses and your progress |
| `/new-course <topic>` | Build a course without enrolling |

## How it works

### Registration
When you register, the Registrar conducts a short intake — your name, background domains, and interests. This seeds your student profile, which every agent reads to personalize your experience.

### Course creation
When you enroll in a topic that doesn't have a course yet, Claude:

1. Researches the subject using live web sources
2. Designs a session sequence sized to the material (4–12 sessions)
3. Writes every lesson, exercise set, and quiz from that research
4. Creates a midterm and a final project

Courses are generic curriculum — the same material for any student.

### Personalization
After enrollment, the Personalizer reads your profile and rewrites the exercise sets with scenarios drawn from your background. A philosopher with a homebrewing background gets different examples than a software engineer — same concepts, same rigor, different framing.

As you progress through sessions, the Tutor and Lab Instructor update your profile with newly discovered bridges and domain knowledge. Each new course you take benefits from everything learned in prior ones.

### Lab courses
Some subjects have a lab companion (e.g. COFF-100L alongside COFF-100). Lab courses are hands-on: you perform procedures, record observations, and build a running log. A Lab Instructor guides each session and connects your physical results back to lecture concepts.

## Available courses

See [academy/catalog.json](academy/catalog.json) for the full list.

| Code | Title | Type |
|------|-------|------|
| COFF-100 | Home Coffee Roasting — Foundations | Lecture |
| COFF-100L | Home Coffee Roasting — Lab | Lab |
| PHIL-100 | Classical Philosophy — Foundations | Lecture |

## Repository structure

```
agents/                   Agent specs — Course Creator, Registrar, Personalizer,
                          Researcher, Tutor, Lab Instructor
academy/
  catalog.json            All available courses
  departments.json        Department registry
  students/
    profile-template.json Empty schema for new student profiles
    default/              Empty template directory
courses/
  {DEPT}/{DEPT-###}/      Lecture course — lessons, exercises, quizzes, assessments
  {DEPT}/{DEPT-###L}/     Lab course — procedures, briefs, debriefs
.claude/commands/         Slash command entry points
```

Student data (profiles, progress, personalized exercises) is excluded from this repository and lives only on your local machine.
