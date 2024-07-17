# Entity Relationship Model

## Entities

- Hospital staff (employees)
- Patients
- User Type
- The waitlist (i.e. the queue)
- Severity Rank

### Entity Relationship Diagram

![Database Schema](/docs/schema.png)

Note that attributes have been listed within the boxes instead of as bubbles. This was to show which attributes are keys. Cardinality is displayed via arrows. Image created with [https://app.diagrams.net/](https://app.diagrams.net/).

### Attributes Details

#### Employee

- Employee ID (Integer, Primary Key)
- Type ID (Integer, Foreign Key [User Type])
- Employee Name (String)

#### Patient

- Patient ID (Integer, Primary Key)
- Type ID (Integer, Foreign Key [User Type])
- Patient Name (String)
  - First Name (String)
  - Last Name (String)

#### User Type

- Type ID (Integer, Primary Key)
- Type Name (String)

#### Severity

- Severity ID (Integer, Primary Key)
- Severity Rank (Integer {1,2,3,4,5})
- Severity Description (String)

#### Waitlist
- List ID (Integer, Primary Key)
- Patient ID (Integer, Foreign Key [Patient])
- Severity ID (Integer, Foreign Key [Severity])
- Admission Time (DateTime)
- Estimated Wait Time (Decimal)
- Access Code (String, length=3)

## Schema

### SQL Schema Excerpt

**Note:** see [the full schema export from Maria DB](/db/emergency_waitlist.sql) for a full description of all details including constraints, primary keys, foreign keys, engine information, php version, export time, server version, etc.

The below excerpt is just for demonstration purposes.

```sql
-- Table structure for table `employee`
CREATE TABLE `employee` (
  `employee_id` int(11) NOT NULL,
  `type_id` int(11) NOT NULL,
  `emp_name` text NOT NULL
)

-- Table structure for table `patient`
CREATE TABLE `patient` (
  `patient_id` int(11) NOT NULL,
  `type_id` int(11) NOT NULL,
  `patient_name` text NOT NULL
)

-- Table structure for table `severity`
CREATE TABLE `severity` (
  `severity_id` int(11) NOT NULL,
  `severity_rank` int(11) NOT NULL,
  `severity_description` text NOT NULL
)

-- Table structure for table `usertype`
CREATE TABLE `usertype` (
  `type_id` int(11) NOT NULL,
  `type_name` text NOT NULL
)

-- Table structure for table `waitlist`
CREATE TABLE `waitlist` (
  `list_id` int(11) NOT NULL,
  `patient_id` int(11) NOT NULL,
  `severity_id` int(11) NOT NULL,
  `admit_time` datetime NOT NULL DEFAULT current_timestamp(),
  `estimated_wait` time NOT NULL,
  `access_code` tinytext NOT NULL
)
```


Translate your ERD into a SQL Schema (for example `CREATE TABLE patients`).
This should be valid SQL (hint: it should run on your applications database, e.g. `emergency_waitlist`).

Commit these changes and push to [GitHub](https://github.com/).

#### Sample Data (SQL INSERT)

Create sample data that you can later use for testing.  For example,
`INSERT INTO patients (name, ...) VALUES ('james', ...)`.
This should be valid SQL.

Commit these changes and push to [GitHub](https://github.com/).
