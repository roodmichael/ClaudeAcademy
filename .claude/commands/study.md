Begin or continue a study session for an enrolled course.

Arguments: $ARGUMENTS — optional course code (e.g. "BREW-100"). If omitted, use the
most recently active course from the student's progress files.

Steps:
1. If no course code provided:
   - Read all files matching academy/students/default/progress/*.json
   - Find the course with status "in_progress" and the most recent activity
   - Use that course code
2. Read academy/students/default/progress/{course_code}.json
3. Get the current_session number from the progress file
4. Invoke the Tutor agent (read agents/tutor.md for the full spec) in session mode:
   - student_id: "default"
   - course_code: from step 1 or $ARGUMENTS
   - mode: "session"
   - session_number: current_session from the progress file
5. The Tutor handles all delivery, quiz administration, and progress updates.
