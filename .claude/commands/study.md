Begin or continue a study session for an enrolled course.

Arguments: $ARGUMENTS — optional course code (e.g. "BREW-100"). If omitted, use the
most recently active course from the student's progress files.

Steps:
1. Resolve the student:
   - Read academy/students/registry.json
   - If no students are registered: output "You need to register first. Use /register
     to get started." and stop.
   - If one student: use their student_id (UUID)
   - If multiple students: use the one whose progress files show the most recent activity

2. If no course code provided:
   - Read all files matching academy/students/{student_id}/progress/*.json
   - Find the course with status "in_progress" and the most recent activity
   - Use that course code

3. Read academy/students/{student_id}/progress/{course_code}.json
4. Get the current_session number from the progress file
5. Invoke the Tutor agent (read agents/tutor.md for the full spec) in session mode:
   - student_id: {student_id}
   - course_code: from step 2 or $ARGUMENTS
   - mode: "session"
   - session_number: current_session from the progress file
6. The Tutor handles all delivery, quiz administration, and progress updates.
