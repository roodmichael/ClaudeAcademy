# The Claude Academy

A personal AI-powered college. Tell it what you want to learn — it builds the course and teaches it to you.

## What this is

This repository is a curriculum engine. You pick a topic — homebrewing, Kafka, political philosophy, coffee roasting, whatever — and Claude designs a structured course from scratch: sessions, exercises, quizzes, a midterm, and a final project. Then it teaches you through that curriculum, one session at a time.

The goal is structured learning over casual Q&A. Instead of getting a quick answer, you build real understanding through a course designed specifically for you.

## How to use it

| Command | What it does |
|---------|-------------|
| `/enroll <topic>` | Build a new course (if needed) and enroll you in it |
| `/study` | Begin or continue your current session |
| `/ask <question>` | Ask the tutor a question in the context of your course |
| `/catalog` | Browse all available courses |
| `/new-course <topic>` | Build a course without enrolling |

Start here: `/enroll <something you want to learn>`

## How courses are built

When you enroll in a topic that doesn't have a course yet, Claude:

1. Researches the subject using live web sources
2. Designs a session sequence sized to the material (4–12 sessions)
3. Writes every lesson, exercise set, and quiz from that research
4. Creates a midterm and a final project

Courses live in `courses/{DEPT}/{DEPT-###}/` and are yours to keep.

## What's here

```
agents/       Course Creator, Researcher, and Tutor agent specs
academy/      Catalog, departments, and student records
courses/      All built courses
```
