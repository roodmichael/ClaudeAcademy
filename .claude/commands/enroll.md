Enroll a student in a course, creating it first if it doesn't exist.

Arguments: $ARGUMENTS — the topic the student wants to study (e.g. "homebrewing beer")

Steps:
1. Resolve the student:
   - Read academy/students/registry.json
   - If no students are registered: output "You need to register first. Use /register
     to get started." and stop.
   - If one student: use their student_id (UUID)
   - If multiple students: use the one whose progress files show the most recent activity

2. Read academy/catalog.json.
3. Check if any existing course matches the requested topic.
4. If a match exists:
   - Read academy/students/{student_id}/profile.json
   - Add the course code to enrolled_courses if not already present
   - Write the updated profile.json
   - Create academy/students/{student_id}/progress/{DEPT-###}.json if it doesn't exist:
     { "student_id": "{student_id}", "course_code": "{DEPT-###}", "enrolled_date": "{today}",
       "current_session": 1, "completed_sessions": [], "midterm_completed": false,
       "midterm_score": null, "final_project_submitted": false, "flagged_gaps": [],
       "status": "in_progress" }
   - Invoke the Personalizer agent (read agents/personalizer.md for the full spec)
     with student_id: {student_id}, course_code: "{DEPT-###}"
   - Confirm enrollment with course title, session count, and "Use /study to begin."
5. If no match exists:
   - Tell the student: "No course on that topic exists yet — building one now."
   - Invoke the Course Creator agent (read agents/course-creator.md for the full spec)
     with topic: $ARGUMENTS, student_level: "freshman"
   - After the Course Creator completes, enroll the student as in step 4
   - Confirm with: course code, title, session count, and "Use /study to begin."
