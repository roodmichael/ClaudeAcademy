Ask the tutor a question about course material.

Arguments: $ARGUMENTS — the question, optionally prefixed with a course code
(e.g. "BREW-100 why does yeast die at high temperatures?" or just
"why does yeast die at high temperatures?")

Steps:
1. Parse $ARGUMENTS. If it starts with a course code pattern (4 letters, dash, 3 digits),
   extract it. Otherwise, determine the active course by reading
   academy/students/default/progress/*.json and finding the most recent in_progress course.
2. Invoke the Tutor agent (read agents/tutor.md for the full spec) in office hours mode:
   - student_id: "default"
   - course_code: determined above
   - mode: "office_hours"
   - question: the question text from $ARGUMENTS
3. The Tutor searches course materials scoped to completed sessions and answers in context.
