# Student Information System SQL Practical Exercises

This repository contains hands-on MySQL exercises for creating and managing a
small student information system. The exercises progress from database
permissions and roles to views, stored procedures, and user-defined functions.

## Why use this project?

- Practice SQL against a realistic student-and-teacher data model.
- Learn how to create users, grant and revoke table privileges, and activate
  roles.
- Build reusable database objects, including views, stored procedures, and
  deterministic functions.
- Compare executable SQL with written notes describing the results and common
  MySQL/DBeaver behavior.

This is an educational project rather than a production-ready student
information system. Run the scripts only against a disposable local database.

## Project contents

| Path | Purpose |
| --- | --- |
| [`exercises.md`](exercises.md) | Notes and SQL examples for permissions, users, roles, and privileges |
| [`manipulating.md`](manipulating.md) | Notes for the view, procedure, and function exercises |
| [`ky7PVSRaRmO9yx7OCvig_Module_8/Module_8.sql`](ky7PVSRaRmO9yx7OCvig_Module_8/Module_8.sql) | Executable Module 8 SQL for views, procedures, and functions |
| [`0wis3MXqSkahlkTkcRXe_Module_9/Module_9.sql`](0wis3MXqSkahlkTkcRXe_Module_9/Module_9.sql) | Module 9 SQL solution |
| `student_management/` | Local MySQL data files included as supporting artifacts |

## Prerequisites

- MySQL with support for roles, stored procedures, and user-defined functions
  (MySQL 8.x is recommended).
- A MySQL client such as the `mysql` command-line client or DBeaver.
- An account permitted to create databases, tables, users, roles, views,
  procedures, and functions.

## Get started

1. Clone the repository and open a MySQL client.
2. Create or select a disposable database named `student_management`.
3. Create the `Students` and `Teachers` tables using the schema examples in
   [`exercises.md`](exercises.md).
4. Run the SQL for the permissions exercise as an administrative account.
5. Execute the Module 8 script:

   ```bash
   mysql -u root -p student_management \
     < ky7PVSRaRmO9yx7OCvig_Module_8/Module_8.sql
   ```

   The script uses `DELIMITER $$` for compound statements. If you use DBeaver,
   run the statements in the SQL editor according to its script-execution
   behavior.
6. Inspect the results and explanations in [`manipulating.md`](manipulating.md).

The SQL expects a `students` table with `id`, `name`, `age`, and `grade`
columns. The stored procedure uses `LAST_INSERT_ID()`, so `id` should be an
`AUTO_INCREMENT` column when adding students.

## Example queries

After running the Module 8 script, try:

```sql
USE student_management;

SELECT * FROM student_overview;

SET @new_student_id = 0;
CALL add_student('Jane Smith', 20, 'B', @new_student_id);
SELECT @new_student_id AS new_student_id;

SELECT calculate_discount(100, 15) AS discounted_price;
```

The permissions exercises also demonstrate checking access by attempting
allowed and denied operations as `teacher_user`, `admin_user`, and
`student_user`. Use separate client connections for each account and never
reuse real credentials in the examples.

## Support

Start with the notes in [`exercises.md`](exercises.md) and
[`manipulating.md`](manipulating.md). If something is unclear or reproducible
with a clean local MySQL setup, [open an issue](https://github.com/VoidLance/course-files-sql-practical-exercises-student-information-system/issues)
with your MySQL version, the relevant script, and the complete error message.

## Maintainer and contributions

This project is maintained by
[VoidLance](https://github.com/VoidLance). Contributions are welcome through
issues and pull requests. Keep changes focused on the learning objectives,
include reproducible SQL where appropriate, and update the relevant notes when
an exercise or expected result changes.

## License

See the repository's [`LICENSE`](LICENSE) file for licensing information.
