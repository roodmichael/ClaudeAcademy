Enroll the student in a course, creating it first if it doesn't exist.

Arguments: $ARGUMENTS — the topic the student wants to study (e.g. "homebrewing beer")

Steps:
1. Read academy/catalog.json.
2. Check if any existing course matches the requested topic.
3. If a match exists:
   - Read academy/students/default/profile.json
   - Add the course code to enrolled_courses if not already present
   - Write the updated profile.json
   - Create academy/students/default/progress/{DEPT-###}.json if it doesn't exist:
     { "student_id": "default", "course_code": "{DEPT-###}", "enrolled_date": "{today}",
       "current_session": 1, "completed_sessions": [], "midterm_completed": false,
       "midterm_score": null, "final_project_submitted": false, "flagged_gaps": [],
       "status": "in_progress" }
   - Confirm enrollment with course title, session count, and "Use /study to begin."
4. If no match exists:
   - Tell the student: "No course on that topic exists yet — building one now."
   - Invoke the Course Creator agent (read agents/course-creator.md for the full spec)
     with topic: $ARGUMENTS, student_level: "freshman"
   - After the Course Creator completes, enroll the student as in step 3
   - Confirm with: course code, title, session count, and "Use /study to begin."
