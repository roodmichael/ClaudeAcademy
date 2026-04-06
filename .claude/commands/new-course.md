Directly invoke the Course Creator to build a new course.

Arguments: $ARGUMENTS — topic and optional flags:
  --level=101        force a specific course level (default: auto-determined)
  --depth=deep       survey | standard | deep (default: standard)
  --dept=BREW        force a specific department code (default: auto-determined)

Examples:
  /new-course homebrewing beer
  /new-course Apache Kafka --level=101 --depth=deep
  /new-course home coffee roasting --dept=COFF

Steps:
1. Parse topic and flags from $ARGUMENTS.
2. Read academy/catalog.json and academy/departments.json to provide context.
3. Invoke the Course Creator agent (read agents/course-creator.md for the full spec) with:
   - topic: parsed topic text
   - student_level: "freshman"
   - requested_depth: from --depth flag or "standard"
   - Any department or level overrides from flags
4. When the Course Creator completes, report back:
   - Course code and title
   - Number of sessions created
   - Location on disk
   - "Use /enroll {topic} to register for this course."
