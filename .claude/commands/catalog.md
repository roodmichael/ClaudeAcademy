Browse available courses at The Claude Academy.

Arguments: $ARGUMENTS — optional filter: department code, level number, or keyword

Steps:
1. Read academy/catalog.json
2. Read academy/departments.json
3. Resolve the student:
   - Read academy/students/registry.json
   - If no students registered: skip student-specific steps (steps 4 and 7)
   - If one student: use their student_id (UUID)
   - If multiple students: use the one whose progress files show the most recent activity
4. Read academy/students/{student_id}/profile.json to get enrolled_courses and completed_courses
5. Read all files matching academy/students/{student_id}/progress/*.json to get current progress

6. If no filter provided, display all courses grouped by department division:

   Format:
   ## {Division Name}
   ### {Department Name} ({DEPT})
   - {DEPT-###} — {Title} ({n} sessions) [ENROLLED: Session {x}/{total} | COMPLETED | or blank]

7. If a filter is provided:
   - Department code (e.g. "BREW"): show only that department
   - Level (e.g. "100"): show all 100-level courses across departments
   - Keyword (e.g. "fermentation"): show courses whose title or description contains the keyword

8. At the bottom, always show the student's enrolled courses with a progress summary
   (skip if no student is registered):
   ## Your Courses
   - {DEPT-###} {Title} — Session {current}/{total} | Quiz avg: {average score}%

9. If the catalog is empty, say: "No courses have been created yet. Use /enroll to build
   your first course."
