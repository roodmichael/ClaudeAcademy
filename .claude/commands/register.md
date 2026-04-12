Register a new student with The Claude Academy.

Arguments: none

Steps:
1. Read academy/students/registry.json (create it with { "students": [] } if it doesn't exist).
2. Invoke the Registrar agent (read agents/registrar.md for the full spec).
3. The Registrar conducts the intake conversation, assigns a UUID, creates the student
   directory and profile, and updates the registry.
4. Registration is complete when the Registrar confirms.
