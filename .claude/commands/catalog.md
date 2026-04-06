Browse available courses at The Claude Academy.

Arguments: $ARGUMENTS — optional filter: department code, level number, or keyword

Steps:
1. Read academy/catalog.json
2. Read academy/departments.json
3. Read academy/students/default/profile.json to get enrolled_courses and completed_courses
4. Read all files matching academy/students/default/progress/*.json to get current progress

5. If no filter provided, display all courses grouped by department division:

   Format:
   ## {Division Name}
   ### {Department Name} ({DEPT})
   - {DEPT-###} — {Title} ({n} sessions) [ENROLLED: Session {x}/{total} | COMPLETED | or blank]

6. If a filter is provided:
   - Department code (e.g. "BREW"): show only that department
   - Level (e.g. "100"): show all 100-level courses across departments
   - Keyword (e.g. "fermentation"): show courses whose title or description contains the keyword

7. At the bottom, always show the student's enrolled courses with a progress summary:
   ## Your Courses
   - {DEPT-###} {Title} — Session {current}/{total} | Quiz avg: {average score}%

8. If the catalog is empty, say: "No courses have been created yet. Use /enroll to build
   your first course."
