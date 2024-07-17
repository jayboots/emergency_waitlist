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
- Patient Code (String, length=3)

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